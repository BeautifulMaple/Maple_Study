# 프리팹 ( Prefab )이란?

**프리팹**은 게임에 존재하는 게임 오브젝트를 Project View에 파일로 저장해 둔 것을 말한다.

![Untitled](https://github.com/user-attachments/assets/23ac64fe-7838-46f7-bbc0-88b1633032a3)


- Hierarchy View의 게임 오브젝트를 Project View로 드래그 & 드롭한다.
- Hierarchy View에 있는 게임 오브젝트를 삭제한다.

## Instantiate(GameObject originaI);

- original 게임 오브젝트(프리팹)를 복제해서 생성한다.
- (복제되는 오브젝트의 모든 컴포넌틑 정보가 원본과 완전히 동일하다)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        Instantiate(boxPrefab);
        Instantiate(boxPrefab);

    }
}

```

## Instantiate(GameObject originaI, Vector3 position, Quaternion rotation)

기본 형태

- Instantiate(original, position, rotation)
    
    original :  복제할 원본을 지정
    
    postion : 새 객체를 생성할 위치
    
    rotation : 새 객체의 회전 값
    
    Quaternion.identity 회전하지 않은 상태로 생
    

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        Instantiate(boxPrefab, new Vector3(3, 3, 0), Quaternion.identity);
        Instantiate(boxPrefab, new Vector3(-1, -2, 0), Quaternion.identity);

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/5ff79d35-7fc0-4f85-9601-3cba92c071ad/Untitled.png)

# 회전 정보를 나타나내고 연산하는 방식

## 오일러 (Euder)

- 3차원의 3개의 각도를 표현하기 위해 사용하는 3x3ㅇ 크기의 행렬
- 회전 순서에 따라 결과를 달라지기 때문에 회전 순서에 주의해야 함
    - 유니티에서는 따로 계산할 일이 없기 때문에 걱정할 필요가 없다

### 장점

- 0~360의 각도를 표현할 수 있다.

### 단점

- 지속적으로 회전을 하는 연상을 할 때 퀴터니온보다 **연산속도가 느리고, 짐벌럭 현상**이 발생할 수 있다.

## 짐벌락이란

- 세 개의 축이 서로 종속적인 관계를 가지고 있기 때문에 발생하는 문제로 회전 연산 도중 축이 하나 사라져 3차원의 오브젝트가 일그러지는 현상

## 쿼터니온 (Quateniaon)

- 사원수로 3개의 벡터 요소와 하나의 스칼라 요소로 구성 (4개의 -1 ~ 1 사이의 값)

### 장점

- 연산속도가 빠르고, 짐벌락 현상이 발생하지 않는다.

### 단점

- 우리가 알고 있는 0~360의 각도가 아니기 때문에 특정 각도를 표현하기 힘들다.

## 유니티(Unity)

- transfrom.rotation : 게임오브젝트의 쿼터니온 회전 정보
- transfrom.localScale : 게임오브젝트의 오일러 회전 정보

Inspector View에 보이는 Transform의 rotation은 개발자의 편의를 위해 오일러로 표현한다.

**Quateniaon q = Quateniaon.Euler(0, 0, 0);**

- 오일러 회전 정보를 입력해서 쿼터니온 회전 값으로 변경한다.

**trnasform.rotate(new Vector(1, 0, 0);**

- x축으로 “빙글빙글 돌아라”와 같이 지속적인 회전 함수

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        Quaternion rotation = Quaternion.Euler(0f, 0f, 45f);
        Instantiate(boxPrefab, new Vector3(2, 1, 0), rotation);

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/71c3f0eb-338b-4331-b5cf-dab08a34c886/Untitled.png)

- z축으로 45도를 회전한 오브젝트를 생성합니다.

## GameObject clon = Instantiate(GameObject originaI, Vector3 position, Quaternion rotation);

- original 게임오브젝트(프리맵)를 복제해서 생성하고, 생성된 복젝 오브젝트의 정보를 clon에 저장한다
- clone의 정보가 바뀌면 Hierarchy Vice에 생성된 오브젝트의 정보가 바뀐다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        
        Quaternion rotation = Quaternion.Euler(0f, 0f, 45f);
        // Instantiate(boxPrefab, new Vector3(2, 1, 0), rotation);

        GameObject clon = Instantiate(boxPrefab, Vector3.zero, rotation);

        // 방금 생성된 게임 오브젝트의 이름 변경
        clon.name = "Box001";
        // 방금 생성된 게임 오브젝트의 색상 변경
        clon.GetComponent<SpriteRenderer>().color = Color.black;
        // 방금 생성된 게임 오브젝트의 위치 변경
        clon.transform.position = new Vector3(3, 1, 0);
        //크기 변경
        clon.transform.localScale = new Vector3(3, 3, 1);
    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/382faa76-68f1-4a98-8225-dd586d449e83/Untitled.png)

- Box001로 변경
- 색상 : 검정색
- 크기는 3, 3, 1 사이즈로 변경

## 반복문

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        for (int i = 0; i < 10; i++)
        {
            Vector3     position = new Vector3(-4.5f + i, 0, 0);
            Quaternion  rotation = Quaternion.Euler(0, 0, i * 10);
            Instantiate(boxPrefab, position, rotation);
        }

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/1b4ae6fa-3d3b-44ed-a747-93bcc71de1b8/Untitled.png)

## 2중 반복문

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        // 외부 반복문 (격자의 y축 계산용으로 활용됨)
        for (int y = 0; y < 10; ++y)
        {
            // 내부 반복문 (격자의 x축 계산용으로 활용됨)
            for (int x = 0; x < 10; ++x)
            {
                Vector3 position = new Vector3(-4.5f + x, 4.5f - y, 0);
                Instantiate(boxPrefab, position, Quaternion.identity);

            }
        }

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/6cfb0e7b-7bba-41d6-8715-17157fc580f6/Untitled.png)

## 반복문 + 조건문

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        // 외부 반복문 (격자의 y축 계산용으로 활용됨)
        for (int y = 0; y < 10; ++y)
        {
            // 내부 반복문 (격자의 x축 계산용으로 활용됨)
            for (int x = 0; x < 10; ++x)
            {
		            // x와 y이가 같을 경우 생성하지 않기
                if ( x == y)
                {
                    continue;
                }
                Vector3 position = new Vector3(-4.5f + x, 4.5f - y, 0);
                Instantiate(boxPrefab, position, Quaternion.identity);

            }
        }

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/76241be8-70ba-44a2-9e92-b9d8369f6e5c/Untitled.png)

### X자로 만들기

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        // 외부 반복문 (격자의 y축 계산용으로 활용됨)
        for (int y = 0; y < 10; ++y)
        {
            // 내부 반복문 (격자의 x축 계산용으로 활용됨)
            for (int x = 0; x < 10; ++x)
            {
                if ( x == y || x+y == 9)
                {
                    continue;
                }
                Vector3 position = new Vector3(-4.5f + x, 4.5f - y, 0);
                Instantiate(boxPrefab, position, Quaternion.identity);

            }
        }

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/e7ed9270-c4cb-42b9-9746-07bbd3454074/Untitled.png)

### 마름모 모양으로 만들기

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject boxPrefab;
    // Start is called before the first frame update
    private void Awake()
    {
        // 외부 반복문 (격자의 y축 계산용으로 활용됨)
        for (int y = 0; y < 10; ++y)
        {
            // 내부 반복문 (격자의 x축 계산용으로 활용됨)
            for (int x = 0; x < 10; ++x)
            {
                if ( x + y == 4 || x - y == 5 || y - x == 5 || x + y == 14)
                {
                    continue;
                }
                Vector3 position = new Vector3(-4.5f + x, 4.5f - y, 0);
                Instantiate(boxPrefab, position, Quaternion.identity);

            }
        }

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/dce546ea-8529-4705-8c08-bbfef5de42b5/Untitled.png)

## 임의의 프리팹으로 오브젝트 생성하기

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private GameObject[] PrefabArray;
    // Start is called before the first frame update
    private void Awake()
    {
        for(int i = 0; i < 10; ++i)
        {
            // int value = Random.Range(int min, int max);
            // min부터 max-1까지 정수 중에서 임의의 숫자를 value에 저장
            int index = Random.Range(0, PrefabArray.Length);
            Vector3 positio = new Vector3 (-4.5f + i, 0, 0);

            Instantiate(PrefabArray[index], positio, Quaternion.identity);
        }

    }
}

```

