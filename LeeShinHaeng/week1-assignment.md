## GitHub issue templates

### 이슈란?
- 프로젝트를 진행하며 발생하는 버그, 기능 개발 등을 말함.
- 프로젝트의 issues 탭에서 관리 가능
### 정의
- 프로젝트의 이슈 트래킹을 효과적으로 관리하기 위해 사용되는 템플릿
### 사용법
1. 템플릿 설정
    - 프로젝트 → settings → Features → Issues → Set up templates 클릭
2. 템플릿 추가
    - Add template에서 사용하고자 하는 템플릿 추가
        - Bug Report
        - Feature request
        - Custom
3. 추가된 템플릿 설정
    - 추가된 템플릿의 Preview and edit → 연필아이콘을 눌러 형식 설정
    - 마크다운 형식으로 작성 가능
    - 이슈 제목 형식 설정 가능
4. Propose changes를 눌러 커밋창 띄운 후 커밋 
5. 프로젝트 → Issues → New issue에서 이슈 템플릿 이용 
### 장점
- 이슈를 생성할 때 미리 정의된 형식을 제공
- 이슈의 내용과 정보의 일관성을 유지
- 효율적이고, 쉽게 이슈 사용 가능
### 참조
- [https://velog.io/@yulhee741/Github-Issue-Templates으로-Issue-쉽고-체계적이게-작성해보기]
---

## Git Branch 전략

### 필요성
- 작업 중인 파일을 다른 사람이 건드릴 위험 존재
- 히스토리가 메인 브랜치에 뒤죽박죽 섞임
- 병렬 개발에 어려움
- 롤백하기 어려움
- 메인 브랜치가 불완전한 상태로 존재
### 종류
- Git Flow
    
    : 5개 종류의 브랜치로 나눠 관리하는 전략

    - 브랜치 종류 
    
    1. Main
        
        : 출시 가능한 프로덕션 코드를 모아둠 
        
    2. Develope
        
        : 다음 버전을 위한 신기능을 모아두고 출시할 때 Main에 Merge 
        
    3. Feature
        
        : 세부 기능을 개발하는 코드를 모아두고 각 기능 개발 완료 시 Develope에 Merge
        
        - 작명법: feature/기능
    4. Release
        
        : 출시 하기 전 여러가지 테스트 및 수정을 위한 브랜치. 여기서 가다듬고 완성되면 Main에 Merge + Develope에도 Merge 해서 개발을 이어 갈수 있게 함
        
    5. Hotfix
        
        : Main에서 급하게 수정해야 할 버그 발생 시 Main에서 직접 따서 수정 후 Merge
        
    
    ※ 웹앱에 적합하지 않을 수도 있음
    
    - 이유1. 일반적으로 롤백되지 않음
    - 이유2. CI/CD되므로 여러 버전의 SW를 제공할 필요가 없음
- Github Flow
    
    : Git Flow에 비해 단순한 구조로 Github환경에서 사용하기 적합 

    - 브랜치 종류 
    
    1. Main
        
        : 언제 배포하든지 문제 없을 만큼 항상 Stable한 상태를 유지 
        
    2. Topic
        
        : 새로운 기능을 개발할 때 사용
        
        - Git Flow의 Feature, Hotfix를 통합한 것과 유사한 개념
        - 기능이 완성되지 않더라도 꾸준히 Push하고 커뮤니케이션
        - 완성되면 PR을 통해 Main에 Topic을 Merge
- Trunk-based
    
    : Github Flow와 유사한 방식으로 Main외에 하나의 브랜치만 관리 -> 더 간단
        
### 참조
- https://www.youtube.com/watch?v=EV3FZ3cWBp8
- https://hudi.blog/git-branch-strategy/

---

## Naming convention

### 정의
    
: 식별자에 사용되는 문자열을 선택하기 위한 여러가지 규칙
    
### 목적
- 가독성 향상
- 더 나은 이해
- 코드 작성시 일관성을 촉진
### 종류
- UpperCamelCase(PascalCase)
    
    : 첫 단어를 포함한 각 단어의 첫문자를 대문자로 표시
    
    - 주로 클래스명에 사용
- lowerCamelCase
    
    : 첫 단어를 제외한 각 단어의 첫문자를 대문자로 표시
    
    - 주로 함수명, 변수명에 사용
- snake_case
    
    : 각 단어 사이를 언더스코어 _ 로 구분
    
    - 파일명에 사용
- kebab-case
    
    : 각 단어 사이를 하이픈 - 으로 구분 (꼬치모양처럼)
    
    - 일부 css나 html에서 사용
### 참조
- https://bmind305.tistory.com/45
- [https://velog.io/@hahan/Naming-Convention이란-무엇일까]
