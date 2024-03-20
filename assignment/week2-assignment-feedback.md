# 2주차 과제 안내
안녕 친구들~! 맞는 2주차 과제 피드백을 제공하니 다시 한번 고민해보고 프로젝트에 적용하면 좋을 것 같아. 스터디의 목적이 토이 프로젝트를 돕기보다는 **심화 캡스톤 프로젝트**의 체계화를 위한 것이니 프로젝트 고유의 규칙 보다는 보편적으로 사용되는 규칙을 사용하는게 좋을 것 같다는게 내 의견이야~!

<span style="color:#FFFFFF88">피드백 대상 문서</span> [2024년도 겨울 방학 단기 스터디 > 이신행 > 2주차 과제 제출](https://github.com/kgu-develop/winter-junior-study/blob/LeeShinHaeng/LeeShinHaeng/week2-assignment.md)

## 피드백 주제
<h> 1. GitHub issue templates 적용 &nbsp <span style="color:#E16970">**피드백**</span></h>
<span style="color:#FFFFFF88"><del>2. Git Branch 전략 적용</del></span> &nbsp **통과**
<span style="color:#FFFFFF88"><del>3. Naming convention 적용</del></span> &nbsp **통과**

---

## 피드백 내용
GitHub을 사용하면서 Commit Message, Pull Request 등에 라벨을 붙여서 사용합니다. 프로젝트 고유의 라벨을 사용하는 것도 프로젝트의 독특한 작업 흐름이나 이슈 유형을 원활하게 다루게 해줍니다. 라벨을 붙이는 목적은 아래와 같습니다. **정보 제공,  분류 및 필터링, 작업 흐름 관리, 커뮤니케이션** 등입니다. 다만 과제를 보면 라벨을 `backend` `frontend` `fix` 3가지로 설정했는데 그렇다면 다음과 같은 문제가 발생할 것 같습니다.

1. **세분화된 라벨링 부족:** 코드 작성 중 특정 작업 내용으로 돌아가고 싶을 때, git commit message의 로그가 아래와 같다면 어떤 commit이 본인이 원하는 작업 내용을 담고 있는지 파악하기 어렵습니다.
```python
* frontend: add vector asset about text editor
* frontend: update SRS about text editor
* frontend: implement text editor
```
2. **직관성 부족:** 광범위한 라벨을 사용하여 commit message를 작성하면 특정 작업 내용을 파악하기 위해서 message를 전부 읽어야 한다는 단점이 있습니다.
3. **다른 프로젝트와의 호환성:** 이번 프로젝트에서만 특수하게 적용 가능한 라벨은 다음 프로젝트에서는 적용 못할 수도 있습니다. 하지만 보편적으로 사용되는 라벨 모음 `feat` `fix` `refactor` 등은 대부분의 프로젝트에서 적용 가능하고 팀원의 적응이 쉽다는 장점이 있습니다.

</br>

라벨을 세분화하면 아래와 같이 작업 내용을 세분화하고 복구할 작업 내용의 로그를 명확히 알 수 있습니다. 또한 너무 광범위한 라벨링은 commit 단위를 넓혀 잘못된 commit 습관을 가지게 합니다. 
```python
* gui: add vector asset about text editor
* chore: update SRS about text editor
* build: add manage external storage permission
* gui: design text editor layout
* feat: implement text loader
* refactor: separate text editor feat into mvp pattern
```

</br>

## 피드백 과제

라벨에 대해서는 **스터디 목적에 맞게 프로젝트에 적용하려 한다면** 2월 17일까지 `[2주차] 과제 피드백 반영 제출 `이라는 제목으로 다시 제출해주세요~

그리고 프로젝트에 과제 내용(`GitHub issue templates` `Git Branch 전략` `Naming convention`)을 적용하거나 적용하기 위해 정의한 문서를 링크로 제출해주세요~!

--- 

### 참고 링크

KGU Developer 서지원 [Advanced-Another-Art > Labels](https://github.com/sjiwon/Advanced-Another-Art/labels)