# 5JO-REPOSITORY

## 5장 서버 내용정리
* ### 5.1 서버 저장소 (장태현)
  #### 프로젝트의 규모가 커질수록 혼자 개발을 하는 것은 어려워지고 많은 시간과 노력이 요구된다.
  #### 따라서 여러 개발자와 협업을 하면 규모가 있는 프로젝트를 효율적으로 개발할 수 있는데, 이 협업을 위해 만들어진 도구가 바로 '깃' 이다.
  #### 깃은 분산된 여러 저장소를 하나로 통합하며 코드 배포가 가능하다.
  #### 서버 저장소. 즉, 원격 저장소는 장소와 시간의 제약 없이 프로젝트 개발이 가능하고,
  #### 원격 저장소에 코드를 올려 다른 사람들과 공유하고 복제한 코드를 작업한 뒤 다시 원격 저장소에 올려 통합할 수 있다.
  #### 원격 저장소는 새 개발자에게 현재 개발중인 프로젝트의 코드를 공유하는데 있어서 매우 용이하다.
  
* ### 5.2 깃허브 서버 준비 (장태현)
  #### 개인이 독립적인 깃 서버를 운영할 수 있지만 유지, 관리 비용 부담 등의 이유로 365일 서버 운영을 하기는 어렵다.
  #### 그리하여 개발자들 사이에서 보편적으로 쓰이는 '깃 허브' 라는 깃 호스팅 서비스를 사용한다.
  #### 회원가입 절차에 '사용자 이름'을 입력하는 부분이 있는데 이 것은 개별 깃허브 주소를 가질 때 사용된다. (https://github.com/사용자이름)
  #### 저장소 생성은 우선 + > New repository를 선택한다. 그후, 저장소를 생성할 소유자(owner)를 선택한다.
  #### 다음으로 Repository name에 중복되지 않는 이름 내에서 원하는 저장소 이름을 입력한다.
  #### 그 후 저장소 페이지에 접근하기 위해서는 https://github.com/소유자/저장소 형식으로 접속하면 된다.
  
* ### 5.3 깃허브 연동 및 원격 등록 (김성원, 이세진)
  #### 원격 저장소에 연결하려면 먼저 로컬 저장소가 있어야 한다.
  #### 연결하는 방법은 새 로컬 저장소를 생성하고 연결하거나, 기존 저장소를 연결하는 방법이 있다.
  ###### $ mkdir (폴더 이름) -- 새 폴더 만들기
  ###### $ cd (폴더 이름)
  ###### $ git init -- 저장소를 깃으로 초기화 -> 새 로컬 저장소를 만들고 초기화 
  ###### $ echo "# (폴더 이름)" >> README.md -- 파일 생성 -> 저장소의 소개 페이지 파일 생성
  ###### $ git add README.md -- 스테이지에 등록
  ###### $ git commit -m "first commit" -- 커밋 -> README.md 파일을 추적 등록하고 커밋
  #### 서버와 통신하려면 프로토콜을 사용해야 하는데, 깃은 기본적으로 Local, HTTP, SSH, Git 네 종류의 전송 방식을 지원한다.
  #### Local(로컬) - 로컬은 간단하게 원격 서버를 구축할 수 있을 뿐만 아니라 빠른 동작이 가능하지만, 모든 자료가 자신의 컴퓨터에 집중되는 위험도 있다.
  #### HTTP - 서버에 접속하려면 로그인 절차를 거쳐야 하는데, HTTP는 기존 아이디와 비밀번호만으로 접속자를 인증하여 처리할 수 있다. 익명 처리 가능, 계정 이용 처리 가능
  #### SSH - 높은 수준의 보안 통신으로 처리하기 때문에 깃 서버를 좀 더 안전하게 운영할 수 있다. 익명으로 접속 불가능.
  #### SSH 프로토콜을 사용하려면 주소 앞에 'ssh://계정@주소'처럼 프로토콜 타입을 지정해야 한다.
  #### SSH 접속을 할 때는 인증서를 만들어 사용하는데 인증서로 접속하면 별도의 회원 로그인 절차를 거치지 않아도 된다.
  #### 인증서는 공개키와 개인키로 구분하는데 각각 서버, 로컬에 저장한다.
  #### Git - 깃의 데몬 서비를 위한 전용 프로토콜 방식이다. SSH와 유사하지만 인증 시스템이 없어 보안에 취약할 수 있다.
  #### 깃은 원격 저장소(서버)를 관리하는 데 remote 명령어를 사용하는데 이 명령어는 현재 연결된 원격 저장소 목록을 확인할 수 있고, 동시에 등록과 취소 등 작업을 할 수 있다.
  #### $ git remote -- 원격 저장소의 이름을 출력 / 간단하게 원격 저장소 목록만 확인할 때 편리
  #### $ git remote -v --  원격 저장소의 별칭 이름과 URL을 확인
  #### 깃은 복수의 원격 저장소를 연결하여 사용할 수 있고, 리모트 저장소가 여러개 있을 때는 목록을 모두 출력한지만 저장소의 권한 정보까지는 알 수 없다.
  #### 로컬 저장소에 원격 저장소(서버)를 등록하려면 서버 주소(프로토콜 + 도메인 주소 형태)가 필요하다.
  - ### 5.3.5 원격 저장소에 연결 (이세진)
    ####    git remote 명령어의 add 옵션을 이용하여 로컬 git 저장소에 원격 저장소를 추가할 수 있다. 
    ####    $git remote add 별칭 원격저장소URL 별칭(별칭은 문자열의 서버 주소를 대체한다.)을 붙여 원격저장소를 추가하는 문장은 다음과 같다.
    ####    이미 특정 원격 저장소와 연결이 되어 있을 때 연결을 끊고 다른 저장소와 새로 연결하거나 한번에 여러개의 저장소에 push하는 등 활용 할 수 있다.
    ####    원격 저장소를 추가하는 방법은 3가지가 있다.
    ####    1) 기존 원격저장소는 유지하고 추가
    ####    2) 기존 원격저장소를 old-origin으로 변경하고 origin으로 추가
    ####    3) 기존 원격 저장소를 삭제하고 추가
  - ### 5.3.6 소스트리에서 원격 브랜치 (이세진)
    ####    원격저장소를 연결하면 master이외의 또다른 브랜치가 표시된다.
    ####    master는 현재 로컬 저장소를 의미하고, 별칭이 붙은 것은 원격 저장소의 브랜치이다.
  - ### 5.3.7 별칭 이름 변경과 정보 (이세진)
    ####    $git remote rename 변경전 변경후: rename 옵션으로 별칭을 변경할 수 있다. 
    ####    show 옵션으로 원격 저장소의 상세한 정보를 알 수 있다. 
    ####    $git remote show 별칭 :remote 명령어는 간략한 원격 저장소 정보를 출력한다.
    ####    remote 저장소의 URL과 추적하는 브랜치를 출력하낟. git pull 명령은 remote 저장소 브랜치의 데이터를 모두 가져오고 나서 자동으로 Merge할 수 있다. 
    ####     로컬레서 관리하던 remote 저장소의 브랜치 이름도 변경된다. 
  - ### 5.3.8 원격 서버 삭제 (이세진)
    ####    로컬 저장소에 여러 원격 저장소를 연결할 수 있다. 
    ####    $git remote rm 별칭: rm 옵션으로 임시 등록된 원격 저장소를 삭제할 수 있다. 
  
