### 저절로 움직이기

```C#
using UnityEngine;

public class Movement2D : MonoBehaviour
{
    private void Update()
    {
        // 새로운 위치 = 현재 위치 + (방향 * 속도)
        // transform.position = transform.position + new Vector3(1, 0, 0) * 1;

        transform.position += Vector3.right * 1 * Time.deltaTime;
        // Time.deltaTime : 이전 Update() 종료부터 다음 Update() 시작까지의 시간
        // 컴퓨터 사양이 높을수록 그 시간이 짧다. 60초에 120회면 0.5
        // 그래서 곱해주면 사양이 다른 컴퓨터끼리도 같은 속도로 움직이게 됨
    }
}
```

### 방향키로 움직이기

```C#
using UnityEngine;

public class Movement2D : MonoBehaviour
{
    private float moveSpeed = 5.0f; // 이동 속도
    private Vector3 moveDirection = Vector3.zero; // 이동 방향

    private void Update()
    {
        // GetAxisRaw : Edit -> Project Setting -> Input Manager 의 단축키 이용

        // float value = Input.GetAxisRaw("단축키명");
        // 긍정(Positive) : +1, 부정(Negative) : -1, 대기 : 0

        // float value = Input.GetAxis("단축키명");
        // GetAxisRaw()는 키를 누르면 바로 1 or -1이 되지만
        // GetAxis()는 키를 누르고 있으면 0에서 1 or -1로 서서히 증가.(부정도 마찬가지)

        float x = Input.GetAxisRaw("Horizontal"); // 좌우 이동
        float y = Input.GetAxisRaw("Vertical"); // 상하 이동

        // 이동방향 설정
        moveDirection = new Vector3(x, y, 0);

        // 새로운 위치 = 현재 위치 + (방향 * 속도)
        transform.position += moveDirection * moveSpeed * Time.deltaTime;
    }
}
```
