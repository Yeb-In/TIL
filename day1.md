# Wed Feb 23

# CLI

- CLI vs. GUI

  - GUI(Graphic User Interface): 그래픽을 통해 사용자와 컴퓨터가 상호 작용하는 방식
    - 일반적으로 우리가 사용하는 방식이다

  - CLI(Command Line Interface):터미널을 통해 사용자와 컴퓨터가 상호작용하는 방식
    - Terminal, command 창에서 사용하는 방식

- 커맨드라인 명령어

  ```bash
  #디렉토리 생성
  mkdir
  #디렉토리 이동
  cd
  #파일 생성
  touch
  #디렉토리 안 리스트를 확인
  ls
  #제거
  rm
  ##-r 옵션: 재귀적
  ##-rf 옵션: 강제 삭제
  #이동/이름변경
  mv
  #현재의 경로를 보여줌
  pwd
  #화면 깨끗이/스크롤 올리기
  clear
  ctrl + l
  ```

---

# GIT

- git 3공간

  - 분장실, 무대, 사진 촬영본
  - Working directory(WD), staging area(SA), commits

- git 설치

  - Mac OS 경우 git이 이미 Terminal에 내장되어 있다.

    `command + spacebar (spotlight) -> terminal 입력`

- git 명령어 학습

  - `git init`
    - 맨 처음 1회,절대 홈 폴더에서 하지 않는다
    - git init 한 폴더의 하위 폴더에서 절대 git init 하지 않는다
  - `git add`
  - `git status`: 파일 상태를 확인
  - `git commit -m "메시지"`
  - `git command`
  - `git log`: 커밋 내역 확인
    - --oneline: 한 줄 출력
  
- git 초기 설정

  - git config

  ```bash
  git config --global user.name "유저명"
  git config --global user.email"유저 이메일" #깃허브에서 사용
  ```

---

# Mark down

- 마크다운과 마크업
  - 마크업: html -> 개발자 도구로 확인(태그)
  - 마크다운: 경량화된 마크업 언어
- 마크다운 역할
  - 글자 크기를 위해 부여된 역할에서 벗어나지 말 것

- Typora 설치(최근 버전은 유료이므로 업데이트 X)

  - [이전버전 다운로드](https://typora.io/dev_release.html)

- 마크다운 문법

  1. 제목: #~######

  2. 목록:  -,*,+ 들여쓰기와 내어쓰기(`tab`,`shift`,+`tab`)

  3. 강조

     - *기울임*: `*글자*`
     - **굵게**: `**글자**`
     - ***기울이고 굵게*** : `***글자***`

  4. 코드

     - 인라인: 

  5. 링크: [표시하고 싶은 텍스트] (연결하고 싶은 url)

  6. 이미지: ![이미지 이름] (연결하고 싶은 이미지)

  7. 구분선: `---`,`***`,`___`

  8. 표: option + command + T

     |      |      |      |
     | ---- | ---- | ---- |
     |      |      |      |
     |      |      |      |
     |      |      |      |

     

  9. 인용 : > + 인용문구

     > 인용
     >
     > > 중첩1
     > >
     > > > 중첩2

- 마크업 파일 생성

  [README.md](https://github.com/Yeb-In/Yeb-In)

  ```marks
  - 👋 Hi, I’m @Yeb-In
  - 👀 I’m interested in **Marketing**, **Data Journalism** and **PM** . 
  - 🌱 I’m currently learning **PYTHON** and **TEXT MINING**
  - 💞️ I’m looking to collaborate on projects which makes our life better!
  - 📫 Here's my [LinkedIN](https://www.linkedin.com/in/ww0n/)
  
  <!---
  Yeb-In/Yeb-In is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
  You can click the Preview link to take a look at your changes.
  --->
  