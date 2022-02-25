# Thu Feb 24

# github

- [GitHub](https://github.com) 가입

  - [resposity 생성(remote)](https://github.com/new)

  - resposity 연결(remote-local)

    - 원격 저장소 등록

      `git remote add <이름> <주소>`

    - 원격 저장소 조회

      `git remote -v`

    - 원격 저장소 연결 끊기(삭제/ 저장소 삭제 아님)

      `git remote rm <이름>` |`git remote remove <이름>`

  - [README.md](/Users/yebin/Desktop/TIL)

- 원격 저장소 업로드

  **정확히 말하면, 파일을 업로드하는 게 아니라 commit을 업로드 하는 것!**

  - 로컬 저장소(git)

  ```bash
  git init
  #a.txt 생성
  touch a.txt
  #staging area에 a.txt 등장시키기
  git add a.txt
  #commit 올리기
  git commit -m "add a.txt"
  
  #3 공간에서 file이 어떻게 변했는지 확인
  git status
  
  #commit 내역 확인
  git log
  git log --oneline ##log 한 줄로 보기
  ```

  - 원격 저장소(github)

  ```bash
  #로컬 저장소에 있는 파일을 원격 저장소로 밀어내기
  git push <저장소 이름> <브랜치 이름>
  git push origin master
  ```

  **절대로 파일을 github에 드래그해서 업로드하지 말 것! **

  先 로컬 저장소 -> 後 원격 저장소 순서를 늘 지켜야 한다 

- `.gitignore`: 특정 파일 혹은 폴더에 대해 git이 버전 관리를 하지 못하도록 지정하는 것

  - [gitignore](https://www.toptal.com/developers/gitignore) 링크로 들어간 다음 사용하는 언어,OS 등  입력해 코드 생성 -> command + c -> vscode command + v -> 버전 관리 하지 못하게 할 파일명 입력(확장자 포함)

  - 어떤 정보를 지정하나?
    - 민감한 개인 정보가 담긴 파일(전화번호, 계좌번호 등)
    - OS에서 활용하는 파일
  - .gitignore 작성 시 주의 사항
    - 반드시 이름을 `.gitignore` 로 작성
    - `.gitignore` 파일은 `.git` 폴더와 동일한 위치에 생성
    - 제외하고 싶은 파일은 `git add` 전에 `.gitignore`에 작성

- clone, pull

  - clone(복제)

    - 원격 저장소 복제해 내 컴퓨터에 옮기기

      `git clone <원격 저장소 주소> <내 컴퓨터에 옮긴 원격 저장소 이름(선택)>`

    - gitclone으로 생성한 로컬 저장소는 `git init` 과 `git remote add` 이 이미 완료

  - git pull

    - 원격 저장소의 변경 사항을 가져와서 로컬 저장소 업데이트하는 명령어
    - 로컬 저장소와 원격 저장소 내용이 일치하면 git pull 해도 변화 없음

    `git pull <저장소 이름> <브랜치 이름>`