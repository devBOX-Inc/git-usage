# git-usage
깃 사용에 관한 기본 사용 방법 및 정책입니다.  
깃 히스토리를 잘 남기는 것은 코딩의 역사를 쓰는 것과도 같습니다.  
처음에는 어렵더라도 숙지하면서 천천히 익히다 보면 금새 손에 익힐 수 있을 것입니다. 

## 브랜치
- dev (default) : 개발 진행중인 브랜치, PR등 기본 대상
- main : 릴리즈 완료된 배포 가능한 브랜치
    - 커밋, 머지등 직접 작업하지 않음
    - 릴리즈 사용자만 접근하여 작업
- 그외 : 작업 단위로 생성후 삭제 (feature, release, hotfix)

**NOTE:** dev, main은 레포 전반에 항상 존재, 그외에 필요시 사용후 삭제


## 작업 수행 절차
다음과 같이 업무에 따라 작업 수행

### 일반적인 기능 구현 및 버그 픽스
1. (optional) 하고자 하는 작업에 대한 이슈 등록 또는 이슈 확인

2. dev 브랜치에서 작업 브랜치 생성
    - [브랜치 명명 규칙](#브랜치-명명-규칙) 참조  

3. 생성된 브랜치에서 작은 단위로 커밋 수행
    - [커밋 메시지 작성 규칙](#커밋-메시지-작성-규칙) 참조 
    - 작업중 origin에 푸시해도 좋음

4. dev 브랜치로 PR(Pull Request)
    - [PR 메시지 작성 규칙](#PR-메시지-작성-규칙) 참조 
    - 릴리즈 노트에 자동 반영됨 (dev 브랜치로 push될때, GitHub Action자동 실행)
    - (optional) 필요시 리뷰 요청

5. PR Merge
    - 프로젝트에 따라, 직접 merge하거나 담당자가 merge 실행

6. 작업 정리
    - 작업 브랜치 삭제 (local, origin 모두)
    - (optional) 이슈 코멘트후 Close 처리


### 릴리즈 만들기
1. main 브랜치에서 릴리즈 브랜치 생성   
    ```release-0.9.2```

2. 릴리즈 브랜치에 dev 브랜치 머지하기

3. 릴리즈 브랜치에서 릴리즈 작업 수행
    - Version Bump
    - Build Setup 
    - 테스트

4. main 브랜치로 PR하거나 merge

5. main 브랜치에서 릴리즈(tag) 실행

6. dev 브랜치로 변경사항 반영을 위해 merge


## 명명 규칙 및 메시지 작성 규칙
기본적으로 커밋, PR 메시지는 시간을 들여서라도 잘 작성하기

### 브랜치 명명 규칙
- 규칙 : {id}/{branch-name}  
```epic/add-log-func```

- 이슈번호를 사용해도 좋음  
```epic/issue30```
- **중요** 브랜치가 머지될 때, 브랜치 이름이 커밋 메시지로 기록됨


### 커밋 메시지 작성 규칙
- 이해하기 어려운 영어보다는 간단 명료하게 작성된 한글도 좋음  
```업데이트모듈에 상태정보를 보여주는 로그 기능 추가```
- 다수 앱이 있는 프로젝트의 경우 : ({app-name}) {message}  
```(deep_client) update.py에 로그 기능 추가```

### PR 메시지 작성 규칙
- 이슈 번호를 넣으면 이슈에 자동 등록됨  
```확인 버튼 눌렀을때, 에러 처리 #23```
- 다수 앱이 있는 프로젝트의 경우 : ({app-name}) {message}  
```(deep_client) 상태 정보를 보여주는 로그 기능 추가```
- 추후 Release note에 자동으로 반영됨([Release-drafter](#https://github.com/release-drafter/release-drafter) 활용)

## References

### Git Clients
- Git Graph  
https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph
- GitHub Desktop  
https://desktop.github.com/
- GitKraken (유료)  
https://www.gitkraken.com/

### 읽어볼만한 글
- Understanding the GitHub flow  
https://guides.github.com/introduction/flow/

- Git 뉴비를 위한 기초 사용법 - 시작하기  
https://evan-moon.github.io/2019/07/25/git-tutorial/

- Git 뉴비를 위한 기초 사용법 - 버전 관리  
https://evan-moon.github.io/2019/07/28/git-tutorial-advanced/

- 커밋 히스토리를 이쁘게 단장하자   
https://evan-moon.github.io/2019/08/30/commit-history-merge-strategy/

- Git과 GitHub  
https://brunch.co.kr/magazine/gitandgithub


### 기타
- 우린 Git-flow를 사용하고 있어요  
https://woowabros.github.io/experience/2017/10/30/baemin-mobile-git-branch-strategy.html

- A successful Git branching model  
https://nvie.com/posts/a-successful-git-branching-model/


  


# Author
epic@devbox.co.kr  
devBOX Inc.