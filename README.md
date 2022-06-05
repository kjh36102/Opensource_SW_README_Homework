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
### System time, Uptime, User session

![image](https://user-images.githubusercontent.com/88638058/172029496-50cc2b37-3ae6-4eba-a113-ed7197194793.png)

가장 먼저 보이는 숫자는 **System time** 입니다. 이는 GMT 기준으로 표시되어 있습니다.
`up` 다음으로 표시되는 것은 **Uptime** 으로, OS가 구동된 후 경과일을 나타냅니다.
그 다음 `users` 왼쪽에 표시된 숫자는 현재 접속중인 세션 수 입니다.

좀 더 자세한 세션 정보가 궁금하다면 `who` 명령을 이용할 수 있습니다.

![image](https://user-images.githubusercontent.com/88638058/172029249-d53ef4c6-9ccc-4c8f-ac36-7eccd7071fe8.png)

---

### Load average

![image](https://user-images.githubusercontent.com/88638058/172029503-a620671d-4cfa-4a9d-be8a-6428e4412101.png)

Load average 영역은 **CPU Load의 이동 평균**을 나타냅니다. 3개의 실수가 `,`로 구분되어 있는데 앞에서부터
각각 1분, 5분, 15분에 대한 평균값을 나타냅니다. CPU의 코어가 **1**개인 경우는 `1.0`이 100%의 부하를 말하고,
**8**개인 경우는 `8.0`이 100%의 부하를 나타냅니다.

---

### Tasks info
2번째 줄은 Task에 관한 정보를 나타냅니다.

![image](https://user-images.githubusercontent.com/88638058/172029676-7451cdba-e557-4a46-aca5-5eff00af5289.png)

| Label | Desc |
| :--   | :--  |
| total | 전체 프로세스 |
| running | 실행중인 프로세스 |
| sleeping | 대기중인 프로세스 |
| stopping | 종료된 프로세스 |
| zombies | 좀비상태의 프로세스 |

---

### CPU info

![image](https://user-images.githubusercontent.com/88638058/172029715-46183774-ad78-4bd4-a59c-7c43413e2852.png)

3번째 줄은 **CPU 사용량**과 관련된 정보를 나타냅니다. 모든 값의 총 합은 100% 입니다.

| Label | Desc |
| :--   | :--  |
| us | 유저 영역에서의 CPU 사용률 |
| sy | 커널 영역에서의 CPU 사용률 |
| ni | 우선순위 설정에 쓰이는 CPU 사용률 |
| id | 사용되지 않는 비율 |
| wa | IO 대기를 기다리는 비율 |
| hi | HW 인터럽트에 사용되는 비율 |
| si | SW 인터럽트에 사용되는 비율 |
| st | VM에서 사용하여 대기하는 비율 |

---

### Memory usage

![image](https://user-images.githubusercontent.com/88638058/172029805-68f4af5b-cd14-41aa-97df-690af970ffad.png)

**메모리 사용량**을 나타내는 영역으로, 1번째 줄은 RAM 사용량을 나타냅니다.
2번째 줄은 가상메모리, 즉 SWAP 사용량을 나타냅니다.

---

## 디테일 영역

![image](https://user-images.githubusercontent.com/88638058/172029855-b770f18f-cb3d-4e11-afa0-74ef432f7ab5.png)

디테일 영역에는 **각 프로세스에 대해 좀 더 자세한 정보**를 확인할 수 있습니다.
디테일 영역이 나타내는 정보는 아래와 같습니다.

| Label | Desc |
| :--   | :--  |
| PID | 프로세스의 ID |
| USER | 프로세스를 실행하는 유저 |
| PR | 스케줄링 우선순위 |
| NI | PR에 영향을 주는 nice 값 |
| VIRT | 프로세스의 총 메모리 점유율 |
| RES | 프로세스가 RAM에서 사용중인 크기 |
| SHR | 다른 프로세스와의 공유메모리 |
| S | 프로세스의 현재 상태 |
| %CPU | 프로세스의 CPU 점유율 |
| %MEM | RAM에서 RES가 차지하는 비율 |
| TIME+ | 프로세스가 사용한 총 CPU시간 |
| COMMAND | 해당 프로세스를 실행한 명령어 |


---

## 유용한 top 커맨드
* `k` : 프로세스 종료하기
* `M` : 메모리 사용량순 정렬
* `P` : CPU 점유율순 정렬
* `N` : Process ID순 정렬
* `T` : Running Time 순 정렬
* `H` : 스레드를 기준으로 정보 표시
* `O` : 프로세스 검색 및 필터링