- int value = Random.Range(int min, int max);
min부터 max-1까지 정수 중에서 임의의 숫자를 value에 저장
- float value = Random.Range(float min, float max);
min부터 max-1까지 실수 중에서 임의의 숫자를 value에 저장

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/b5a8f8ef-62c5-4027-9ca9-391bce9271a7/Untitled.png)

### 임의의 위치에서 오브젝트 생성

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private int objectSpawnConut = 30;
    [SerializeField]
    private GameObject[] PrefabArray;
    // Start is called before the first frame update
    private void Awake()
    {
        for(int i = 0; i < 10; ++i)
        {
            // int value = Random.Range(int min, int max);
            // min부터 max-1까지 정수 중에서 임의의 숫자를 value에 저장
            int index = Random.Range(0, PrefabArray.Length);
            float x = Random.Range(-7.5f, 7.5f); // x축
            float y = Random.Range(-4.5f, 4.5f); // y축
            Vector3 positio = new Vector3 (x, y, 0);

            Instantiate(PrefabArray[index], positio, Quaternion.identity);
        }

    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/4c0f9af9-b8e2-4c33-8ba2-7b74b7eb9be6/Untitled.png)

### 플레이이어 위치에서 오브젝트 생성하기

```csharp

// PlayerController Script
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    [SerializeField]
    private KeyCode KeyCodeFire = KeyCode.Space;
    [SerializeField]
    private GameObject bulletPrefab;
    private float moveSpeed = 3.0f;
    private Vector3 lastMoveDirection = Vector3.right;

    // Update is called once per frame
    void Update()
    {
        // Player 오브젝트 이동
        float x = Input.GetAxisRaw("Horizontal");
        float y = Input.GetAxisRaw("Vertical");

        transform.position += new Vector3(x, y, 0) * moveSpeed * Time.deltaTime;

        // 마지막에 입력된 방향키의 방향을 총알의 발사 방향으로 활용
        if (x != 0 || y != 0)
        {
            lastMoveDirection = new Vector3(x, y, 0);
        }

        // Player object 총알 발사
        if (Input.GetKey(KeyCodeFire))
        {
            GameObject clone = Instantiate(bulletPrefab, transform.position, Quaternion.identity);

            clone.name = "Bullet";
            clone.transform.localScale = Vector3.one * 0.5f;
            clone.GetComponent<SpriteRenderer>().color = Color.red;

            clone.GetComponent<Movement2D>().Setup(lastMoveDirection); //방향값 전달
        }
    }
}

```

