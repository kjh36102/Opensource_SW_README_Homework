# 오픈소스 SW README 작성 과제
리눅스 명령어 top, ps, jobs, kill 그리고 vim 매크로 사용방법 조사

#### 작성자
- [@20184356 김주현](https://www.github.com/kjh36102)

### 조사하게 될 내용은...
이번 과제에서는 리눅스 명령어 4가지와 vim 에디터에서의 매크로 사용방법을 알아보겠습니다.

---

### 리눅스 명령어
- top
- ps
- jobs
- kill

---

# top 명령어
top 명령어는 **현재 OS의 상태**를 나타내주는 명령어입니다.
아래 이미지는 top 명령을 실행했을 때 나타나는 모습입니다.

![image](https://user-images.githubusercontent.com/88638058/172028686-adfe74dd-f4fc-42ca-92d3-405d89e25fe1.png)

## 요약 영역
요약 영역은 위 이미지에서 **강조된 라인 윗부분**을 말합니다.
요약 영역은 전체 프로세스가 OS에 대해서 리소스를 어느정도 차지하고 있는지를 알려줍니다.
요약 영역에서 확인할 수 있는 값은 아래와 같습니다.

![image](https://user-images.githubusercontent.com/88638058/172028863-ea3c910d-256a-4e0d-a978-f520d440919f.png)

### 요약 영역의 Values
| Values                  | Description                                |
| :------------------     | :----------                                |
| System time | 현재 시스템 시간 |
| Uptime | 서버 시작 후 경과일 |
| User session | 현재 접속중인 유저 수 |
| Load average | 시스템 부하 평균 |
| Tasks info | Task 관련 정보 |
| CPU info | CPU 관련 정보 |
| Memory usage | 메모리 사용량 |

---

&nbsp;

![image](https://user-images.githubusercontent.com/88638058/172029496-50cc2b37-3ae6-4eba-a113-ed7197194793.png)

### System time, Uptime, User session
가장 먼저 보이는 숫자는 **System time** 입니다. 이는 GMT 기준으로 표시되어 있습니다.
`up` 다음으로 표시되는 것은 **Uptime** 으로, OS가 구동된 후 경과일을 나타냅니다.
그 다음 `users` 왼쪽에 표시된 숫자는 현재 접속중인 세션 수 입니다.

좀 더 자세한 세션 정보가 궁금하다면 `who` 명령을 이용할 수 있습니다.

![image](https://user-images.githubusercontent.com/88638058/172029249-d53ef4c6-9ccc-4c8f-ac36-7eccd7071fe8.png)

---

&nbsp;

![image](https://user-images.githubusercontent.com/88638058/172029503-a620671d-4cfa-4a9d-be8a-6428e4412101.png)

### Load average
Load average 영역은 **CPU Load의 이동 평균**을 나타냅니다. 3개의 실수가 `,`로 구분되어 있는데 앞에서부터
각각 1분, 5분, 15분에 대한 평균값을 나타냅니다.
