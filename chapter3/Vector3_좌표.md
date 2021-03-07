# Vector

- float x, y, z 를 가지고 있음.
- 유니티 엔진에서는 y 가 높이, z 가 전방 방향을 의미하는 게 보통.
- 크게 위치벡터, 방향 벡터로 구분
- 덧셈, 뺄셈 등의 오퍼레이터 연산 지원
- 출발지점에서 목표지점으로 가기 위한 방향벡터(방향 + 크기)는, `목표지점 벡터 - 출발지점 벡터  (to - from)` 이다.
- 즉 방향벡터는 거리(크기) 뿐만 아니라 방향까지 둘 다 가지는 값이다.

## 크기 (magnitude)
피타고라스의 정리를 이용한다. 3차원이기 때문에 z 축까지 더해주어야 한다. (x,z 로 밑변 구하고 그 다음에 y 까지 고려하는 느낌?)
- `Math.Sqrt(x*x + y*y + z*z)`

## 단위벡터 (normalized)
크기를 무시한 방향만을 고려하는 크기가 1인 벡터
- `x / magnitude, y/magnitude, z/magnitude` 의 벡터 값.

## 월드좌표 로컬좌표
- Local -> World 로 좌표 변환시 TransformDirection
- World -> Local 변환시 InverseTransformDirection
- 하지만 그냥 transform.Translate() 를 쓰면 알아서 로컬 기준으로 (현재 obj 기준으로) 해준다...

```c#
// 아래 두 코드는 하고자 하는 게 동일함.
transform.Translate(Vector3.forward * Time.deltaTime * _speed);
transform.position += transform.TransformDirection(Vector3.forward * Time.deltaTime * _speed);
```