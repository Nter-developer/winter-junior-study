#### 1. GitHub issue templates <br>
-> 깃허브 이슈가 약간 퀘스트창 같이 투두리스트를 적어놓는 곳으로 사용된다. <br>
-> 이 때 label을 정해서 어떤 내용에 대한 퀘스트인지 분류해놓을 수 있음 <br>
-> 누군가 퀘스트를 수주하면 다른 사람은 그 퀘스트를 하지 못하는 것 처럼, 팀원이 자기가 이 이슈를 맡겠다고 assigness 로 두면 퀘스트 수주완료 <br>
-> Pull request를 통해서 자기가 해결한 이슈 작업내용을 올리고 각 팀이 정한 규칙대로 팀원들이 ok 하거나 no 하면 merge 하거나 수정해서 다시 올리거나 한다. <br>
-> Pr에서 merge 할 때 해당 이슈 넘버로 연동시켜서 close 할 수 있음 <br>

<br>

#### 2. Git Branch 전략 <br>
-> 여러 개발자가 동시에 작업하고, 동시에 변경 사항을 추가할 때, 애플리케이션에는 많은 오류가 발생할 수 있다. <br>
   코드 간의 충돌이 심할수록, Merge하는 일은 복잡하고 어려워지며 <br>
   Merge에 시간이 많이 쓰이면 쓰일수록, 원활한 워크플로와 효율적인 DevOps 프로세스에 방해가 된다. <br>
-> Git Flow, Github Flow, Gitlab Flow 등이 있는데 이 순서대로 많이 쓰이는 듯 <br>

[Git Flow] <br>
-> 각 용도에 맞게 main(master), develop, feature, release, hotfix 브랜치를 분리해서 사용 <br>
-> 명확한 릴리즈 기간과 주기적인 버전이 정해진 프로덕트를 개발하는 환경에 적합 <br>
-> 릴리즈 버전 관리를 위한 release 브랜치를 따로 관리하기 때문에, 특정 버전에 대한 유지보수 기간이 길고, 여러 버전을 동시에 관리해야 할 필요가 있을때 유용함 <br>
-> 위와 같은 장점 때문에 소규모 팀보다는 규모가 있는 팀에 더 어울림 <br>
-> 근데 좀 복잡하고 어려움 <br>

[Github Flow] <br>
-> 단일 브랜치를 사용 <br>
-> 지금까지 했던 모든 프로젝트가 다 이런식이다. 좋게 말하면 간편하고 나쁘게 말하면 주먹구구식으로 대책없이 하는 방식 <br>
-> 최근 개발한 abc 가계부도 굳이 따지면 이런 식이겠네 <br>
-> 배포 관리가 어렵지만 간편하고 쉽다 <br>
-> 대참사 나기도 쉬움 <br>
-> 소규모 프젝에 용이할듯 <br>

<br>

#### 3. Naming convention <br>
-> 카멜 케이스(camelCase) Lower Version <br>
첫 단어는 소문자로 시작하고, 그 이후의 단어들은 첫 문자를 대문자로 적는 방식이다. <br>
예를 들어, myVariableName, myFunctionName, myClassName 등이 있다. <br>

-> 카멜 케이스(camelCase) Upper Version <br>
쌍봉 낙타 표기법 이라고도 하며, 첫 단어부터 각 단어의 시작 알파벳을 대문자로 작성하는 방법으로 단어와 단어사이는 모두 연결하여 작성한다. <br>
예를 들어, NamingConvention 등이 있다. <br>
보통 클래스명에 많이 사용됨 <br>

-> 파스칼 케이스(PascalCase) <br>
모든 단어의 첫 문자를 대문자로 적는 방식이다. <br>
예를 들어, MyVariableName, MyFunctionName, MyClass 등이 있다. <br>

-> 스네이크 케이스(snake_case) <br>
단어를 밑줄로 구분하여 적는 방식이다. <br>
예를 들어, my_variable_name, my_function_name, my_class_name 등이 있다. <br>

-> 케밥 케이스(kebab-case) <br>
단어를 하이픈(-)으로 구분하여 적는 방식이다. <br>
예를 들어, my-variable-name, my-function-name, my-class-name 등이 있다. <br>

-> 헝가리안 케이스(strHungarianCase) <br>
헝가리안 표기법으로로 더 많이 불린다.(다른 것들도 다 가능) <br>
이는 함수의 이름 앞에 변수의 타입을 나타내는 접두사를 붙이는 방법이다. <br>
예를 들어, "strName"과 같은 형태로 표기한다. <br>
이 방법은 변수의 타입을 명시하여 코드의 가독성을 높이고, 코드의 버그를 방지하는 데 도움이 된다. <br>
하지만 요즘에는 대부분의 프로그래밍 언어에서 타입 추론 기능을 제공하기 때문에 헝가리안 표기법은 더 이상 많이 사용되지 않는다. <br>
