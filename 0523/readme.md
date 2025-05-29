# 🔅System programming week12🔅

# 프로세스생성: fork1.c

```c
 #include <stdio.h>
 #include <unistd.h>
 /* 자식 프로세스를 생성한다. */
 int main()
 { 
int pid;
 printf("[%d] 프로세스 시작 \n", getpid());
 pid = fork();
 printf("[%d] 프로세스 : 리턴값 %d\n", getpid(), pid);
 }
 $ fork1
 [15065] 프로세스 시작
 [15065] 프로세스 : 반환값 15066
 [15066] 프로세스 : 반환값 0
```
# 부모 프로세스와 자식 프로세스 구분
- fork() 호출 후에 리턴값이 다르므로 이 리턴값을 이용하여 부모 프로세스와 자식 프로세스를 구별하고 서로 다른 일을 하도록 할 수있다.
```c
  pid = fork();
  if ( pid == 0 ) 
  { 자식 프로세스의실행코드} 
  else
  { 부모 프로세스의실행코드}
```

# fork2.c
```c
 #include <stdlib.h>
 #include <stdio.h>
 /* 부모 프로세스가 자식프로세스를생성하고서로다른메시지를프린트*/
 int main() 
{
 int pid;
 pid = fork();
 if (pid ==0) {   // 자식 프로세스
printf("[Child] : Hello, world pid=%d\n“, getpid());
 }
 else {   // 부모 프로세스
printf("[Parent] : Hello, world pid=%d\n", getpid());
 }
 }
```

# 두 개의 자식 프로세스 생성: fork3.c
```c
 #include <stdlib.h>
 #include <stdio.h>
 /* 부모 프로세스가 두개의자식프로세스를생성한다. */
 int main() 
{
 int pid1, pid2;
 pid1 = fork();
 if (pid1 == 0) {
 printf("[Child 1] : Hello, world ! pid=%d\n", getpid());
 exit(0);
 }
 pid2 = fork();
 if (pid2 == 0) {
 printf("[Child 2] : Hello, world ! pid=%d\n", getpid());
 exit(0);
 }
 printf("[PARENT] : Hello, world ! pid=%d\n",getpid());
```

# 프로세스 기다리기 : wait()
- 자식 프로세스 중의 하나가 끝날 때까지 기다린다.
  - 끝난 자식 프로세스의 종료 코드가 status에 저장되며 끝난 자식 프로세스의 번호를 리턴한다.
```c
#include <sys/types.h>
 #include <sys/wait.h>
 pid_t wait(int *status);
 pid_t waitpid(pid_t pid, int *statloc, int options);
```

# 프로그램 실행 흐름: `fork()` 와 `exec()`

---

### 1. `fork()`
- 부모 프로세스가 새로운 자식 프로세스를 생성한다.
- **자식 프로세스는 부모와 동일한 코드와 데이터를 복제하여 실행을 시작한다.**
- 즉, `fork()` 호출 후 부모와 자식은 같은 위치에서 코드 실행이 계속된다.

---

### 2. `exec()` 시스템 호출
- 자식 프로세스는 `fork()`로 복제된 상태에서 **`exec()`를 사용하여 자신이 실행할 프로그램을 새 프로그램으로 완전히 대체**한다.
- `exec()` 호출 이후에는 기존 프로그램 코드는 없어지고, 새 프로그램 코드가 프로세스 메모리에 로드되어 실행된다.

---

### 일반적인 실행 순서
```plaintext
부모 프로세스: fork() → 자식 프로세스 생성
자식 프로세스: exec() → 새로운 프로그램 실행
```

# 프로세스(Process)

---

### 1. 프로세스란?
- **실행 중인 프로그램**을 의미한다.
- 즉, 단순히 저장된 프로그램 파일 자체는 프로세스가 아니다!

---

### 2. 프로그램 실행 시 필요한 요소
- 프로그램의 **코드(Code)**
- 프로그램의 **데이터(Data)**
- **스택(Stack)**: 함수 호출 시 사용하는 메모리 공간
- **힙(Heap)**: 동적 메모리 할당에 사용되는 공간
- **U-영역(User 영역)**: 프로세스 제어 관련 정보 등이 포함

---

### 3. 프로세스 이미지(Process Image)
- 메모리 내에 프로세스가 실행되기 위해 배치된 모든 영역의 집합
- 즉, 코드, 데이터, 스택, 힙 등이 포함된 프로세스의 메모리 구조(레이아웃)를 뜻함

---

### 핵심!
- **프로그램 자체는 프로세스가 아니다!**
- **프로세스는 실행 중인 상태의 프로그램이다!**
