# Fri Feb 25

# branch

1. git branch

```bash
#브랜치
git branch

#브랜치 생성
git branch <신규 브랜치 이름>

#브랜치 삭제
git branch -d <삭제할 브랜치 이름>
git branch -D <삭제할 브랜치 이름> #강제삭제 옵션
```

2. git switch

- 다른 브랜치로 이동하는 명령어

```bash
#브랜치 이동
git switch

#브랜치 생성 후 이동
git switch -c
```

3. git merge

- 분기된 브랜치들을 합치는 명령어

```bash
#주의! 내가 기준으로 가지고 있을 브랜치에 위치
git switch master
git merge <브랜치명> #실습에서는 water
```



+)git diff

- 커밋들 사이 변경사항의 차이를 보여주는 명령어

```bash
#두 버전의 차이점을 볼 때
#git log --oneline 통해 확인한 해쉬값들 이용
git diff <hash1> <hash2>

git diff 4ae8e43 0ede971

diff --git a/README.md b/README.md
index b76f398..c7da8b6 100644
--- a/README.md
+++ b/README.md
@@ -1,3 +1,2 @@
 # 놀이공원 어트랙션
-- 바이킹
-- 아틀란티스
\ No newline at end of file
+- 바이킹
\ No newline at end of file
```



# git workflow

1. 원격 저장소 소유권이 있는 경우(Shared Repository Model)
2. 원격 저장소 소유권이 없는 경우(Full & Fork)

- 개념
  - 자신의 소유가 아닌 원격 저장소인 경우 사용
  - 원본 원격 저장소를 내 원격 저장소에 `복제`한다( `fork`)
  - 기능 완성 후 `push` 는 복제한 내 원격 저장소에 진행
  - `Pull Request` 를 통해 원본 원격 저장소에 반영될 수 있도록 한다

- 작업 흐름

  1. 나한테 소유권이 없는 원격 저장소를 fork 해 내 원격 저장소로 복제한다
  2. Fork 해 복제한 내 원격 저장소를 로컬 저장소에 clone해 받아준다
  3. 로컬 저장소와 원본 원격 저장소 연결한다 -> 동기화하기 위해
  4. 작업할 기능을 수행할 브랜치 생성하고 기능 구현
  5. 기능 구현이 끝나면 복제 원격 저장소(origin)에 브랜치 push
  6. 복제 원격 저장소에 master 와 브랜치 저장
  7. Pull request 해 origin 브랜치를 원본 원격 저장소 master에 반영해달라고 요청한다
  8. 원본 원격 저장소 master에 브랜치가 반영되면 복제 원격 저장소(origin) 브랜치 삭제하고 so master 브랜치로 이동
  9. 병합으로 인해 변경된 원본 원격 저장소 master 내용을 로컬에 받아오고, 기존 로컬 브랜치 삭제
  10. 한 사이클 종료

  ```markdown
  **순서**
  
  `fork`→`clone`→브랜치 생성→ `add` → `commit` → 브랜치 `push` → `pull&request` 보내기
  ```

  
