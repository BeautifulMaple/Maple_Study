# 초기화를 위한 이벤트 함수

## Awake() 함수

- 현재 씬에서 게임오브젝트가 활성화 되어 있을 때 1회 호출
(컴포넌트가 비활성화 상태여도 게임오브젝트가 활성화되어 있으면 호출된다.)
- 데이터를 초기화하는 용도로 사용

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void Awake()
    {
        Debug.Log("Awake 함수가 실행되었습니다.");
        Debug.Log("Awake 함수가 실행되었습니다.");
    }
}

```

## Start()함수

- 현재 씬에서 게임오브젝트와 컴포넌트가 모두 활성화되어 있을 때 1회 호출
- 데이터를 초기화하는 용도로 사용
- 첫 번째 업데이트 함수가 실행되기 직전에 호출
- 초기화 함수 호출 순선 Awake() → OnEnable() → Start()

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void Awake()
    {
        Debug.Log("Awake 함수가 실행되었습니다.");
        Debug.Log("Awake 함수가 실행되었습니다.");

    }
    private void Start()
    {
        Debug.Log("Start 함수가 실행되었습니다.");

    }
}

```

## OnEnable()함수

- 컴포넌트가 비활성화 되었다가 활성화 될 때마다 1회 호출

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void Awake()
    {
        Debug.Log("Awake 함수가 실행되었습니다.");
        Debug.Log("Awake 함수가 실행되었습니다.");

    }
    private void Start()
    {
        Debug.Log("Start 함수가 실행되었습니다.");

    }

    private void OnEnable()
    {
        Debug.Log("OnEnable함수가 실행되었습니다.");
    }

}

```

# Update()함수

## Update()함수

- 현재 씬이 실행된 후 컴포넌트가 활성화되어 있을 때 매 프레임마다 호출
(FPS 60이라 하면 Update() 함수가 1초에 60번 호출된다는 뜻이다.)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{  
    private void Update()
    {
        Debug.Log("Update함수가 실행되었습니다.");
    }
}

```

## LateUpdate()함수

- 현재 씬에 존재하는 모든 게임오브젝트의 Update() 함수가 1회 실행된 후 실행된다.
- 업데이트 함수 호출 순서 : Update() → LateUpdate()

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void Update()
    {
        Debug.Log("Update함수가 실행되었습니다.");
    }

    private void LateUpdate()
    {
        Debug.Log("LastUpdate함수가 실행되었습니다.");
    }
}

```

### Tip.

- 플레이어 캐릭터, 카메라와 같이 서로 다른 오브젝트가 존재할 때
플레이어 캐릭터를 쫓아다니는 카메라를 구현한다면?
- 플레이어 캐릭터가 Update()를 이용해 움직이고 난 후
- 카메라는 LateUpdate()에서 플레이어의 위치를 바탕으로 이동을 한다.

## FixedUpdate() 함수

- 프레임의 영향을 받지 않고 일정한 간격으로 호출
- Edit - Project Settings - Time 옵션의 Fixed Timestep 변수로 조설 가능
(기본 값 0.02로 0.02초에 1번 호출된다는 뜻, 1초에 50번)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void Update()
    {
        Debug.Log("Update함수가 실행되었습니다.");
    }

    private void LateUpdate()
    {
        Debug.Log("LastUpdate함수가 실행되었습니다.");
    }

    private void FixedUpdate()
    {
        Debug.Log("FixedUpdate함수가 실행되었습니다.");
    }
}

```

# 오브젝트 파괴를 위한 이벤트 함수

## OnDestroy()함수

- 게임오브젝트가 파괴될 때 1회 호출
- 씬이 변경되거나 게임이 종료될 때도 오브젝트가 파괴되기 때문에 호출된다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{

    private void OnDestroy()
    {
        Debug.Log("OnDestroy함수가 실행되었습니다.");
    }
}

```

# 종료를 위한 이벤트 함수

## OnApplicationQuit() 함수

- 게임이 종료될 때 1회 호출한다.
- 유니티 에디터에서는 플레이 모드를 중지할 때 호출된다.

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void OnApplicationQuit()
    {
        Debug.Log("OnApplicationQuit함수가 실행되었습니다.");
    }
}
```

## OnDisable() 함수

- 컴포넌트가 활성화되었다가 비활성화 될 때마다 1회 호출(OnEnable과 반대)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EventFuntionsTest : MonoBehaviour
{
    private void OnDisable()
    {
        Debug.Log("OnDisable함수가 실행되었습니다.");

    }
}

```

# 물리적인 충돌 이벤트 함수

- 매개변수 Collision2D collision

## OnCollisionEnter2D()

- 두 오브젝트가 충돌하는 순간 1회 호출

```csharp
using System.Collections;
using System.Collections.Generic;
using System.Xml.Serialization;
using UnityEngine;

public class CollisionEvent : MonoBehaviour
{
    [SerializeField]
    private Color color;
    private SpriteRenderer spriteRenderer;

