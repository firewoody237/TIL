# Git 이란

**VCS(Version Control System)** : 프로그램의 시간&차원을 관리

- 시간 : 개발된 버전을 관리
- 차원 : 해당코드로 실험적인 테스트를 진행해 봄
  <br><br><br>

# Git 설치

```git
git version
//git 버전 확인

brew install git
//git 설치 및 업데이트

git config --global core.autocrlf input
//윈도우와 맥의 엔터 차이 해결
```

<br><br><br>

# Git 설정

- 개발 이력관리를 위한 본인정보 입력(Github과는 별개)

```git
git config --global user.name "(UserName)"
git config --global user.email "(MainAddress)"
//조회시에는 "()" 부분만 없으면 됨

git config --global init.defaultBranch main
//기본브런치를 master가 아닌 main으로 변경
```

<br><br><br>

# Git 프로젝트 세팅

1. 프로젝트 폴더 생성
2. 하단 코드 입력

```git
git init
//생성되는 .git 폴더를 지울경우 형상관리가 불가능
```

3. 소스추가 및 개발 진행
4. 하기 소스로 상태 확인

```git
git status
//현재 작업중인 것들 확인 가능
```

<br><br><br>

# Git 필요 없는 것들

1. 자동으로 생성되는 파일들(빌드 결과물, 라이브러리)
2. 보안상 민감한 정보

## .gitignore 형식

```git
# 이렇게 #를 사용해서 주석

# 모든 file.c
file.c

# 최상위 폴더의 file.c
/file.c

# 모든 .c 확장자 파일
*.c

# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c

# logs란 이름의 파일 또는 폴더와 그 내용들
logs

# logs란 이름의 폴더와 그 내용들
logs/

# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c

# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log
```

<br><br><br>

# Git 파일 등록

```git
git add aFileName
git add .

git commit
git commit -m "Message"
git commit -am "Message"
//Untracked(추가)된 파일이 없을때만 가능. commit 전 add수행

git log

git diff
//j, k, q를 사용해서 조작
```

<br><br><br>

# 시간 이동

- Reset : 기존 수정내역을 지우고 이전 소스로 돌아감
- Revert : 과거내역을 제외한 특정 히스토리만 편집이 가능(협업 시)

```git
//git log를 통해 해쉬값을 가져와서 사용

git reset --hard afda66372e35b611daa88033aae79e250bf0a073
git reset --hard
//바로 전 단계로 이동

git revert 9fe260a043a989b5b731c751afb46716ad853fd4

git revert --no-commit fe3e0afeb3b97f21c5d5f1e46769a48608536b39
//커밋하지 않은 채 revert
//다른 커밋까지 하고 싶을 때
```

<br><br><br>

# 차원 이동

```git
git branch branchnName
git branch //브랜치 확인

git switch branchName

git switch -c branchName
//생성과 이동 동시에

git branch -d branchName
//브랜치 삭제
//커밋할 내용을 강제무시해야할 경우 -d 대신 -D 사용

git branch -m beforeName toName
//beforeName에서 toName으로 브랜치명 변경
```

<br><br><br>

# Branch 합병

- merge : 두 소스를 합병(브랜치 흔적을 남김)
  - reset 사용 가능
- rebase : 두 브랜치를 하나의 브랜치로

```git
git merge 합칠브랜치(other)

git rebase 합쳐질브랜치(main)
git merge 합칠브랜치(other)
//main브랜치를 merge로 가장 위로 끌어올림
```

<br><br><br>

# Conflict

- rebase는 commit하나 마다 모두 따로 관리해주어야 한다.

```git
git merge --abort
//merge 취소

git rebase --abort
//rebase 취소
```

- conflict 해결 후 add, commit을 진행

```git
//rebase가 여러개인 경우 continue로 전부 잡아줘야 함
git rebase --continue
```

<br><br><br>

# Github

- Commit단위로 관리하여, 여러명이 동시에 협업하기 위함
- 협업하려면 Repository의 [Settings-Collaborators-AddPeople]