* ### 5.4 서버 전송 (양준모)
  #### push : 원격 저장소로 커밋된 파일들을 업로드하는 동작
  #### $ git remote -v를 이용하여 원격 저장소와 연결된 서버 목록을 확인
  #### $ git push (원격저장소별칭) (브랜치이름을) 통해 커밋들을 원격저장소에 저장할 수 있다
  #### $ git push origin master으로 보면 origin=원격저장소별칭, master=브랜치이름
  
* ### 5.5 자동으로 내려받기 (김태윤)
  ### clone 복제 :
일반적인 복제와 원격저장소를 복제하는 방법은 차이가 있다.

원격조장소를 다른 이름의 로컬 저장소에 복제하는 명령어 예시
$ cd 메인폴더
$ mkdir gitstudy05_clone 복제할 새 폴더 만들기
$ cd gitstudy05_clone/

   
* ### 5.6 수동으로 내려받기 (양준모)
  #### 원격 저장소의 내용을 내려받는 방법은 크케 두가지로 pull(풀)과 fetch(페치)가 있다
  #### pull(풀)은 원격 서버에서 현재 커밋보다 더 최신 커밋 정보가 있을 때 내려받는다
  
  #### 여러 개발자와 협업하는 과정에서 pull 명령어가 자동으로 브랜치 병합을 하지 못하고 충돌이 발생하기도 하는데 이럴때는 페치 방식을 사용해야 한다
  #### fetch(페치)는 원격 저장소에서 코드를 수동으로 내려받는 작업을 한다.
  #### 페치 사용 방법 : $ git fetch 원격저장소URL
  #### pull 명령어와 달리 fetch 명령어를 실행한 후에는 커밋이 추가된 것을 확인할 수 없당. 
  #### 왜냐하면 페치는 원격 저장소의 커밋들만 가지고 왔을 뿐 로컬 저장소에서 어떤 작업도 하지 않기 때문이다.
  #### 내려받은 커밋을 로컬 저장소에 적용하려면 병합 명령을 실행해야 하는데 이떄 merge 명령어를 사용해야한다.
  #### $ git merge 원격저장소별칭/브랜치이름 명령어를 사용하면 수동으로 병합이 된다.
  #### 1. pull명령어 사용 2. pull오류 나면 fetch로 커밋을 가져오고 merge로 가져온 커밋을 병합

Note
   
* ### 5.7 순서 (김태윤)
  ### (내용)
   
* ### 5.8 정리
  ### (내용)