    private void Awake()
    {
        spriteRenderer = GetComponent<SpriteRenderer>();
    }
    /// <summary> 충돌이 일어나는 순간 1회 호출
    private void OnCollisionEnter2D(Collision2D collision)
    {
        spriteRenderer.color = color;
    }
}

```

## OnCollisionStay2D()

- 충돌 직후 맞닿아 있는 동안 매 프레임 호출

```csharp
using System.Collections;
using System.Collections.Generic;
using System.Xml.Serialization;
using UnityEngine;

public class CollisionEvent : MonoBehaviour
{
    [SerializeField]
    private Color color;
    private SpriteRenderer spriteRenderer;

    private void Awake()
    {
        spriteRenderer = GetComponent<SpriteRenderer>();
    }
    /// <summary> 충돌이 일어나는 순간 1회 호출
    private void OnCollisionEnter2D(Collision2D collision)
    {
        spriteRenderer.color = color;
    }
    /// <summary> 충돌이 유지되는 동안 매 프레임 호출
    private void OnCollisionStay2D(Collision2D collision)
    {
        Debug.Log(gameObject.name + " : OnCollisionStay2D() 메소드 실행");
    }
}

```

## OnCollisionExit2D()

- 두 오브젝트가 떨어져서 충돌이 중료되는 순간 1회

```csharp
using System.Collections;
using System.Collections.Generic;
using System.Xml.Serialization;
using UnityEngine;

public class CollisionEvent : MonoBehaviour
{
    [SerializeField]
    private Color color;
    private SpriteRenderer spriteRenderer;

    private void Awake()
    {
        spriteRenderer = GetComponent<SpriteRenderer>();
    }
    /// <summary> 충돌이 일어나는 순간 1회 호출
    private void OnCollisionEnter2D(Collision2D collision)
    {
        spriteRenderer.color = color;
    }
    /// <summary> 충돌이 유지되는 동안 매 프레임 호출
    private void OnCollisionStay2D(Collision2D collision)
    {
        Debug.Log(gameObject.name + " : OnCollisionStay2D() 메소드 실행");
    }
    /// <summary> 충돌이 종료되는 순간 1회 호출
    private void OnCollisionExit2D(Collision2D collision)
    {
        spriteRenderer.color = Color.white;
    }
}

```

# 물리적인 충돌 없는 이벤트 함수
![testaa](https://github.com/user-attachments/assets/137a7e4f-42b7-420d-9be9-23a2eeb143e6)


## OnTriggerEnter2D()

- 두 오브젝트가 충돌하는 순간 1회 호출

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TriggerEvent : MonoBehaviour
{
    [SerializeField]
    private GameObject moveObject;
    [SerializeField]
    private Vector3 moveDirection;
    private float moveSpeed;

    private void Awake()
    {
        moveSpeed = 5.0f;
    }
    private void OnTriggerEnter2D(Collider2D collision)
    {
        // moveObject 오브젝트의 색상을 검은색으로 설정한다.
        moveObject.GetComponent<SpriteRenderer>().color = Color.black;
    }

}

```

## OnTriggerStay2D()

- 충돌 직후 맞닿아 있는 동안 매 프레임 호출

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TriggerEvent : MonoBehaviour
{
    [SerializeField]
    private GameObject moveObject;
    [SerializeField]
    private Vector3 moveDirection;
    private float moveSpeed;

    private void Awake()
    {
        moveSpeed = 5.0f;
    }
    private void OnTriggerEnter2D(Collider2D collision)
    {
        // moveObject 오브젝트의 색상을 검은색으로 설정한다.
        moveObject.GetComponent<SpriteRenderer>().color = Color.black;
    }

    private void OnTriggerStay2D(Collider2D collision)
    {
        // moveObject 오브젝트를 moveDirection 방향으로 이동한다.
        moveObject.transform.position += moveDirection * moveSpeed * Time.deltaTime;
    }
    
}

```

## OnTriggerExit2D()

- 두 오브젝트가 떨어져서 충돌이 중료되는 순간 1회

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TriggerEvent : MonoBehaviour
{
    [SerializeField]
    private GameObject moveObject;
    [SerializeField]
    private Vector3 moveDirection;
    private float moveSpeed;

    private void Awake()
    {
        moveSpeed = 5.0f;
    }
    private void OnTriggerEnter2D(Collider2D collision)
    {
        // moveObject 오브젝트의 색상을 검은색으로 설정한다.
        moveObject.GetComponent<SpriteRenderer>().color = Color.black;
    }

    private void OnTriggerStay2D(Collider2D collision)
    {
        // moveObject 오브젝트를 moveDirection 방향으로 이동한다.
        moveObject.transform.position += moveDirection * moveSpeed * Time.deltaTime;
    }
    private void OnTriggerExit2D(Collider2D collision)
    {
        // moveObject 오브젝트를 색상을 흰색으로 설정한다.
        moveObject.GetComponent <SpriteRenderer>().color = Color.white;
        // moveObject 오브젝트의 위치를 (0, 4, 0)으로 설정한다.
        moveObject.transform.position = new Vector3(0, 4, 0);
    }
}

```
