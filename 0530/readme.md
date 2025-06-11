# 🔅System programming week13🔅

# grep 명령어

## grep 개념
- 파일 안에서 특정 문자열을 빠르게 찾는 명령어

## grep 구조
grep [옵션] '찾을 문자열' 파일명

- 예제 1 : 이름이 Kim인 사람 찾기
```bash
grep "Kim" students.txt
```

![image](https://github.com/user-attachments/assets/bf720a52-db53-4ac5-a368-593b29d54e61)


- 예제 2 : 학번이 2020으로 시작하는 줄 찾기
```bash
grep "^2020" students.txt # 파일 형태에 따라 위치 조절
```

![image](https://github.com/user-attachments/assets/ee9464c9-de58-4963-b8c2-acda8bfbf07c)

---
+ 파일 내용에 따른 다양한 활용 팁
1. 파일 내 검색과 함께 통계 내기
```bash
grep -c "ERROR" system.log  # 에러 개수 세기
grep -n "ERROR" system.log  # 에러가 몇 번째 줄에 있는지
```
![image](https://github.com/user-attachments/assets/999beeae-e0a2-428d-b90b-2fbf5b93e362)


2. 디렉토리 전체 검색
```bash
grep -r "TODO" ./project     # 프로젝트 전체에서 TODO 찾기
```
![image](https://github.com/user-attachments/assets/14fb9b43-0c46-4f6b-ab80-e21bc4239283)

3. 특정 확장자만 검색
```bash
grep "main()" *.c            # 모든 C파일에서 main() 찾기
```
![image](https://github.com/user-attachments/assets/fa088447-4bc9-4d01-bce7-5d6460136f5a)

## 자주 쓰는 grep 옵션

![image](https://github.com/user-attachments/assets/4aa67ea9-0948-4aec-bc8f-8376eb498e59)

## grep 관련 변형 명령어

![image](https://github.com/user-attachments/assets/9a6e5523-b641-4575-9ddb-3605729ee945)

## 정규 표현식

![image](https://github.com/user-attachments/assets/295b0461-ccb7-42ac-9d85-7f0ee09b1d90)
