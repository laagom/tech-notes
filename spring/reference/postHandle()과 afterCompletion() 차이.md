# postHandle()과 afterCompletion() 차이

| 메서드                 | 실행 시점                       | 예외발생 시           | 주로 하는 일                |
| ------------------- | --------------------------- | ---------------- | ---------------------- |
| `postHandle()`      | Controller 실행 후, View 렌더링 전 | 예외 발생 시 호출 되지 않음 | Model 수정, View 결정 전 가공 |
| `afterCompletion()` | View 렌더링 후, 응답까지 모두 끝난 후    | 예외 발생해도 호출 됨     | 리소스 정리, 로깅, 예외 추적      |

```scss
클라이언트 요청
    ↓
preHandle()
    ↓
Controller 실행
    ↓
postHandle() ← 결과 조작 가능 (ModelAndView)
    ↓
View Rendering (템플릿 처리)
    ↓
afterCompletion() ← 예외 여부와 무관하게 마지막 정리 작업
    ↓
응답 전송 완료

```
