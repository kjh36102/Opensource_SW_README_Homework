# 오픈소스 SW README 작성 과제
리눅스 명령어 top, ps, jobs, kill 그리고 vim 매크로 사용방법 조사

#### 작성자
- [@20184356 김주현](https://www.github.com/kjh36102)

### 조사하게 될 내용은...
이번 과제에서는 리눅스 명령어 4가지와 vim 에디터에서의 매크로 사용방법을 알아보겠습니다.

---

### Index
- [top](#top-명령어)
- [ps](#ps-명령어)
- [kill](#kill-명령어)
- [jobs](#jobs-명령어)
- [Vim 매크로](#vim-매크로)
- [참고문헌](#참고문헌)

---

# top 명령어
`top` 명령어는 **현재 OS의 상태**를 나타내주는 명령어입니다.
아래 이미지는 `top` 명령을 실행했을 때 나타나는 모습입니다.
`top` 명령어의 정보는 두가지 영역([**요약 영역**](#요약-영역), [**디테일 영역**](#디테일-영역))으로 나뉩니다.

![image](https://user-images.githubusercontent.com/88638058/172028686-adfe74dd-f4fc-42ca-92d3-405d89e25fe1.png)

## 요약 영역
요약 영역은 위 이미지에서 **강조된 라인 윗부분**을 말합니다.
요약 영역은 전체 프로세스가 OS에 대해서 **리소스를 어느정도 차지하고 있는지**를 알려줍니다.
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

가장 먼저 보이는 숫자는 **System time** 입니다. 이는 GMT 기준으로 표시되어 있습니다.
`up` 다음으로 표시되는 것은 **Uptime** 으로, OS가 구동된 후 경과일을 나타냅니다.
그 다음 `users` 왼쪽에 표시된 숫자는 현재 접속중인 세션 수 입니다.

![image](https://user-images.githubusercontent.com/88638058/172029496-50cc2b37-3ae6-4eba-a113-ed7197194793.png)

좀 더 자세한 세션 정보가 궁금하다면 `who` 명령을 이용할 수 있습니다.

![image](https://user-images.githubusercontent.com/88638058/172029249-d53ef4c6-9ccc-4c8f-ac36-7eccd7071fe8.png)

---
### Load average
Load average 영역은 **CPU Load의 이동 평균**을 나타냅니다. 3개의 실수가 `,`로 구분되어 있는데 앞에서부터
각각 1분, 5분, 15분에 대한 평균값을 나타냅니다. CPU의 코어가 **1**개인 경우는 `1.0`이 100%의 부하를 말하고,
**8**개인 경우는 `8.0`이 100%의 부하를 나타냅니다.

![image](https://user-images.githubusercontent.com/88638058/172029503-a620671d-4cfa-4a9d-be8a-6428e4412101.png)

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

## 유용한 top 단축키
* `k` : 프로세스 종료하기
* `M` : 메모리 사용량순 정렬
* `P` : CPU 점유율순 정렬
* `N` : Process ID순 정렬
* `T` : Running Time 순 정렬
* `H` : 스레드를 기준으로 정보 표시
* `O` : 프로세스 검색 및 필터링

[[Index]](#index)

---

# ps 명령어

ps 명령어는 현재 실행중인 프로세스 목록과 상태를 보여줍니다.

#### ps 명령어 사용법
`$ ps [option]`

### Options
명령어의 option이 될 수 있는 것들은 아래와 같습니다.

| Option | Desc |
| :-- | :-- |
| `-A` | 모든 프로세스를 출력 |
| `a` | 터미널과 연관된 프로세스를 출력 |
| `-a` | 세션 리더를 제외한 터미널에 종속되지 않은 모든 프로세스 출력 |
| `-e` | 커널 프로세스를 제외한 모든 프로세스를 출력 |
| `-f` | 풀 포맷으로 출력 |
| `-l` | 긴 포맷으로 출력 |
| `-o` | 출력 포맷을 지정하는 옵션으로 값으로는 pid, tty, time, cmd |
| `-M` | 64비트 프로세스 출력 |
| `-m` | 프로세스 + 커널 스레드 출력 |
| `-p` | 특정 PID를 지정할 때 사용 |
| `-r` | 현재 실행 중인 프로세서 출력 |
| `u` | 소유자를 기준으로 출력 |
| `-u` | 특정 사용자의 프로세스 정보 출력 |
| `x` |  터미널에 종속되지 않는 프로세스를 출력 |
| `-x` | 로그인 상태에 있는 동안 아직 완료되지 않은 프로세스 출력 |

### 사용 예시
`$ ps aux `

![image](https://user-images.githubusercontent.com/88638058/172030447-1ad855e7-d8f4-4d95-9efd-c24ce3ed0a17.png)

각 레이블이 나타내는 정보는 아래와 같습니다.

| Label | Desc |
| :-- | :-- |
|  USER | BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름  |
| UID  | SYSTEM V계열에서 나타나는 항목으로 프로세스 소유자의 이름  |
| PID  | 프로세스의 식별변호   |
|  PPID |  부모 프로세스 ID |
| %CPU  |  CPU 사용 비율의 추정치(BSD) |
| %MEM  |  메모리의 사용 비율의 추정치 (BSD) |
|  VSZ |  K단위 또는 페이지 단위의 가상메모리 사용량 |
|  RSS | 실제 메모리 사용량 (Resident Set Size)  |
| TTY  | 프로세스와 연결된 터미널   |
|  S, STAT |  현재 프로세스의 상태 코드 (S: Sys V, STAT: BSD) |
| TIME  |  총 CPU 사용 시간 |
|  COMMAND | 프로세스의 실행 명령행  |
| STIME  |  프로세스가 시작된 시간 혹은 날짜 |
| C, CP  | 짧은 기간 동안의 CPU 사용률 (C: Sys V, CP: BSD)  |
|  F |  프로세스의 플래그  |
|  PRI |  실제 실행 우선순위 |
| NI  | nice 우선순위 번호   |

[[Index]](#index)

---

# kill 명령어
`kill` 명령어는 프로세스에 시그널을 보내는 명령어입니다. 프로세스는 시그널을 받았을 때 기본 동작이
**종료** 이기 때문에 `kill`로 명명되었습니다. `ps` 명령어와 함께 자주 사용됩니다.

#### 시그널의 종류
`kill` 로 보낼 수 있는 시그널의 종류는 `$ kill -l` 명령으로 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/88638058/172030827-7944d1fd-cd62-4360-9bf5-4e02f18715d0.png)

#### 사용 예시
* `$ kill -INT 123`
* `$ kill -2 123`

위 두 명령어는 **같은 동작**을 합니다. 시그널 레이블에서 `SIG`를 뺀 나머지 부분을 두번째 옵션으로 주는 것과,
시그널 번호를 입력하는 것은 같은것으로 취급됩니다. `123`은 PID(프로세스 ID) 입니다.

[[Index]](#index)

---

# jobs 명령어
jobs 명령어는 **작업 상태를 표시**하는 명령어입니다. 현재 쉘 세션에서 실행시킨 백그라운드 작업 목록이
출력되며, 각 작업은 번호가 붙어있어 `kill` 명령어 뒤에 작업의 번호를 붙여 사용할 수 있습니다.

![image](https://user-images.githubusercontent.com/88638058/172030622-7bbff856-3926-4b10-aac4-0a8c0396a5d1.png)

#### 사용법
`$ jobs [옵션][작업번호]`

#### 예시
* `$ jobs kill %1 %3` : 1번 3번 작업을 종료

### 작업의 상태
작업의 상태를 나타내는 값은 아래와 같습니다.

| State | Desc |
| :-- | :-- |
| Running  | 작업이 계속 진행중임  |
| Done  |  작업이 완료되어 0을 반환 |
|  Done(code) | 작업이 종료되었으며 0이 아닌 코드를 반환  |
|  Stopped | 작업이 일시 중단  |
| Stopped(SIGTSTP)  |  SIGTSTP 시그널이 작업을 일시 중단 |
| Stopped(SIGSTOP)  |  SIGSTOP 시그널이 작업을 일시 중단 |
|  Stopped(SIGTTIN) |  SIGTTIN 시그널이 작업을 일시 중단 |
| Stopped(SIGTTOU)  | SIGTTOU 시그널이 작업을 일시 중단  |

### 옵션
옵션이 될 수 있는 값은 아래와 같습니다.

| Option | Desc |
| :-- | :-- |
|  -l | 프로세스 그룹 ID를 state 필드 앞에 출력  |
| -n  | 프로세스 그룹 중에 대표 프로세스 ID를 출력  |
|   -p |   각 프로세스 ID에 대해 한 행씩 출력 |
|  command	  |  지정한 명령어를 실행  |

[[Index]](#index)

---

# Vim 매크로
Vim 에디터에서 매크로 기능은 **막강**합니다. 반복적이고 지루한 편집작업을 미리 기록해두고 **나중에 단축키 한번**만
누르면 해당 작업을 반복해줍니다.

## 매크로 사용 방법
매크로 사용을 위한 일련의 순서는 아래와 같습니다.

    1. 매크로 저장하기
    2. 매크로 사용하기
    3. 파일에 저장하기 (재사용을 원한다면)

### 1. 매크로 저장하기
매크로를 저장하는 방법은 먼저 `q`를 누르고 그 다음 **바로** 저장할 문자를 누릅니다.
예를들어 a라는 문자에 매크로를 저장하려면 `qa` 를 입력하면 됩니다.

`qa`를 눌렀다면 **기록모드**로 전환됩니다. 이 상태에서 입력되는 키는 모두 매크로에 기록됩니다.

매크로 작성이 끝났다면 **다시** `q`를 눌러 매크로 작성을 마칩니다. 이제 `a`키에 매크로가 **저장**되었습니다.

### 2. 매크로 사용하기
특정 문자에 저장된 매크로를 실행하는 방법은 **먼저** `@`를 입력하고 저장된 문자를 누릅니다.
위에서 `a`에 저장된 매크로를 실행하려면 `@a`를 입력하면 됩니다.

매크로를 **여러번** 반복하려면 `@` 앞에 반복 횟수를 붙여줍니다. 예를들어 `a`매크로를 10번 반복하려면
`10@a`를 입력하면 됩니다.

마지막으로 수행한 매크로를 **다시 실행**하려면 `@@`를 입력하면 됩니다.

### 3. 매크로 저장하기
매 편집마다 매크로를 설정하고 사용하기는 번거롭습니다. 따라서 **파일에 미리 저장**했다가 불러올 수
있는 방법을 제공합니다.

#### 3-1. ~/.vimrc 파일 열기
매크로를 저장하려면 `~/.vimrc` 파일을 열어 그 안에 매크로를 기록해야 합니다.

Vim 에디터에서 아래 명령어를 입력하면 이동할 수 있습니다.

`:w`

`:e ~/.vimrc`

#### 3-2. 매크로 이름을 변수로 삼아 매크로 저장하기
예시로 `a`키에 매크로를 미리 작성해보겠습니다.
`~/.vimrc` 파일 내부에 다음과 같은 내용을 한 줄 추가합니다.

`let @a='fewoif wweoif woef ijwof ijwof wef^Mwoefjiwe fwefwq^['`

![image](https://user-images.githubusercontent.com/88638058/172031933-ff795368-7611-4685-a3eb-db47f12620db.png)

알아둘 점은 작은 따옴표 `''` 내부에는 사용자가 원하는 키 입력을 나열해야 합니다.

그 후 `:wq!` 또는 `:x` 로 저장한 뒤 저장된 매크로를 이용하면 됩니다.
    
[[Index]](#index)

---

## 참고 문헌
- [[Linux] top 명령어로 서버의 상태 파악하기](https://sabarada.tistory.com/146)
- [[리눅스, 유닉스] ps 프로세스 명령어 완벽정리, 프로세스 관리, 계열에 따른 옵션 차이, 조건에 맞게 프로세스 정보 추출하기](https://jhnyang.tistory.com/268)
- [Unix, Linux 에서 kill 명령어로 안전하게 프로세스 종료 시키는 방법](https://www.lesstif.com/system-admin/unix-linux-kill-12943674.html)
- [[Linux] jobs 명령어 사용법](https://hbase.tistory.com/265)
- [6일차: vim 매크로 사용](https://clem.tistory.com/29)

[[Top]](#오픈소스-sw-readme-작성-과제)
