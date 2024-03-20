# 4주차 과제

## 기술 블로그 & GitHub README

### 기술 블로그

- 링크
    - https://velog.io/@snhng
- velog 선택 이유
    - 직관적이고, 빠른 세팅
    - 많은 개발자의 사용
    - 마크다운 언어 지원

### GitHub README

- 링크
    - https://github.com/LeeShinHaeng/LeeShinHaeng/blob/master/README.md
- 참조
    - https://80000coding.oopy.io/865f4b2a-5198-49e8-a173-0f893a4fed45
    - https://velog.io/@somm/Github-readme-꾸미기
    - https://github.com/Kimhanyeol/Kimhanyeol/blob/main/README.md

---

## Logging

### 로그란?

- 개념
  - 런타임 동안 로그 메시지를 기록하고 저장하는 데 사용되는 메커니즘
  - 시스템 운영에 대한 기록

- 목적
  - 디버깅, 시스템 에러 추적, 성능, 문제점 향상 등의 목적으로 사용

- 언제 사용?
  - 로직의 흐름, 예외 등등을 파악하고 싶을 때
  - 주로 예외 상황


### 자바에서의 로그

1. Logger 클래스를 생성한다.
   - 편의를 위해서 모든 레벨의 로그를 저장하는 코드로 작성
   - java.util.logging.Logger 클래스에서 제공하는 getLogger() 메서드를 사용
2. 로그를 생성할 파일을 생성 및 지정
   - 싱글톤 패턴으로 생성자에서 생성
    

### 스프링부트에서의 로그

- 스프링부트는 자바 친화적인 프레임워크지만 Logger 클래스 외에 로그를 남기는 다양한 방식을 지원한다.
- 그중 대표적인 것이 바로 logback!
  - Slf4j의 구현체
- 사용법
  1. 로그 사용
    - 클래스위에 @Slf4j 어노테이션을 붙이기 (Lombok 사용)   
    - 로거 팩토리에서 직접 가져오기
        ```
        private static final Logger log = LoggerFactory.getLogger(Log.class);
  2. Springboot 로그 설정
    1. resourece 디렉터리 밑에 logback-spring.xml을 읽고, 로그를 만듭니다. 
    2. 위의 logback-spring.xml이 없다면, .yml파일 혹은 .properties 파일을 읽고, 로그를 만듭니다. 
    3. 만약 두 개 다 있다면, .yml파일 먼저 읽고, logback-spring.xml 파일에서 추가되는 부분을 사용합니다. 
  3. 세부 설정
    - 레벨 지정
      - TRACE  <  DEBUG  <  INFO  <  WARN  <  ERROR  <  FATAL
    - Appender 
      - 로그의 출력 위치를 지정
    - rollingPolicy
      - max-file-size: 로그 파일 1개의 최대 용량(size)를 설정
      - max-history: 로그 파일을 유지할 기간(일수)을 설정
      - totalSizeCap
    - 로그 파일 이름 설정
      - logging.file.name : 로그 파일의 이름



### 로그의 사용 예시 (스프링, 롬복 사용)

- 입력값 로그로 남기기 (간단히)
```
@Slf4j
public class UserController {
    private final UserService UserService;