### 내 소스를 Github에 올릴 때

```git
git remote add origin (원격 저장소 주소)
//로컬의 Git 저장소에 원격 저장소로의 연결 추가

git branch -M main
//GitHub 권장 - 기본 브랜치명을 main으로

git push -u origin main
//로컬 저장소의 커밋 내역들 원격으로 push
```

### Github에서 소스를 가져올 때

```git
git clone repository-address
```

### 원격으로 커밋 밀어올리기

```git
git push
```

### 원격에서 커밋 당겨오기

```git
git pull
```

### 원격 및 로컬 모두 수정이 있을 때

- 먼저 pull을 진행한 후, push해야 함

```git
git pull --no-rebase
//merge 방식. local과 remote의 분기를 하나로 합쳐 줌

git pull --rebase
//rebase 방식. 원격을 먼저 붙이고, 잘라서 내것을 붙임

git push --force
//강제로 덮어씌우기
```

### 원격 branch 조정

```git
//브랜치 생성 후
git push -u origin from-local

git branch --all
//원격 포함 모든 브랜치 확인

---------------------------------
//원격 branch가져오기
git fetch

git switch -t origin/from-remote

git push (원격 이름) --delete (원격의 브랜치명)
//원격의 branch 삭제
```

## <br><br><br>

# Git의 강점

1. snapshot을 사용
   1. 최종상태 그대로 저장
   2. 델타방식은 commit될 때마다 히스토리를 따라가야 함
2. 중앙집중식이 아닌 분산버전관리
   1. 상태까지 가져오므로 네트워크가 끊어져도 독립적으로 사용 가능

<br><br><br>

# Git의 3가지 공간

1. Respository : Commit들이 저장되는 공간
2. Working Directory : 수정사항이 만들어지면 저장
   1. Untracked : 새로 추가된 파일
   2. Tracked : 기존 파일에서 수정된 것
3. Staging Area : Add 했을 때 공간

Working Directory >add> Staging Area >commit> Repository

```git
git rm tigers.yaml
//tigers.yaml을 지우고, add까지 한 Staging Area 상태가 됨

git mv tigers.yaml zzamtigers.yaml
//tigers.yaml의 파일이름을 zzamtigers.yaml으로 바꾸고 Staging Area상태가 됨

git restore --staged pumas.yaml
//pumas.yaml만 staging area에서 제거. working directory로 가게 됨 (ex. pumas만 다음번에 commit할 때 등에 사용)

git restore pumas.yaml
//working directory에서도 제거.

git reset
//--hard : 내역 자체를 지워버림
//--mixed : working directory에는 남겨 둠
//--soft : repository에서만 제거하고 staging area에 남겨 둠
```

<br><br><br>

# HEAD

head : 속한 브런치에 가장 최신 커밋

```git
git checkout HEAD^
//^대신 ~로도 대체 가능
//^는 여러번 쓸 수 있음
//^의 갯수 만큼 앞 commit으로 이동

git checkout -
//하나만큼 뒷 커밋으로 이동

git reset --hard HEAD~2
//현재 커밋에서 2개만큼 앞 커밋으로 reset
```

<br><br><br>

# Fetch와 Pull

- fetch: 원격 저장소의 최신 커밋을 로컬로 가져오기만 함
- pull: 원격 저장소의 최신 커밋을 로컬로 가져와 merge 또는 rebase

fetch로 원격 저장소의 변화를 우선 가져오고, pull로 가져온다.
단, pull에는 fetch도 포함되어있다.

---

<br><br><br>

# Git 보다 잘 사용하기

## Git help

```git
git (명령어) -h
git help
git help (명령어) //웹사이트를 통해 열어 봄
```

