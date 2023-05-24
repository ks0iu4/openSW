# OpenSourceSW 과제
### 20233093_김시우
---
## top
+ 시스템의 상태를 전반적으로 가장 빠르게 파악 가능
+ 옵션 없이 입력하면 3초 간격으로 화면을 갱신하며 정보를 보여줌
+ **top** 실행 전 옵션
  + `-b` : 순간의 정보 확인 (batch 모드)
  + `-n` : top 실행 주기 설정 (반복 횟수)
+ **top** 실행 후 옵션
  | Option | Content |
  |:---:|:---:|
  | `shift` + `p` | CPU 사용률 내림차순 |
  | `shift` + `m` | 메모리 사용률 내림차순 |
  | `shift` + `t` | 프로세스가 돌아가고 있는 시간 순 |
  | `k` | `kill`, `k` 입력 후 PID 번호 작성, signal은 9 |
  | `f` | sort field 선택 화면 -> q 누르면 RES순으로 정렬 |
  | `a` | 메모리 사용량에 따라 정렬 |
  | `b` | batch 모드로 작동 |
  | `1` | CPU Core별로 사용량을 보여줌 |
 
+ `top -n 1`
![image](https://github.com/ks0iu4/openSW/assets/132364542/f17d420d-97cc-44dc-bc39-9952a584bd81)
  + `25 min` : 25분 전 구동
  + `load average` : 현재 시스템이 얼마나 일을 하는지를 나타냄.
    + 3개의 숫자는 1분, 5분, 15분 간의 평균 실행/대기 중인 프로세스의 수
  + `Tasks` : 프로세스 개수
  + `MiB Mem` `MiB Swap` : 각 메모리의 사용량
  + `PR` : 실행 우선순위
  + `VIRT` : 프로세스가 사용하고 있는 가상 메모리의 전체 용량
    + SWAP + RES
  + `RES` : 프로세스가 사용하고 있는 물리 메모리의 양
  + `SHR` : 다른 프로세스와 공유하고 있는 공유 메모리의 양
  + `S` : 프로세스 상태
---
## ps
+ 현재 실행중인 프로세스 목록과 상태를 보여줌
+ 옵션 사용
  + `System V` : `-`
  + `BSD` : ` ` 
  + `GNU` : `--`


  | Option | Content |
  |:---:|:---:|
  | `-A` | 모든 프로세스 출력 |
  | `a`(BSD) | 터미널과 연관된 프로세스 출력 |
  | `-a` | 세션 리더를 제외하고 터미널에 종속되지 않은 모든 프로세스 출력 |
  | `-e` | 커널 프로세스를 제외한 모든 프로세스 출력 |
  | `-f` | 풀 포맷으로 출력 |
  | `-l` `l`(BSD) | 긴 포맷으로 출력 |
  | `-o` 값 | 출력 포맷을 지정 |
  | `-M` | 64비트 프로세스 출력 |
  | `-m` | 커널 스레드 출력 |
  | `-p` | 특정 PID를 지정할 때 사용 |
  | `-r` | 현재 실행 중인 프로세스 출력 |
  | `u`(BSD) | 프로세스 소유자를 기준으로 출력 |
  | `-u` | 특정 사용자의 프로세스 정보 확인 |
  | `x`(BSD) | 터미널에 종속되지 않은 프로세스 출력 |
  | `-x` | 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서 출력 |
  
+ `ps -ef`
![image](https://github.com/ks0iu4/openSW/assets/132364542/7465c40e-deb1-4687-9b80-a327a447ebbf)
  + `PID` : 프로세스의 식별번호
  + `PPID` : 부모 프로세스 ID
  + `C` : 짧은 시간 동안의 CPU 사용률
  + `STIME` : 프로세스가 시작된 시간
  + `TTY` : 프로세스와 연결된 터미널
  + `TIME` : 총 CPU 사용 시간
  + `CMD` : 프로세스의 실행 명령행
---
## jobs
+ 작업의 상태를 표시해줌
+ 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록 출력

| Option | Content |
|:---:|:---:|
| `-l` | 프로세스 그룹 ID를 state 필드 앞에 출력 |
| `-n` | 프로세스 그룹 중에 대표 프로세스 ID를 출력 |
| `-p` | 각 프로세스 ID에 대해 한 행씩 출력 |
| `cmd` | 지정한 명령어를 실행 |

![image](https://github.com/ks0iu4/openSW/assets/132364542/fe83673d-4bd7-451c-b350-deda3ce47d9c)

| State | Content |
|:---:|:---:|
| `Running` | 작업이 계속 진행중임 |
| `Done` | 작업이 완료되어 0을 반환 |
| `Done(code)` | 작업이 종료되었으며 0이 아닌 코드를 반환 |
| `Stopped` | 작업이 일시 중단 |
| `Stopped(SIGTSTP)` | SIGTSTP 시그널이 작업을 일시 중단 |
| `Stopped(SIGSTOP)` | SIGSTOP 시그널이 작업을 일시 중단 |
| `Stopped(SIGTTIN)` | SIGTTIN 시그널이 작업을 일시 중단 |
| `Stopped(SIGTTOU)` | SIGTTOU 시그널이 작업을 일시 중단 |

---
## kill
+ 프로세스를 지정하고 신호를 보내서 제어하는 명령어
+ 주로 프로세스를 종료하는 용도로 사용

| Option | Content |
|:---:|:---:|
| `-9` | PID를 직접 지정하여 종료 |
| `-l` | 신호로 사용할 수 있는 신호 이름들 출력 |

| Number | Signal name | Signal | Content |
|:---:|:---:|:---:|:---:|
| 1 | `SIGHUP` | `HUP` | 특정 실행 중인 프로그램이 사용하는 설정 파일 변경 및 변화된 내용 적용 |
| 2 | `SIGINT` | `INT` | 현재 작동중인 프로그램 동작 멈추기 |
| 9 | `SIGKILL` | `KILL` | 프로그램 무조건 종료 |
| 11 | `SIGSEGV` | `SEGV` | 잘못된 메모리 관리시 생기는 신호 |
| 15 | `SIGTERM` | `TERM` | 실행중인 프로그램의 정상적인 종료방법 |
| 18 | `SIGCONT` | `CONT` | 중지 되어 있는 프로그램 재실행 |
| 19 | `SIGSTOP` | `STOP` | 프로그램 중지 |
| 20 | `SIGTSTP` | `TSTP` | 터미널에서 중지되어 있는 신호 |

---
