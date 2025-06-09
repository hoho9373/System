
# 우분투 리눅스 명령어 50개

---

### 1. `ls`  
- 설명: 현재 디렉터리의 파일과 폴더 목록을 보여줌  
- 사용법:  
  ```bash
  ls
  ls -l
  ls -a
  ```

---

### 2. `cd`  
- 설명: 디렉터리 이동  
- 사용법:  
  ```bash
  cd /home/user/Documents
  cd ..
  cd ~
  ```

---

### 3. `pwd`  
- 설명: 현재 작업 중인 디렉터리 경로 출력  
- 사용법:  
  ```bash
  pwd
  ```

---

### 4. `mkdir`  
- 설명: 새 디렉터리 생성  
- 사용법:  
  ```bash
  mkdir new_folder
  mkdir -p parent/child
  ```

---

### 5. `rmdir`  
- 설명: 빈 디렉터리 삭제  
- 사용법:  
  ```bash
  rmdir empty_folder
  ```

---

### 6. `rm`  
- 설명: 파일 또는 디렉터리 삭제  
- 사용법:  
  ```bash
  rm file.txt
  rm -r folder/
  rm -f file.txt
  ```

---

### 7. `cp`  
- 설명: 파일 또는 폴더 복사  
- 사용법:  
  ```bash
  cp file1.txt file2.txt
  cp -r folder1 folder2
  ```

---

### 8. `mv`  
- 설명: 파일 또는 폴더 이동 또는 이름 변경  
- 사용법:  
  ```bash
  mv oldname.txt newname.txt
  mv file.txt /home/user/Documents/
  ```

---

### 9. `touch`  
- 설명: 새 빈 파일 생성  
- 사용법:  
  ```bash
  touch newfile.txt
  ```

---

### 10. `cat`  
- 설명: 파일 내용 출력  
- 사용법:  
  ```bash
  cat file.txt
  ```

---

### 11. `less`  
- 설명: 파일 내용 페이지 단위로 보기  
- 사용법:  
  ```bash
  less file.txt
  ```

---

### 12. `head`  
- 설명: 파일의 앞부분 출력  
- 사용법:  
  ```bash
  head file.txt
  head -n 5 file.txt
  ```

---

### 13. `tail`  
- 설명: 파일의 마지막 부분 출력  
- 사용법:  
  ```bash
  tail file.txt
  tail -n 5 file.txt
  ```

---

### 14. `chmod`  
- 설명: 파일/디렉터리 권한 변경  
- 사용법:  
  ```bash
  chmod 755 script.sh
  chmod +x script.sh
  ```

---

### 15. `chown`  
- 설명: 소유자 및 그룹 변경  
- 사용법:  
  ```bash
  chown user:group file.txt
  ```

---

(생략된 나머지 명령어는 파일로 이어집니다)

---

### 16. `echo`  
- 설명: 문자열을 출력  
- 사용법:  
  ```bash
  echo "Hello, world!"
  ```

---

### 17. `man`  
- 설명: 명령어의 매뉴얼 페이지 보기  
- 사용법:  
  ```bash
  man ls
  ```

---

### 18. `df`  
- 설명: 디스크 사용량 확인  
- 사용법:  
  ```bash
  df -h
  ```

---

### 19. `du`  
- 설명: 파일/디렉터리의 용량 확인  
- 사용법:  
  ```bash
  du -sh *
  ```

---

### 20. `top`  
- 설명: 실시간 시스템 리소스 사용 현황 보기  
- 사용법:  
  ```bash
  top
  ```

---

### 21. `htop`  
- 설명: 향상된 top 명령어 (설치 필요)  
- 사용법:  
  ```bash
  htop
  ```

---

### 22. `ps`  
- 설명: 현재 실행 중인 프로세스 목록 보기  
- 사용법:  
  ```bash
  ps aux
  ```

---

### 23. `kill`  
- 설명: 프로세스 종료  
- 사용법:  
  ```bash
  kill 1234
  kill -9 1234
  ```

---

### 24. `grep`  
- 설명: 문자열 검색  
- 사용법:  
  ```bash
  grep "search" file.txt
  ```

