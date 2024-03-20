> 4주차 과제

---

# 기술 블로그 & GitHub README

### 기술 블로그
[https://dawning-record.tistory.com/](https://dawning-record.tistory.com/)

### GitHub README

[https://github.com/Kimhanyeol/Kimhanyeol/blob/main/README.md](https://github.com/Kimhanyeol/Kimhanyeol/blob/main/README.md)

---

# Logging

### 로그란?

- 컴퓨터의 처리 내용이나 이용 상황을 시간의 흐름에 따른 기록 </br>
- 개인용 컴퓨터 통신에서 메일 등 통신 내용의 기록이며, 그 파일을 로그 파일(log file)이라고 한다</br>
- 통나무 목선 log on(승선), log out(하선)으로부터 유래되었다</br></br>

### 로그 사용목적

- 시스템 보안이나 유지보수 목적으로 사용된다 </br>
- 사고가 발생했을 때 데이터의 복원이나 사고 원인의 규명 등에 도움이 된다 </br>
- 해킹 등의 사건이 발생했을 때, 로그 파일을 분석하여 사건의 원인을 파악 </br>
- 네트워크의 부정 이용이나 데이터 파괴의 방지와 이용 요금의 산정의 기본 등에 사용 </br>
</br>

### 자바스크립트에서의 로그

``` 
console.log() 를 이용해 로그를 남길 수 있다.
```
</br>

### console api 목록

| 메소드 이름 | 내용 |
| --- | --- |
| console.log() | 임의의 값 출력 |
| console.clear() | 콘솔 화면 비움 |
| console.error() | 오류 정보로 출력(info, warn도 있음) |
| console.group() | 계층 구조를 갖게 출력(groupEnd()로 종료) |
| console.time() | time() ~ timeEnd() 사이 시간을 계산 |
| console.trace() | 호출 함수 등을 기록, 실행 과정 출력 |
| console.count() | 실핼할 때 마다 카운트 up, 횟수 출력 |
| console.table() | 배열, 객체등의 구조를 테이블 형태로 출력 |
| console.dir() | 객체가 보유한 속성목록 리스트 출력 |

</br>


## print 와 무슨 차이일까??

log에 대해 찾아보다 보니 println 혹은 system.out.println() 과 똑같은 역할을 하는 거 같은데, </br>
익숙한 print 냅두고 왜 로그를 써야하는 지 궁금해서 찾아봤다. </br>
</br>

### 휘발된다

```System.out.println()``` 은 로그가 표준 출력으로 출력된다. </br>
즉, 파일로 저장되지 않고 휘발된다는 의미이다. </br>
로그는 에러가 발생한 상황을 기록하고, 추후 확인하여 문제를 진단하고, 재현하고, 고치기 위해 사용된다. </br>
하지만 표준 출력으로 한번 출력되고 어디에도 저장되지 않으면 로그의 제 역할을 할 수 없다.</br>
로그된 데이터는 실제로 기록되어야 한다. 하지만 ```System.out.println()``` 만으로는 불가능하다.</br>

### 에러 발생 시 추적할 수 있는 최소한의 정보가 남지 않는다

```System.out.println()``` 은 인자로 전달한 문자열만을 출력한다. </br>
문제가 발생한 날짜, 시각 그리고 문제의 수준, 로그가 발생한 위치 등 최소한의 정보가 기록되지 않는다는 것 이다. </br>
이런 제한적인 정보만으로는 문제를 해결하기 어려울 것 이다.</br>
물론 이런 정보도 함께 인자로 전달한다면 충분히 에러와 장애를 추적할 수 있는 정보를 남길수야 있지만… </br>
매번 그런 정보를 일일히 남기기엔 번거로울 것 이다.</br>

### 로그 출력 레벨을 사용할 수 없다

로컬에서 개발할 때에는 디버깅을 위한 아주 상세한 정보가 출력되어 확인할 수 있어야한다. </br>
하지만, 프로덕션에서 동작하는 코드는 에러/장애가 발생할 때 문제를 진단할 수 있는 정보만을 남겨야한다. </br>
개발시에만 사용되는 정보와 문제 상황에 대한 정보가 함께 로깅된다면 문제 해결을 위한 정작 중요한 정보를 얻기 힘들 뿐더러, </br>
민감한 정보를 로그로 남길수도 있기 때문이다. </br>
또한 의미없는 로그가 쌓여 서버 용량을 차지할 수도 있다.</br>
</br>

따라서 로깅 라이브러리는 환경에 맞게(로컬 개발 환경, 개발 서버, 프로덕션 서버 등) 로그가 출력될 수 있도록 로그 출력 레벨이라는 기능을 제공한다. </br>
많이 사용되는 Logback이라는 라이브러리에서는 ```TRACE, DEBUG, INFO, WARN, ERROR, FATAL``` 와 같은 레벨을 제공한다. </br>
하지만 ```System.out.println()``` 은 이런 기능을 제공하지 않는다. </br>
어떤 환경에서든 동일한 로그가 출력된다. </br>
프로덕션에서 이런 로그를 제거하려면 코드를 일일히 제거하거나 주석처리하거나 별도의 조건문을 설정하는 등 번거로운 일들을 해야한다.</br>

</br>

### 성능저하의 원인이 될 수 있다

</br>

> System.out.println() 메소드
```
/**
 * Terminates the current line by writing the line separator string.  The
 * line separator string is defined by the system property
 * {@code line.separator}, and is not necessarily a single newline
 * character ({@code '\n'}).
*/
public void println() {
    newLine();
}
```

</br>

> println 내부에 있는 newLine 메소드
```
private void newLine() {
    try {
        synchronized (this) {
            ensureOpen();
            textOut.newLine();
		// ...
```

</br>

여기서 synchronized 때문에 오버헤가 발생해서 성능이 떨어진다는데 더 자세히 찾아보진 않았음

</br>

### 참조

- https://hudi.blog/do-not-use-system-out-println-for-logging/
- https://velog.io/@devjennie/javascript-자바스크립트-콘솔로그-찍는-방법

---

## Git Squash & Rebase & Stash

### Squash

- 여러 개의 커밋을 하나의 커밋으로 합치는 방법 
- 여러 개의 중간 커밋들을 깔끔하게 정리하여 하나의 의미 있는 커밋으로 만들 수 있다
- 보통 git rebase의 interactive 모드를 사용하여 squash 작업을 진행
- 깃허브 pr을 이용하면 머지와 함께 스쿼시할 수 있음

### Rebase

- Rebase 는 말 그대로 base를 재설정한다는 의미로, 하나의 브랜치가 다른 브랜치에서 파생되서 나온 경우, </br>
  다른 브랜치에서 진행된 커밋을 다시 가져와서 base 를 재설정한다는 것
- 브랜치는 base 지점을 가지고 있어, base 에서부터 코드를 수정
- Rebase 는 커밋의 시간에 관계없이 마지막에 merge 되는 브랜치의 커밋을 가장 뒤에 붙이는 전략이다

### Merge

- Merge 는 브랜치를 통합하는 것
- 병합을 하면 합쳐진 브랜치의 커밋 메시지가 중복으로 쌓이며, 새로운 Merge 커밋을 생성


### Stash

- Git stash는 변경사항을 일시적으로 저장하는 기능
- 아직 커밋하기엔 이른 경우나 다른 브랜치로 체크아웃할 때 변경사항을 유지하고 싶을 때 사용
- 혹은 변경사항을 일시적으로 저장하고 싶은 경우 사용

### Stash와 Commit의 차이점
  - 용도
    - Stash: 주로 다른 브랜치로 이동하거나 특정 작업을 위해 현재 작업 중인 변경 사항을 임시로 저장
    - Commit: 변경 사항을 영구적으로 기록 -> 프로젝트의 히스토리에 남겨짐
  - 브랜치와 관련성
    - Stash: 브랜치에 직접적으로 연결되지 않음 -> 다른 브랜치로 이동할 때엗고 적용 가능
    - Commit: 브랜치에 직접적으로 연결


### 참조

- https://resilient-923.tistory.com/358
- https://velog.io/@lgs03042/Git-Squash-커밋-기록-깔끔하게-관리하기
- https://velog.io/@msung99/Git-Rebase란-무엇인가
- https://velog.io/@zeler1004/git-commit과-stash