```csharp
// ObjectSpawner Script
using UnityEngine;

public class ObjectSpawner : MonoBehaviour
{
    [SerializeField]
    private int objectSpawnCount = 30; 
    [SerializeField]
    private GameObject[] PrefabArray;
    [SerializeField]
    private Transform[] spawnPointArray;
    private int currentObjectCount = 0; // 현재까지 생성한 오브젝트 개수
    private float objectSpawnTime = 0.0f;

    private void Update()
    {
        // objectSpawnCount 개수만큼만 생성하고 더 이상 생성하지 않도록 하기 위해 설정
        if (currentObjectCount >= objectSpawnCount)
        {
            return;
        }

        // 원하는 시간마다 오브젝트를 생성하기 위한 시간 변수 연산
        objectSpawnTime += Time.deltaTime;

        // 0.5초에 한번씩 실행
        if (objectSpawnTime >= 0.5f)
        {
            int prefabIndex = Random.Range(0, PrefabArray.Length);
            int spawnIndex = Random.Range(0, spawnPointArray.Length);

            Vector3 position = spawnPointArray[spawnIndex].position;
            GameObject clone = Instantiate(PrefabArray[prefabIndex], position, Quaternion.identity);

            // spawnIndex가 0인 오브젝트가 왼쪽에 있기 때문에 오른쪽으로 이동
            // spawnIndex가 1인 오브젝트가 오른쪽에 있기 때문에 왼쪽으로 이동
            Vector3 moveDirection = (spawnIndex == 0 ? Vector3.left : Vector3.right);
            clone.GetComponent<Movement2D>().Setup(moveDirection);

            currentObjectCount++;   // 현재 생성된 오브젝트의 개수를 1 증가시킨다.
            objectSpawnTime = 0.0f; // 시간을 0으로 초기화 해야 다시 0.5초를 계산할 수 있다.
        }
    }
}

```

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b31fc591-a9dc-4af5-b3b4-68153414245b/bd385dcf-c019-47fd-901c-35e47da56f33/Untitled.png)