---

### 25. `find`  
- 설명: 파일/디렉터리 검색  
- 사용법:  
  ```bash
  find . -name "*.txt"
  ```

---

### 26. `locate`  
- 설명: 빠르게 파일 찾기 (인덱스 기반)  
- 사용법:  
  ```bash
  locate file.txt
  ```

---

### 27. `nano`  
- 설명: 터미널 기반 텍스트 편집기  
- 사용법:  
  ```bash
  nano file.txt
  ```

---

### 28. `vim`  
- 설명: 고급 텍스트 편집기  
- 사용법:  
  ```bash
  vim file.txt
  ```

---

### 29. `wget`  
- 설명: 파일 다운로드  
- 사용법:  
  ```bash
  wget http://example.com/file.txt
  ```

---

### 30. `curl`  
- 설명: URL 요청 (API 호출 등)  
- 사용법:  
  ```bash
  curl http://example.com
  ```

---

### 31. `tar`  
- 설명: 아카이브 생성 및 압축 해제  
- 사용법:  
  ```bash
  tar -cvf archive.tar folder/
  tar -xvf archive.tar
  ```

---

### 32. `zip` / `unzip`  
- 설명: 파일 압축 및 해제  
- 사용법:  
  ```bash
  zip archive.zip file.txt
  unzip archive.zip
  ```

---

### 33. `ssh`  
- 설명: 원격 서버 접속  
- 사용법:  
  ```bash
  ssh user@hostname
  ```

---

### 34. `scp`  
- 설명: 원격 서버 간 파일 복사  
- 사용법:  
  ```bash
  scp file.txt user@host:/path/
  ```

---

### 35. `apt`  
- 설명: 패키지 설치 및 관리  
- 사용법:  
  ```bash
  sudo apt update
  sudo apt install package
  ```

---

### 36. `dpkg`  
- 설명: 개별 패키지 파일 설치  
- 사용법:  
  ```bash
  sudo dpkg -i package.deb
  ```

---

### 37. `service`  
- 설명: 시스템 서비스 시작/중지  
- 사용법:  
  ```bash
  sudo service apache2 start
  ```

---

### 38. `systemctl`  
- 설명: 시스템 서비스 관리 (systemd)  
- 사용법:  
  ```bash
  sudo systemctl status nginx
  ```

---

### 39. `alias`  
- 설명: 명령어 단축 별칭 지정  
- 사용법:  
  ```bash
  alias ll='ls -la'
  ```

---

### 40. `uname`  
- 설명: 시스템 정보 출력  
- 사용법:  
  ```bash
  uname -a
  ```

---

### 41. `whoami`  
- 설명: 현재 사용자 이름 출력  
- 사용법:  
  ```bash
  whoami
  ```

---

### 42. `id`  
- 설명: 사용자 ID 및 그룹 정보 보기  
- 사용법:  
  ```bash
  id
  ```

---

### 43. `history`  
- 설명: 이전 명령어 기록 보기  
- 사용법:  
  ```bash
  history
  ```

---

### 44. `clear`  
- 설명: 터미널 화면 지우기  
- 사용법:  
  ```bash
  clear
  ```

---

### 45. `env`  
- 설명: 환경 변수 출력  
- 사용법:  
  ```bash
  env
  ```

---

### 46. `export`  
- 설명: 환경 변수 설정  
- 사용법:  
  ```bash
  export VAR=value
  ```

---

### 47. `xargs`  
- 설명: 인수를 표준 입력에서 받아 실행  
- 사용법:  
  ```bash
  find . -name "*.txt" | xargs rm
  ```

---

### 48. `cron` (`crontab`)  
- 설명: 주기적인 작업 예약  
- 사용법:  
  ```bash
  crontab -e
  ```

---

### 49. `date`  
- 설명: 현재 날짜 및 시간 표시  
- 사용법:  
  ```bash
  date
  ```

---

### 50. `uptime`  
- 설명: 시스템 부팅 이후 경과 시간  
- 사용법:  
  ```bash
  uptime
  ```




