# 🐧 리눅스 명령어 50선 & 사용법 정리

---

## 📁 파일 및 디렉토리 관련

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `ls` | 파일 목록 보기 | `ls -l`, `ls -a` |
| `cd` | 디렉토리 이동 | `cd /home/user`, `cd ..` |
| `pwd` | 현재 디렉토리 경로 출력 | `pwd` |
| `mkdir` | 새 디렉토리 생성 | `mkdir mydir` |
| `rmdir` | 빈 디렉토리 삭제 | `rmdir olddir` |
| `rm` | 파일/디렉토리 삭제 | `rm file.txt`, `rm -r folder` |
| `touch` | 빈 파일 생성 | `touch hello.txt` |
| `cp` | 파일 복사 | `cp a.txt b.txt`, `cp -r dir1 dir2` |
| `mv` | 파일 이동/이름 변경 | `mv a.txt b.txt`, `mv file.txt /home/user/` |
| `find` | 파일 검색 | `find . -name "*.txt"` |

---

## 📄 파일 내용 확인/편집

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `cat` | 파일 내용 출력 | `cat file.txt` |
| `more` | 페이지 단위 출력 | `more file.txt` |
| `less` | 스크롤 가능한 출력 | `less file.txt` |
| `head` | 앞부분 출력 | `head -n 10 file.txt` |
| `tail` | 뒷부분 출력 | `tail -n 10 file.txt` |
| `tail -f` | 실시간 로그 보기 | `tail -f /var/log/syslog` |
| `nano` | 간단한 편집기 | `nano file.txt` |
| `vim` | 고급 편집기 | `vim file.txt` |
| `echo` | 출력 또는 파일에 쓰기 | `echo "hello"`<br>`echo "text" > file.txt` |
| `tee` | 출력 + 파일 저장 | `echo "log" | tee logfile.txt` |

---

## 🔐 권한 및 소유자

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `chmod` | 권한 변경 | `chmod 755 script.sh` |
| `chown` | 소유자 변경 | `chown user:user file.txt` |
| `umask` | 기본 권한 설정 | `umask`, `umask 022` |

---

## 📦 압축/해제

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `tar` | 압축/해제 | `tar -czvf archive.tar.gz dir/`<br>`tar -xzvf archive.tar.gz` |
| `zip` | 압축 | `zip files.zip file1 file2` |
| `unzip` | 압축 해제 | `unzip files.zip` |

---

## 📡 네트워크 관련

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `ping` | 연결 확인 | `ping google.com` |
| `curl` | 웹 요청 | `curl https://example.com` |
| `wget` | 파일 다운로드 | `wget https://example.com/file.zip` |
| `ifconfig` | 네트워크 설정 확인 | `ifconfig` |
| `netstat` | 포트 상태 보기 | `netstat -tulnp` |

---

## 👨‍💻 프로세스 및 시스템

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `top` | 실시간 프로세스 보기 | `top` |
| `ps` | 프로세스 정보 | `ps aux`, `ps -ef` |
| `kill` | PID로 프로세스 종료 | `kill 1234` |
| `killall` | 이름으로 종료 | `killall firefox` |
| `htop` | top의 개선판 | `htop` |
| `uptime` | 시스템 가동 시간 | `uptime` |
| `df` | 디스크 사용량 | `df -h` |
| `du` | 디렉토리 용량 | `du -sh *` |
| `free` | 메모리 사용량 | `free -h` |

---

## 🔁 입출력 및 기타 유틸

| 명령어 | 설명 | 사용 예시 |
|--------|------|-----------|
| `history` | 명령 기록 | `history` |
| `alias` | 별칭 만들기 | `alias ll='ls -alF'` |
| `date` | 날짜/시간 출력 | `date`, `date "+%Y-%m-%d"` |
| `cal` | 달력 출력 | `cal`, `cal 2025` |
| `whoami` | 현재 사용자 | `whoami` |
| `hostname` | 호스트 이름 보기 | `hostname` |
| `man` | 매뉴얼 보기 | `man ls`, `man grep` |
| `grep` | 문자열 검색 | `grep "text" file.txt` |
| `sort` | 정렬 | `sort file.txt` |
| `cut` | 텍스트 자르기 | `cut -d':' -f1 /etc/passwd` |
| `awk` | 텍스트 필터링 | `awk '{print $1}' file.txt` |

---


