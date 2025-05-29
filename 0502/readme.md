# 🔅System programming week9🔅

# 🖥️ 컴퓨터 시스템 구조

---

## ● 유닉스 커널 (kernel)
- 하드웨어를 운영 관리하여 다음과 같은 서비스를 제공

| 서비스 종류             | 설명                    |
|-----------------------|-----------------------|
| 파일 관리 (File management)       | 파일과 디렉터리 관리          |
| 프로세스 관리 (Process management) | 프로세스 생성 및 관리          |
| 메모리 관리 (Memory management)   | 메모리 할당 및 관리           |
| 통신 관리 (Communication management) | 프로세스 간 통신 관리          |
| 주변 장치 관리 (Device management)   | 하드웨어 장치 제어 및 관리      |

<img width="617" alt="image" src="https://github.com/user-attachments/assets/bcff8191-d088-45a9-8b7b-ca6781adb7fd" />

# ⚙️ 시스템 호출 요약

---

## ● 주요 자원과 관련 시스템 호출

| 주요 자원     | 시스템 호출 예시                                  |
|--------------|-------------------------------------------------|
| **파일**       | `open()`, `close()`, `read()`, `write()`, `dup()`, `lseek()` 등 |
| **프로세스**   | `fork()`, `exec()`, `exit()`, `wait()`, `getpid()`, `getppid()` 등 |
| **메모리**     | `malloc()`, `calloc()`, `free()` 등             |
| **시그널**     | `signal()`, `alarm()`, `kill()`, `sleep()` 등    |
| **프로세스 간 통신** | `pipe()`, `socket()` 등                        |

---

# 파일 열기 : open()
- 파일을 사용하기 위해서는 먼저 open() 시스템 호출을 이용하여 파일을 열어야 한다.
# 📂 `open()` 함수 사용 예제

```c
fd = open("account", O_RDONLY);
// "account" 파일을 읽기 전용으로 연다.

fd = open(argv[1], O_RDWR);
// 명령행 인자로 받은 파일을 읽기/쓰기 모드로 연다.

fd = open(argv[1], O_RDWR | O_CREAT, 0600);
// 명령행 인자로 받은 파일을 읽기/쓰기 모드로 열고, 없으면 생성한다.
// 새 파일 권한은 0600 (소유자 읽기/쓰기)

fd = open("tmpfile", O_WRONLY | O_CREAT | O_TRUNC, 0600);
// "tmpfile"을 쓰기 전용으로 열고, 없으면 생성, 기존 내용은 지운다.

fd = open("/sys/log", O_WRONLY | O_APPEND | O_CREAT, 0600);
// "/sys/log" 파일을 쓰기 전용으로 열고, 없으면 생성, 내용을 덧붙인다.

if ((fd = open("tmpfile", O_WRONLY | O_CREAT | O_EXCL, 0666)) == -1) {
    // "tmpfile"이 존재하면 실패(-1) 반환, 없으면 생성 후 열기
}
```
<img width="611" alt="image" src="https://github.com/user-attachments/assets/0299d280-123c-4eea-ae31-9a0e6c650ce5" />

# 파일 생성: creat()
- creat() 시스템 호출
  - path가 나타내는 파일을 생성하고 쓰기 전용으로 연다.
  - 생성된 파일의 사용권한은 mode로 정한다.
  - 기존 파일이 있는 경우에는 그 내용을 삭제하고 연다.

# 파일 닫기 : close()
- close() 시스템 호출은 fd가 나타내는 파일을 닫는다.
```c
#include <unistd.h>
int close( int fd );
```

# 데이터 읽기 : read()
- read() 시스템 호출
  - fd가 나타내는 파일에서 nbytes 만큼의 데이터를 읽고 일긍ㄴ 데이터는 buf에 저장한다
```c
#include <unistd.h>
ssize_t read (int fd, void *buf, size_t nbytes);
```
<img width="485" alt="image" src="https://github.com/user-attachments/assets/8a7c619d-133b-4b96-b7c7-39d5239941d6" />

# 데이터 쓰기 : write()
- write() 시스템 호출
 - buf에 있는 nbytes 만큼의 데이터를 fd가 나타내는 파일에 쓴다.
```c
#include <unistd.h>
ssize_t write (int fd, void *buf, size_t nbytes);
```
<img width="490" alt="image" src="https://github.com/user-attachments/assets/446f0ade-629a-4c4f-93de-fac68c0a1adf" />


