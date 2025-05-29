# 🔅System programming week11🔅

# 🗂 파일 시스템 구조 (File System Structure)

유닉스 및 리눅스 기반 시스템의 파일 시스템은 아래와 같은 **4가지 주요 구성 요소**로 이루어져 있습니다.

---

## 1️⃣ 부트 블록 (Boot Block)
- 파일 시스템의 **가장 시작 부분**에 위치 (보통 첫 번째 섹터)
- 시스템이 부팅할 때 사용하는 **부트스트랩 코드**가 저장됨

---

## 2️⃣ 슈퍼블록 (Super Block)
- 파일 시스템 전체에 대한 **중요한 메타데이터**를 저장
- 포함 정보:
  - 총 블록 수
  - 사용 가능한 i-노드 개수
  - 사용 가능한 블록 비트맵
  - 블록 크기
  - 사용 중인 블록 수
  - 사용 가능한 블록 수 등

---

## 3️⃣ i-리스트 (i-list)
- **모든 i-노드(i-node)**들을 포함하는 리스트
- 각 i-노드는 하나의 파일을 나타냄
- 한 블록에는 약 **40개의 i-노드**가 저장 가능

---

## 4️⃣ 데이터 블록 (Data Block)
- 실제 **파일의 내용(데이터)**이 저장되는 블록들
- 파일이 커질수록 여러 데이터 블록을 사용하게 됨

---

> ✅ **요약**:  
파일 시스템은 부트 블록 → 슈퍼블록 → i-리스트 → 데이터 블록의 순서로 구성되며, 각각은 시스템 부팅, 파일 메타데이터 관리, 파일 식별, 실제 데이터 저장의 역할을 담당합니다.

# 📂 파일 열기 및 파일 입출력 구현

---

## 🔓 파일 열기: `open()`

- `open()` 시스템 호출은 커널에게 **파일을 사용할 준비**를 하도록 요청합니다.
- 성공 시, 해당 파일에 대한 **파일 디스크립터(정수)**를 반환합니다.
- 이 디스크립터는 이후 `read()`, `write()`, `close()` 등의 함수에서 파일을 식별하는 데 사용됩니다.

---

## 🧠 파일 입출력 구현을 위한 커널 내 자료구조

리눅스 커널은 파일 입출력 구현을 위해 아래의 **3가지 주요 자료구조**를 사용합니다:

---

### 1️⃣ 파일 디스크립터 배열 (File Descriptor Array)

- **프로세스 단위**로 존재
- 각 열린 파일마다 고유한 **정수 인덱스(fd)**를 가짐  
- 배열의 각 항목은 열린 파일 테이블의 엔트리를 가리킴

---

### 2️⃣ 열린 파일 테이블 (Open File Table)

- **시스템 전체**에서 열린 모든 파일들의 정보를 저장
- 각 엔트리는 다음을 포함:
  - 파일 포인터 (현재 위치)
  - 접근 권한 (읽기, 쓰기 등)
  - 참조 카운트
  - 동적 i-노드 테이블을 가리키는 포인터

---

### 3️⃣ 동적 i-노드 테이블 (Active i-node Table)

- **열린 파일들의 메타데이터**를 저장
- 디스크 상의 i-노드를 메모리로 가져와 관리
- 포함 정보:
  - 파일 타입
  - 파일 크기
  - 소유자, 권한, 시간 정보 등
  - 데이터 블록 포인터

---

## 상태 정보 : stat()
- 파일 하나당 하나의 i-노트가 있으며 i-노드 내에 파일에 대한 모든 상태 정보가 저장되어 있다.
```c
#include <sys/types.h>
 #include <sys/stat.h>
 int stat (const char *filename, struct stat *buf);
 int fstat (int fd, struct stat *buf);
 int lstat (const char *filename, struct stat *buf);
```

# 📁 파일 타입 (File Types)

