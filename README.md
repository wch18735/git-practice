# CRA과정

2024.04.17 ~ 2024.05.10

## Git

CRA 과정 실습

**Code Review Agent 과정 Git 정리**

Git 목적은 버전 관리이고, 이를 사용하는 GitHub 목적은 협업이다. 레포지토리 제공이 아니다. 개발자들이 협업할 때 필요한 모든 도구들이 다 포함되어 있다.

원격 협업에서 사용하는 요청, 질문, 버그리포트, 기능 추가 등을 모두 Issue 라고 한다.

## 명령어 팁

`git rebase -i HEAD~N`

rebase 명령어 치면 보통 History 로그와 순서가 반대로 나타난다. 즉, 위쪽이 더 과거. 여기서 최근 커밋들 왼쪽에 pick 으로 되어있는 값을 s 로 바꾸면 스쿼시(합치기)된다. r 명령으를 쓰면 스쿼시 방향을 반대로 할 수 있음.
 
`git checkout [commit id]`

이 명령어 쓰면 HEAD와 브랜치를 불리할 수 있다. 코딩 공부하고 레포 분석할 때, 특정 커밋으로 이동해서 당시 파일만 확인해 볼 때 쓰면 좋다!

`git commit -am "message"`

ADD + COMMIT 명령어로 익숙해지면 편하다.

`git diff --name-only`

충돌(conflict) 났을 때, 이 명령어로 어떤 파일에서 충돌 났는지 확인할 수 있다.

`git diff --name-only --diff-filter=U --relative`

Use git diff, with name-only to show only the names, and diff-filter=U to only include 'Unmerged' files (optionally, relative to show paths relative to current working directory).


## TDD

테스트를 먼저하라는 뜻은 요구조건과 스펙을 명확히 산출하고 진행한다는 뜻이다.

레드의 의미: 곧 만들 것을 뜻한다.
(Unit Test == To Do)

### TDD 규칙

1. Baby Step

오직 실패할 때만 새로운 코드를 작성하고, 중복을 제거한다.
물론 TDD 할 때 이렇게 작게는 하지 않지만, 작은 단계를 밟을 능력을 갖추면 자기만의 보폭을 찾아낼 수 있다.

2. 설계는 리팩토링에서

구현 모자랑 리팩토링 모자가 있는데 모자는 무조건 하나만 쓴다.
구현 모드일 때에는 To Do 에만 집중하고, 리팩토링 모드일 때에는 문제해결에 집중한다.

마틴 파울러는 컴파일이 실패하지 않는 선에서 테스트를 작성한다는 점에서 켄트 백과 약간의 차이가 있다.

### Why TDD

- 모듈화가 잘 된다.
  자연스럽게 테스트가 쉬운 모듈을 만들게 되는데 이런 테스트 모듈의 특징이 Loose Coupling, Cohesion 높은 모듈이 된다. 

- 버그율 감소
  당연히 버그율이 감소한다.

- Code Coverage 확보
  '알고 있다' 라는 코드 커버리지가 넓어진다. 이로써 심리적 안정감이 커진다.

반면 단점도 있다. 가령, TDD를 위해 Unit Test를 억지로 만드는데 그 비용이 크다. 그런데 이런 경우는 테스트를 작성하는 사람의 숙련도가 부족한 것이지 보통 테스트 자체가 어려운 것이 아니다. 이건 시간이 지나면 점차 해결된다.

또한 단위 테스트가 너무 많아질 수 있다. 테스트 개수가 3,000개인데 이를 관리하는 것이 어렵다. 이러한 품질 관리 역시 스타트업과 같이 개발 속도가 빠른 경우는 짐이 될 수 있다. 그런데 이건 반대로 코드 품질을 높이는 방법이 될 수 있다. 결국은 트레이드 오프!