[Git Documentation](https://git-scm.com/docs)
[Git Book](https://git-scm.com/book/ko/v2)

## Git 각종 설정

- --global은 전역으로 등록이 됨

```git
//현재 이 프로젝트의 user.name만 text로 사용
git config user.name text


//설정들 보기
git config --list
git config --global --list

//vi editor에서 설정파일 수정
git config -e

//VS Code에서 설정파일 수정
git config --global core.editor "code --wait" //세팅 후
git config -e
```

- 여러 유용한 설정

```git
//줄바꿈 호환문제 해결
git config --global core.autocrlf (윈도우: true / 맥: input)

//pull전략을 기본적으로 rebase로 하고 싶다면 true, merge로 하고싶다면 false
git config pull.rebase false

//기본 브랜치명 변경
git config --global init.defaultBranch main

//push시 로컬과 동일한 브랜치명으로
git config --global push.default current

//단축기 설정
git config --global alias.(단축키) "명령어"
//예시
git config --global alias.cam "commit -am"
```

## <br><br><br>

# 프로답게 커밋 관리하기

- 커밋 메시지는 누가보더라도 내용을 알 수 있도록 적어야 한다.
- 한 단위 작업은 하나의 커밋에 하는 것이 좋다.

## Git 커밋 컨벤션

```git
type: subject

body (optional)
...
...

footer (optional)
```

<예시>

```git
feat: 압축파일 미리보기 기능 추가

사용자의 편의를 위해 압출을 풀기 전에
다음과 같이 압축파일 미리보기를 할 수 있도록 함

Closes #125
```

1. feat : 새로운 기능 추가
2. fix : 버그 수정
3. docs : 문서 수정
4. style : 공백, 세미콜론 등 스타일 수정
5. refactor : 코드 리팩토링
6. perf : 성능 개선
7. test : 테스트 추가
8. chore : 빌드 과정 또는 보조 기능(문서 생성기능 등 수정)

Subject : 커밋의 작업 내용 간단히 설명

Body : 길게 설명할 필요가 있을 시 사용

Footer : Breaking Point가 있을 때, 특정 이슈에 대한 해결 작업일 때

---

## 세심하게 스테이징, 커밋하기

```git
git add -p
//하나씩 순차적으로 진행

git commit -v
//커밋하는 변경사항을 다시한번 확인
```

---

## 커밋하기 애매한 변화 stash하기

- 하던 수정들을 다른 공간에 치워 둠

```git
git stash
//소스 변경 잠시 치워두기

git stash pop
//stash 한 것 가져오기

git stash -p
//순차적으로 stash

git stash -m 'Message'

git stash list

git stash apply StashName
git stash drop StashName

git stash pop //apply와 drop을 한번에

git stash branch StashBranchName //브랜치를 생성하고 거기에 Stash Pop
git stash clear //stash 비우기
```

---

## 커밋 수정하기

### 커밋 메시지 수정하기

```git
git commit --amend //커밋 메시지 수정

git commit --amend -m 'New Commit Message' //한줄로 이전 커밋 메시지 수정
```

### 커밋 내용 수정하기

```git
git rebase -i 커밋위치
//과거 내역을 수정할 때, 해당 위치부터 수정해야 하기 때문에 rebase사용

/*
pick을 다음 용도에 맞게 변경해서 사용
p : pick : 커밋 그대로 두기
r : reword : 커밋 메시지 변경
e : edit : 수정을 위해 정지
d : drop : 커밋 삭제
s : squash : 이전 커밋에 합치기
*/

//전부 변경한 후 다음 진행
git rebase --continue
```

## <br><br><br>

# 취소와 되돌리기 보다 깊이 알기

## 관리되지 않는 파일들 삭제하기

git clean
-n : 삭제될 파일들 보여주기
-i : 인터렉티브 모드 시작
-d : 폴더 포함
-f : 강제로 바로 지워버리기
-x : gitignore에 등록된 파일들도 삭제

## 커밋하지 않은 변경사항 되돌리기

git restore (fileName)

- 로컬 저장소의 변동들을 삭제

git restore --staged (fileName)

- stage된 변동들도 삭제

git restore --source=HEAD~~ (fileName)
git restore --source=(커밋 로그 값) (fileName)

- 파일을 특정 커밋의 저장된 상태로 복구

## reset했어도 희망은 있다.

git reflog 으로 특정 시점을 찾고
git reset --hard (특정시점값)으로 원복
<br><br><br>

---

# 태그

## 커밋에 태그 달기

- 특정 시점을 키워드로 저장하고 싶을 때
- 커밋에 버전 정보를 붙일 때
  [Sematic Version](https://semver.org/lang/ko/)

* 태그 종류
  - lightweight : 오직 태그만
  - annotated : 작성자 정보와 날짜, 메시지, GPG 서명 포함 등

```git
//lightweight
//마지막 태그에 커밋
git tag v2.0.0
//태그 확인
git tag
//특정 태그 커밋 확인
git show v2.0.0
//태그 삭제
git tag -d v2.0.0

//annotated
git tag -a v2.0.0
git tag v2.0.0 -m '버전 설명'
```

```git
//원하는 커밋에 넣기
git tag (버전명) (커밋해시) -m (메시지)

//태그 필터링하여 검색
git tag -l 'v1.*'

//해당 태그로 이동
git checkout v1.0.0
```

## 원격의 태그와 릴리즈

```git
//특정 태그 원격에 올리기
git push (원격명) (태그명)
git push origin v1.0.0

//특정 태그 원격에서 삭제
git push --delete (원격명) (태그명)

//로컬의 모든 태그 원격에 올리기
git push --tags
```

- 릴리즈 배포 시 github 내 해당 태그에서 'Create Release' 사용
  <br><br><br>

---

# Branch 보다 깊이 알기

1. Fastforard
   1. merge 기록이 남지 않을 수 있음
      1. git merge (branch)
   2. 기록이 남도록 fast-forward하지 않음
      1. git merge --no-ff (branch)
2. 3-way merge
   1. 두 브랜치에 모두 변경사항이 있을경우
   2. 조상 커밋과 두 브랜치를 비교하기 때문에 3-way merge

## 다른 브랜치에서 원하는 커밋만 복제해서 가져오기(Cherry-Pick)

```git
git cherry-pick (해시값)
```

## 다른 가지의 잔가지만 가져오기

```git
git rebase --onto (도착 브랜치) (출발 브랜치) (이동할 브랜치)
//[도착 브랜치]로, [출발 브랜치]에 속해있는, [이동할 브랜치]만 가져온다.
```

## 여러 가지의 마디(커밋)들 묶어서 가져오기

```git
git merge --squash (합칠 브랜치)
```

## 협업을 위한 브랜치 사용법 - Gitflow

- 협업을 위한 브랜치 전략
- [참조 페이지](https://nvie.com/posts/a-successful-git-branching-model/)

* main : 제품 출시/배포
* develop : 다음 출시/배포를 위한 개발진행
* release : 출시/배포 전 테스트 진행(QA)
* feature : 기능 개발
* hotfix : 긴급한 버그 수정

# 분석하고 디버깅하기

## log 더 자세히 알아보기

```git
//각 커밋마다 변경내용 함께 보기
git log -p

//이전 커밋 3개만 보기
git log -3

//통계와 함께 보기
git log --stat
git log --shortstat

//log 한줄로 보기
git log --oneline
git log --pretty=oneline --abbrev=commit

//변경사항 내 단어 검색
git log -S (검색어)

//커밋 메시지 검색
git log --grep (검색어)

//그래프 로그로 보기
git log --all --decorate --oneline --graph

//얄코 커스터마이징 로그 pretty format
git log --graph --all --pretty=format:'%C(yellow) %h  %C(reset)%C(blue)%ad%C(reset) : %C(white)%s %C(bold green)-- %an%C(reset) %C(bold red)%d%C(reset)' --date=short
```

[포맷 로그 커스터마이징](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0#pretty_format)

## 차이 살펴보기

```git
git diff
//주로 워킹 디렉토리의 변경사항을 확인하는데 사용

//파일 명만 확인
git diff --name-only

//스테이지에 변경사항 확인
git diff --staged
git diff --cached
git diff --staged --name-only

//두 커밋 비교
git diff (커밋1) (커밋2)
//태그나 HEAD~, HEAD~7도 사용 가능

//브랜치간 비교
git diff (브랜치1) (브랜치2)
```

## 누가 작성했는지 알아내기

```git
git blame (파일명)

//특정 라인 검색
git blame -L (시작라인),(끝라인) (파일명)
git blame -L 10,12 text.txt
git blame -L 10,+3 text.txt
```

- VS코드에서 gitlens 플러그인 유용

## 오류난곳 찾기

- 어느곳부터 오류가 났는지 찾아야 함

```git
git bisect //이진탐색 사용

git bisect start //이진탐색 시작
git bisect good/bad //에러가 없으면 good, 에러가 있으면 bad입력
git checkout (해쉬) //이러식으로 원하는 곳으로 이동도 가능
git bisect reset //찾고 내서 끝낼 때
```

## <br><br><br>

# git의 기타 기능들

## Git Hooks

- 이벤트마다 자동으로 실행될 스크립트를 지정(자동화)
- .git 폴더 내 .hooks 폴더
- gitmoji 같은것에 사용

## Git Submodules

- 프로젝트안에 또다른 프로젝트를 관리해야 할 때

```git
git submodule add (서브모듈 주소)
```

- 서브 모듈을 등록하면 현재 프로젝트에 대해서만 git작업이 가능하다.
- 서브 모듈 자체에 관여하진 않지만, 서브모듈의 커밋이 발생하는 것은 관여함

- main 프로젝트를 clone하는 경우, 처음에는 submodule들이 가져와져 있지 않다.
- 그럴 땐 git submodule init
- 특정 서브모듈만 원할 때 git submodule init "서브모듈명"
- 그 후 git submodule update

- 수정 사항 가져오기 git submodule update --remote

- 서브모듈 안에 또 서브모듈이 있을 때 git submodule update --remote --recursive

# GitHub 잘 활용하기

## 프로젝트와 폴더에 대한 문서

- README.md

[마크다운 문법](markdownguide.org)
[Github 제공 가이드](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

## 풀 리퀘스트와 이슈

### 풀 리퀘스트

Settings의 Manage access로 사용자 추가가 가능
풀 리퀘스트를 통해 소스의 변경을 검토받고, 동의하에 적용이 가능함

- GitHub 레포지토리 페이지에서 Compare & Pull Request 버튼
- 잘 진행되면 merge 진행

### 이슈

Issues

- 라벨 : 내가 필요한 라벨을 붙이거나, 만들어서 사용할 수 있음
- 마일스톤 : 이슈들의 묶음

* 관련 개발 착수 (브랜치명이나 커밋 footer에 이슈 번호 반영)
* 해결 뒤 Close Issue

## 오픈 소스에 참여하기

Fork로 프로젝트를 복사해 옴
Fork에서 수정해서 Pull Request를 진행하여 요청

## Github에 블로그 만들기

Github 페이지 사용해서 블로그 작성
<br><br><br>

---

# GitHub 제대로 활용하기

## SSH로 접속하기

- 공개키 암호화 방식 활용
- username 과 토큰 사용할 필요 없음
- 컴퓨터 자체에 키 저장
  Account settings > SSH and GPG keys에 컴퓨터에 있는 SSH키를 등록하여 사용
- ssh키를 컴퓨터에 생성해서 사용

## GPG로 커밋에 사인하기

커밋에 Verified 처럼 인증을 함
컴퓨터에 GPG Tool으로 GPG Key를 생성하여 Git에 등록하여 사용

## GitHub Actions - CI/CD(지속적 통합과 배포)

- 웹사이트에서 Actions 탭
- 자동화 할 것을 고르고(혹은 만들고 사용)

## GitHub 추가 팁

### OctoTree

파일 탐색기 처럼 볼 수 있음(Chrome Extension)

### GitHub CLI

좀더 쉬운 명령어로 사용 가능
[GitHub CLI](cli.github.com)