리눅스/유닉스 파일 시스템에서는 여러 종류의 파일 타입을 지원합니다. 각 파일은 고유한 속성과 용도를 갖습니다.

| 파일 타입       | 설명 |
|----------------|------|
| **일반 파일** (`Regular File`) | 텍스트 파일 또는 이진 파일 등 실제 데이터를 포함한 파일 |
| **디렉터리 파일** (`Directory`) | 파일 이름과 해당 파일 정보를 포함하는 구조 (폴더 역할) |
| **문자 장치 파일** (`Character Device`) | 문자 단위로 데이터를 입출력하는 장치 (예: 키보드, 마우스) |
| **블록 장치 파일** (`Block Device`) | 블록 단위로 데이터를 입출력하는 장치 (예: 하드디스크, SSD) |
| **FIFO 파일** (`Named Pipe`) | 프로세스 간 통신(IPC)을 위한 이름 있는 파이프 |
| **소켓** (`Socket`) | 네트워크 통신에 사용되는 특수 파일 (예: TCP/IP 통신) |
| **심볼릭 링크** (`Symbolic Link`) | 다른 파일을 가리키는 포인터 역할을 하는 파일 (일종의 바로가기) |

# chmod(), fchmod()
```c
 #include <sys/stat.h>
 #include <sys/types.h>
 int chmod (const char *path, mode_t mode );
 int fchmod (int fd, mode_t mode );
```
- 파일의접근권한(access permission)을 변경한다

# 접근및수정시간변경: utime()
```c
 #include <sys/types.h>
 #include <utime.h>
 int utime (const char *filename, const struct utimbuf *times );
```
- 파일의최종접근시간과최종변경시간을조정한다.
- times가 NULL 이면, 현재시간으로 설정된다.
- 리턴값
 - 성공하면0, 실패하면-1
- UNIX 명령어 touch 참고

# 접근및수정시간변경: touch.c
```c
 #include <utime.h>
 #include <stdio.h>
 #include <stdlib.h>
 int main(int argc, char *argv[]) 
{
 if (argc < 2) {
 fprintf(stderr, "사용법:  touch file1 \n");
 exit(-1);
 }
 utime(argv[1], NULL); 
}
```

# 접근및수정시간복사: cptime.c
```c
#include <sys/types.h> 
#include <utime.h>       
#include <sys/stat.h> 
#include <stdio.h>      
int main(int argc, char *argv[]) 
{
 struct stat buf;        
struct utimbuf time;
 // 파일 상태저장을위한변수
if (argc < 3) {
 fprintf(stderr, "사용법: cptime file1 file2\n");
 exit(1);
 }
 if (stat(argv[1], &buf) <0) { // 상태 가져오기
perror("stat()");
 exit(-1);
 }
 time.actime = buf.st_atime;
 time.modtime = buf.st_mtime;
 if (utime(argv[2], &time))   // 접근, 수정 시간 복사
perror("utime");
 else exit(0);
 #include <sys/time.h>
 #include <stdlib.h>
 }
 ```
# 파일 소유자 변경 : chown()
```c
 #include <sys/types.h>
 #include <unistd.h>
 int chown (const char *path, uid_t owner, gid_t group );
 int fchown (int filedes, uid_t owner, gid_t group );
 int lchown (const char *path, uid_t owner, gid_t group );
```
- 파일의 user ID와 group ID를 변경한다.

# 디렉터리 생성
- mkdir() 시스템 호출
 - path가 나타내는 새로운디렉터리를만든다.
 - "." 와 ".." 파일은 자동적으로 만들어진다
```c
#include <sys/types.h>
 #include <sys/stat.h>
 int mkdir (const char *path, mode_t mode );
```
# 디렉터리 삭제
- rmdir() 시스템 호출
 -path가 나타내는 디렉터리가 비어있으면 삭제한다.
  ```c
  #include <unistd.h>
  int rmdir (const char *path);
 ```

