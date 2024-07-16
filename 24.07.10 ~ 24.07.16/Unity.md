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