    public void saveUser(UserCreateRequest request) {
      UserService.save(new User(request.getName(), request.getAge()));
      log.info("name={}, age={}",request.getName(), request.getAge());
    }
}
```
결과
```
name=aaa, age=20
```

### 참조
- https://berom.tistory.com/213
- https://sdesigner.tistory.com/100
- https://wikidocs.net/163118
- https://loosie.tistory.com/829

---


## Git Squash & Rebase & Stash


### Squash

- 여러 개의 커밋을 하나의 커밋으로 합치는 방법
- 기능
  - 여러 개의 중간 커밋들을 깔끔하게 정리하여 하나의 의미 있는 커밋으로 관리 가능

### Rebase

- base를 재설정한다는 의미
- 하나의 브랜치가 다른 브랜치에서 파생되서 나온 경우, 다른 브랜치에서 진행된 커밋을 다시 가져와서 base를 재설정하는 것
- 기능
  - 불필요한 병합 커밋을 제거
  - 마치 하나의 브랜치에서 작업된 것처럼 병합이 아닌 선형의 커밋 히스토리가 남기 때문에 작업 이력을 확인하기 유용
- 유의점
  - 파생된 브랜치에서 이미 새로운 커밋이 발생했다면 위험함
  - 작업이 기록되고 있는데 이전 기준 브랜치로 base를 변경해버리면 파생브랜치로 작업하고 있던 작업자들의 커밋 히스토리가 변경되기 때문
    - 파생브랜치로 작업하고 있던 작업자는 커밋을 다시 반영하거나 재작업을 해야 할 수도 있음 
- interactive 모드
  - interactive 모드 명령을 실행하면 텍스트 편집기가 열리면서, 커밋을 변경 할 수 있음
  - 변경 옵션
    - p, pick: 해당 커밋을 수정하지 않고 그냥 사용하겠다 라는 명령어
    - r, reword: 커밋 메세지를 수정하기 위한 명령어 
      - 저장후 에디터를 닫으면 커밋을 변경할 수 있는 다른 에디터 창이 출력
    - e, edit: 작업을 수정하거나 커밋 사이에 커밋을 추가
      - 저장후 종료하면 reword 처럼 커밋 메세지를 수정할 수 있으며, 변경할 커밋으로 checkout되어 작업을 수정하거나 커밋 사이에 커밋을 추가 가능
      - 커밋 메세지를 수정: git commit --amend
      - 커밋 추가: git add와 commit 명령어로 커밋과 커밋 사이에 commit을 만든 후 git rebase --continue로 진행중인 리베이스 과정을 종료
    - s, squash: 해당 커밋을 이전 커밋과 합치는 명령어
    - f, fixup: "squash"처럼 작동하지만 이전 커밋 메세지만 남김
    - e, exec: 리베이스를 저장후 종료할 때 실행할 쉘 명령어를 작성
    - b, break: 해당 라인에서 리베이스를 일시중지 
      - a2와 a3 사이에서 break 명령어를 사용하면 해당 커밋에서 a2에서 일시중지
      - 일시중지된 커밋에서 추가적인 작업이 가능
      - continue 명령어를 사용하면 재개
    - d, drop: 해당 커밋을 명시적으로 삭제하는 명령어
      - 커밋 리스트에서 지우는 것과 같은 기능이지만 어떤 커밋이 삭제 됐는지 출력 
- Rebase와 Merge의 차이점
  - 결과
    - merge: 두 개의 다른 브랜치를 하나로 합침
    - rebase: 기존 브랜치를 다른 브랜치의 끝으로 이동시키면서 커밋 히스토리를 재작성
  - 커밋
    - merge: 실제 통합을 보여주는 별도의 커밋이 생성 ->  상대적으로 복잡
    - rebase: 히스토리가 선형적
  - 브랜치
    - merge: 두 브랜치가 동시에 존재 ->  브랜치의 내용이 모두 유지
    - rebase: 브랜치가 변경 -> 이전 브랜치의 내용이 새로운 브랜치로 흡수

### Rebase를 이용한 Squash 사용법
- 단순히 squash 명령만으로는 작업을 수행 불가
- git rebase의 interactive 모드를 사용
1. Rebase (Interactive 모드)
   - 작업을 정리하고 싶은 커밋의 개수만큼 이전으로 이동
   ```
    git rebase -i HEAD~[커밋 개수]
   ```
   - 텍스트 에디터가 열리며, 여러 커밋 목록이 표시. 
   - 합치고 싶은 커밋 앞의 키워드를 squash 또는 간단히 s로 변경
2. Merge, Squash
    ```
      git checkout main-branch
      git merge --squash feature-branch
      git commit 커밋 내용 
    ```

### Stash

- 정의
  - 아직 마무리하지 않은 작업을 스택에 잠시 저장할 수 있도록 하는 명령어
  - 기능
    - 아직 완료하지 않은 일을 commit하지 않고 나중에 다시 꺼내와 
  - 가능한 파일
    1. Modified & Tracked = 과거에 한번이라도 commit한적 있는 파일
    2. Stagied 상태의 파일 = add 명령어를 실행한 파일


- 사용법
  1. Stash
     - 새로운 Stash 스택을 만드렁 작업을 임시로 저장
     ```
      git stash
     ``` 
  2. 목록 확인
     - 이전에 Stash를 사용한 적이 있다면 다음 명령어로 목록 확인
     ```
      git stash list
     ``` 
     - 결과 예시
     ```
      stash@{0}: WIP on master: 049d078 added the index file
     ```
  1. 스택에서 작업 가져오기
     ```
      # 가장 최근 stash
      git stash apply

      
      # "STASH이름"에 해당하는 stash (stash@{0})
      git stash apply STASH이름

      # !위의 명령어만으로는 Staged 상태였던 파일을 다시 Staged로 만들어주지 않음!
      # --index 옵션을 통해 Staged 상태까지 복원
      git stash apply --index
     ``` 
  2. 제거
     - 스택에서 stash 제거
     ```
      # 가장 최근 stash 제거
      git stash drop

      
      # "STASH이름"에 해당하는 stash 제거
      git stash drop STASH이름

      # apply + drop 하고 싶다면?
      git stash pop
     ``` 
  3. 되돌리기
     - 잘못 Stash를 적용해서 되돌리고 싶다면?
     ```
      # 가장 최근 stash를 사용해 패치를 만들고 그것을 거꾸로 적용 
      git stash show -p | git apply -R

      
      # "STASH이름"에 해당하는 stash로 적용
      git stash show -p STASH이름 | git apply -R
     ``` 

- Stash와 Commit의 차이점
  - 용도
    - Stash: 주로 다른 브랜치로 이동하거나 특정 작업을 위해 현재 작업 중인 변경 사항을 임시로 저장
    - Commit: 변경 사항을 영구적으로 기록 -> 프로젝트의 히스토리에 남겨짐
  - 브랜치와 관련성
    - Stash: 브랜치에 직접적으로 연결되지 않음 -> 다른 브랜치로 이동할 때엗고 적용 가능
    - Commit: 브랜치에 직접적으로 연결

### 참조
- https://velog.io/@lgs03042/Git-Squash-커밋-기록-깔끔하게-관리하기
- https://www.delftstack.com/ko/howto/git/git-squash-commits/
- https://cross-the-line.tistory.com/20
- https://myung-ho.tistory.com/91
- https://gmlwjd9405.github.io/2018/05/18/git-stash.html
- https://velog.io/@bangina/아직도-Git으로-commit만해-Git활용법-1.-Git-Stash

---