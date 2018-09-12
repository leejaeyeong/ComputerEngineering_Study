## GIT이란 ?
**git은 프로그램 등의 소스 코드 관리를 위한 분산 버전 관리 시스템이다.** 기하학적 불변 이론을 바탕으로 설계됐고, 빠른 수행 속도에 중점을 두고 있는 것이 특징이다. 최초에는 리누스 토르발스가 리눅스 커널 개발에 이용하려고 개발하였으며, 현재는 다른 곳에도 널리 사용되고 있다. 깃의 작업 폴더는 모두, 전체 기록과 각 기록을 추적할 수 있는 정보를 포함하고 있으며, 완전한 형태의 저장소이다. 네트워크에 접근하거나 중앙 서버에 의존하지 않는다.

## 관련 용어 정리
 - **repository** : 파일이나 폴더를 저장해 두는 곳
 - **remote** repository : 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소
 - **local repository** : 내 PC에 파일이 저장되는 개인 전용 저장소
 - **index** : repository에 기록하기 전 파일 상태를 기록하는 곳
 - **stage** :인덱스에 등록하는 것(인덱스에 등록은 원하는 일부 변경사항만 등록할 수 도 있다.
 - **commit** : 가장 최근 commit 후 부터 지금까지의 변경 사항을 현재 local repository에 저장

 ## Git 명령어 정리
  - **Init** - 로컬 디렉토리를 깃 저장소로 등록 한다
  - **Commit** - 로컬에 변경사항 기록한다.(snapshot)
  - **Clone** - sever의 repo를 불러온다
  - **Push** - 서버에 변경사항 저장
  - **fetch** - 서버의 변경사항이 있는지 확인한다.
  - **pull** - 서버의 변경사항을 로컬 저장소로 불러온다.
  - **PR(Pull request)** - 다른 branch와 merge 되는지 checking 하는 단계이다.
  - **Checkout** - 해당 branch로 이동한다.(해당 branch로 변경)
  - **Reset(option)** - 해당 commit point로 초기화한다.
    - soft : 로컬 변경사항을 유지한 채로 해당 commit point로 reset
    - mixed : 작업상태는 유지한 채 index는 reset
    - hard : 모든 변경사항을 버리고 해당 commit point로 reset

 ## Source Tree 사용방법
 위에 정리한 명령어는 git bash라는 프로그램을 통해 이용할 수 있다. Source Tree 또한 git bash와 마찬가지로 git 저장소를 관리하기 위한 프로그램이지만 GUI를 제공하기 때문에 보다 직관적으로 이해 할 수 있다.

 ### 1. repository 생성 또는 불러오기
  - `파일` - `복제/생성` : git clone, git init과 같은 항목임을 알 수 있다. url을 입력하라는 창이 나오면 repo의 주소를 복사하는 것으로 내 directory에 clone된다.
  - `파일` - `열기` : 이미 나의 local directory에 local repository가 있을 경우 해당 폴더를 선택하면 Source Tree에 내용을 불러온다.
 ### 2. 서버의 변경 사항 확인 또는 불러오기
  - 작업중에 서버에 저장된 내용이 변경 되었을 수도 있다. 이 경우에는 fetch로 변경 사항을 확인하고 pull로 server의 저장된 내용을 내 local로 불러온다.
 ### 3. 내 local에 변경사항 발생
  - local에 변경사항이 발생한 경우 Source Tree 하단에 stage되지 않은 변경사항이 발생했다는 항목을 볼 수 있다. 이 항목을 stage에 올리는 것으로 변경사항을 commit할 수 있는 상태가 된다. git bash의 git add [파일명]과 같다.
 ### 4. Branch 생성 / 삭제
  - branch를 생성하거나 삭제하는 항목을 확인할 수 있다. GUI에서 현재 checkout된 branch에서 새 branch를 생성한다.
  - 현재 checkout 되어 있는 branch를 삭제할 경우 error가 발생함으로 다른 branch로 checkout한 후 삭제해야한다.
 ### 5. Push
  - Push 버튼을 통해 내 로컬의 변경사항을 서버에 저장할 수 있다.

 ※ Push가 정상적으로 완료되면 PM이 검토 후 문제가 없을 시 merge한다.  

 ## Git Flow
 소프트웨어의 소스코드를 효율적으로 관리하고 제품을 출시하기 위한 브렌치 관리 전략
 **Production** - 특정 버전으로 개발이 완료되어 제품으로 출시될 수 있는 브랜치이다.
 **Hotfix** - 출시해서 배포된 제품에서 발생한 버그를 빠르게 해결하기 위한 브랜치이다.
 **Development** - 다음 출시 버전을 개발하는, 개발자들이 함께 보며 업무를 진행하는 가장 역동적인 브랜치이다.
 **Bugfix** - 다음 출시 버전 개발 중 발생한 버그를 해결하기 위한 브랜치이다.
 **Feature** - 각각의 독립된 기능을 개발하는 브랜치, 기능 개발이 완료 되면 Development로 merge된다.
 개발을 진행하면서 큰 기능을 수행하는 개발을 할때에는 Development, 특정기능 수행을 작업을 진행할 시에는 Feature, 기능 구현 후 merge 후 발생한 버그는 Bugfix,  프로그램 배포는 Production, 배포후에 긴급히 수정해야 할 버그에 관한 작업은 Hotfix에서 작업한다.

 ## Git-Hub
 - Git 저장소를 직접 설치하지 않고 GitHub를 통해 사용 가능하다.
 - 좋은 Web UI를 제공
 - gh-pages Branch 파일을 올리면 [계정명].github.io/[저장소명] 홈페이지가 완성된다.
 - 여러 질문 & 답변, 이슈 사항을 기록하기 위한 Issue 페이지 제공
 - 무료로 이용 시 오픈소스 저장소로 이용 가능하고 유료 결제 시 공개되지 않는 저장소 제공
