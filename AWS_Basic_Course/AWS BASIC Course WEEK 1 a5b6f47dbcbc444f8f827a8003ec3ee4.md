# AWS BASIC Course Week 1

**[수업 목표]**

1. AWS가 무엇이고 왜 쓰는지 알게 됩니다.
2. AWS 제품 중에 가장 가볍게 배워볼 수 있는 S3의 파일 저장 기능에 대해서 알게 됩니다.
3. 개발 언어와 연계해서 AWS를 사용할 수 있는 IAM 에 대해서 알게 됩니다.

## **01. 알아보자 AWS**

- 1.  클라우드란 무엇인가?

  클라우드는 기존의 서버 컴퓨팅 시장을 빠르게 대체하는 산업입니다.

  🔥 클라우드의 성장으로 인해 인프라 아키텍트의 수요가 늘고있고,
  IT 어떤 분야 보다 임금 또한 가파르게 상승하고 있습니다.

  - 클라우드로 인해 빌려쓰는 형태로 변경

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.24.30.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.24.30.png)

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.25.33.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.25.33.png)

  - 2021년 인프라 아키텍트의 평균임금

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__7.53.29.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__7.53.29.png)

- 2.  AWS 무엇인가?

  클라우드는 우리가 만든 서비스를 돌아갈 수 있게 해주는 곳입니다.
  흔히들 웹사이트를 돌리기 위해 필요한 도메인, 서버, 데이터베이스 등등을
  제공해 줍니다. 개발자들 사이에서는 **인프라**라고 얘기합니다.

  AWS는 수많은 클라우드 서비스 중에 제일 잘나가는 서비스입니다.
  **Amazon Web Service** 의 약자이고,
  우리가 잘 알고 있는 쇼핑몰 회사 아마존에서 만들었어요 놀랍죠!!

- 3.  어떻게 사용하는가?

  [사이트](http://aws.amazon.com)에서 가입을 하고 바로 사용하면 됩니다.
  어렵지 않습니다.

  - 하지만 제공하고 있는 서비스가 너무 많다 보니 구성하기가 쉽지 않아요 😱
    그래서 어떤 서비스들이 AWS를 잘 사용하고 있는지 관찰해보면 좋습니다.

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/aws_items.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/aws_items.png)

## **02. AWS를 잘 활용하려면**

---

- 8.  AWS 를 활용하는 서비스들

  AWS를 사용하는 가장 유명한 글로벌 서비스로는 넷플릭스가 있습니다.
  넷플릭스는 AWS로 이사 가는 데만 7년이라는 시간이 걸린 것으로 유명합니다.
  한국에서는 쿠팡, 배민, 당근마켓 등등 거의 모든 스타트업들이 AWS를
  사용하고 있습니다.

  - 넷플릭스는 개발자에게는 세계에서 AWS를 가장 잘 쓰는 회사로 유명합니다.
    AWS의 제품들을 사용한 경험들을 인터넷상에 많이 공개 하기로도 유명합니다.
  - 100만 회원을 가진 서비스에서 1000만 회원을 가진 서비스를 만들기 위해서는 이런 회사들이 AWS를 사용하는 방식을 참조하면 많은 팁을 얻을수 있어요.
  - **[코드스니펫] 넷플릭스**

    ```jsx
    https://aws.amazon.com/ko/solutions/case-studies/netflix/
    ```

- 9.  어떻게 넷플릭스는 AWS를 사용하여 글로벌 서비스를 운영할까?

  - 의미

    AWS는 여러 나라에 데이터 센터를 갖고 있습니다.
    데이터 센터가 있는 나라를 리전이라고 하고, 리전 내의 데이터 센터 위치를
    존이라고 합니다.

    만약에 서울에 데이터 센터가 영등포, 강남, 도봉에 위치하고 있으면 서울리전에 영등포 존, 강남 존, 도봉 존 이라고 불리어지는 것입니다.

    🔥**AWS 의 모든 제품들은 기본적으로 어떤 리전과 존에 배치할지를 먼저 결정해야합니다.**

  - 리전 과 존 이 중요한 이유는 AWS 사용하여 인프라를 구성할때 서비스 하려는 지역의 리전과 존을 사용해야 한다는 것입니다. 한국에서 서비스 하려면 ap-northeast-2 리전을 사용합니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/region.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/region.png)

    - 서비스하려고 하는 지역과 가까운 곳의 리전을 사용할수록 사용자들에게 좀 더 빠른 속도로 서비스를 제공할 수 있습니다.
    - 넷플릭스는 전 세계를 상대로 하는 서비스이기 때문에 클라우드 서비스중에 리전이 가장 많은 AWS를 사용하는 것입니다.

## 03. **S3** 파일 저장소 사용해보기

---

- **[코드스니펫] 참고 문서**

  ```jsx
  https://docs.aws.amazon.com/s3/?id=docs_gateway
  ```

- 10. AWS 로그인 하기

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/login.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/login.png)

- 11. S3 메뉴 찾기

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3.png)

- 12. S3 메인 구경하기

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_main.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_main.png)

- 13. 버킷 만들기

  버킷은 S3에서 파일을 저장하는 폴더라고 생각하시면 됩니다.
  우리가 컴퓨터를 사용할 때 폴더 안에 파일을 저장하는 것처럼
  S3에서도 버킷 안에 파일을 저장합니다.

  버킷 만들기에 보이는 옵션들은 전부 사용하지는 않습니다.
  서비스의 상황에 따라 그때그때 찾아보면서 사용하는 것을 추천드립니다 😀

  그럼 버킷 만들기 버튼을 클릭해볼까요!!

  - 일반구성

    **버킷이름**: 이름은 무수히 많은 버킷중에 고유한 이름이어야 합니다.
    (이유는 나중에 알려드려요!! 기대하세요~ 😛)
    **AWS 리전**: 앞에서 배웠던 리전을 선택합니다.
    **기존 버킷 복사**: 기존 버킷의 설정을 그대로 사용할때 유용합니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket.png)

  - 엑세스 차단 설정

    **액세스 차단 설정**은 버킷에 저장한 파일의 권한을 설정하는 기능입니다.
    **퍼블릭 엑세스**: 버킷이 생성되면 고유한 URL이 부여됩니다. URL을 통해서
    저장된 파일에 접근 할수 있게 하는 기능입니다.
    **ACL**: 액세스 제어 목록으로 버킷과 객체에 대한 액세스를 관리합니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_access.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_access.png)

  - 버킷버전관리

    **버전관리**는 개발할때 소스를 git, svn으로 관리하는 것처럼
    버킷내의 파일들을 버전을 관리할 수 있는 기능입니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_version.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_version.png)

  - 태그

    **태그**는 해당 버킷을 태깅해놓고 이후에 비용측정이라던지
    많은 버킷중에 태그로 검색을 한다던지 할때 쓰는 태깅 기능입니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_tag.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_tag.png)

  - 기본암호화

    **암호화**는 말그대로 파일들을 암호화해서 좀더 보안적으로 신경써서 관리하게 해주는 기능입니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_crypto.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_crypto.png)

  - 고급설정

    **객체 잠금**은 보시는 것과 같이 고~~급 설정입니다.
    중요한 파일이 버킷에 저장되면 보안에 좀 더 신경써야겠죠!!
    이런경우 사용하는 기능입니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_.advancedpng.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/bucket_.advancedpng.png)

  - 🙏버킷만들기 클릭

    버킷이름은 **myspartabucket** 하고,
    AWS 리전은 **아시아 태평양(서울) ap-northeast-2** 로 설정했어요
    나머지 옵션들은 그냥 기본으로 나두셔도 됩니다.
    버킷이 생성되도 설정을 바꿀수 있기 때문이죠 😍
    버킷 만들기 클릭합니다!!

  - 버킷생성 확인

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__4.59.04.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__4.59.04.png)

- 14. 파일 업로드 해보기

  버킷이 잘 생성되셨나요❓
  그럼 바로 파일을 저장해 볼게요 파일 저장은 업로드 버튼 클릭해서
  업로드할 파일을 추가하고 저장하면 됩니다.

  1. 버킷선택

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__4.59.57.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__4.59.57.png)

  2. 업로드 화면 이동 & 파일 추가 & 그 외 옵션

     업로드할 파일을 추가합니다.
     대상 탭에 보시면 업로드할 파일이 어떤 옵션을 가지는지 보이고요
     추가 업로드 옵션을 사용하여 버킷을 만들 때 설정했던 옵션들을 업로드할 때
     다시 설정할 수 있습니다.

     🍯 앞에서도 알려드렸듯이 AWS의 제품들에는 옵션들이 엄청 많아요!!
     옵션들을 전부 알고 있을 필요는 없고 필요할 때 찾아서 쓰시면 됩니다.

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.03.36.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.03.36.png)

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.07.14.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.07.14.png)

  3. 👌 업로드 완료

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.13.12.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.13.12.png)

- 15. 파일 확인 해보기

  1) 파일 리스트 확인

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.17.02.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.17.02.png)

  2) 파일 정보 확인

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.18.33.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.18.33.png)

  3) 객체 URL 확인하기

     S3에 업로드 되는 모든 파일에는 객체 URL이 부여됩니다.
     해당 URL을 브라우저 주소창에서 호출하면 업로드된 파일이 보입니다.

     하지만 파일에 권한을 퍼블릭 하게
     주지 않았기 때문에 AccessDenied 라는 에러가 보입니다.

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.21.15.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.21.15.png)

  4) 권한 탭에서 변경시도

     파일의 권한 탭으로 이동해서 퍼블릭 접근 권한을
     부여하기 위해 편집을 해봅니다.

     하지만 피부여자 그룹에서 객체 소유자의 권한만 변경할수 있고
     모든 사람의 권한은 변경할수 없습니다.

     브라우저에서 접근하기 위해서는 모든 사람의 권한을 변경해 줘야 합니다.

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.40.57.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.40.57.png)

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.41.28.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.41.28.png)

  5) 버킷 권한 확인

     파일의 권한을 퍼블릭하게 주기 위해서는
     버킷의 권한을 퍼블릭하게 수정해줘야 합니다.
     버킷을 생성할때 설정할 수도 있고 생성후에 수정할 수도 있습니다.

     버킷의 엑세스 상태를 확인해보면 모든 퍼블릭 엑세스가 차단된 것이 보입니다.
     🙏 편집버튼을 클릭합니다.

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.29.31.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-03-26__5.29.31.png)

  6) 버킷에 퍼블릭 권한 부여하기

     모든 퍼블릭 엑세스 차단 체크박스의 체크를 풀고
     🙏 변경 사항 저장 버튼을 클릭합니다.

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_public.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_public.png)

  7) 파일 퍼블릭 권한 부여

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_object_public.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_object_public.png)

  8) 브라우저에서 보기

     S3에 업로드된 파일이 브라우저에서 보여요!!
     여기까지 S3의 가장 기본 기능인 파일 저장 기능을 알아보았어요~

     이외에도 S3가 가진 기능은 너~무 많지만 그걸 다 학습하기에는 시간이 꽤 많이 걸려요 그래서 실무에서는 사용하면서 필요한 부분만 학습하고 적용합니다

     ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_image.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/s3_image.png)

## 04. **IAM** 이용하여 AWS SDK를 이용한 S3 파일 업로드

---

- **[코드스니펫] 참고 문서**

  ```jsx
  https://docs.aws.amazon.com/iam/?id=docs_gateway
  ```

- 16. IAM 메뉴 찾기

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam.png)

- 17. IAM 메인 구경하기

  IAM 메인에 보이듯이 Identity and Access Management의 약자인 거 아시겠죠!!
  IAM은 간단히 사용자, 역할을 관리하는 서비스라고 보시면 됩니다.

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_main.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_main.png)

- 18. 프로그램 연동을 위한 계정 만들기

  왼쪽 메뉴 중에 사용자 메뉴를 클릭하여 화면으로 이동합니다.

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_user.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_user.png)

- 19. 사용자 추가

  - 사용자 세부정보, 엑세스 유형 선택

    사용자 이름, 엑세스 유형 중 프로그래밍 방식 엑세스를 체크하고
    다음 단계로 넘어갑니다.
    **프로그래밍 방식 엑세스**는 개발 언어와 연계해서 사용하는 방식이고,
    **AWS Management Console 엑세스**는 해당계정을 AWS 콘솔에서 로그인해서
    사용하게 하는 방식입니다.

    우리는 개발 언어와 연계해서 사용하는 것이 목적이기 때문에 프로그래밍 방식 엑세스만 체크 합니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_addUser.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_addUser.png)

  - 권한 부여

    생성하는 사용자에게 권한을 부여합니다.
    기존그룹에 추가하는 방법, 기존사용자 권한 복사, 기존 정책 직접 연결 하는 방법이 있습니다. 우리는 기존 그룹, 사용자가 없기때문에
    정의되어 있는 정책에 직접 연결하는 방법을 사용합니다.
    S3를 위한 사용자이기 때문에 AmazonS3FullAccess 권한을 부여합니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_permision.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_permision.png)

  - 사용자 추가 전 검토

    설정한 부분들을 검토하고, 🙏사용자 만들기 버튼을 클릭합니다.

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_review.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_review.png)

  - 키 확인

    사용자가 성공적으로 추가되었습니다.
    이 화면에서 **엑세스 키 ID**, **비밀 엑세스 키**를 복사해놓는것이 중요합니다.
    😱 절때 외부에 노출이 되면 안됩니다!!

    ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_key.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/iam_key.png)

- 20. AWS SDK 설치 및 설정

  **SDK**는 Software Development Kit의 약자로
  프로그래밍을 돕는 라이브러리라고 생각하시면 됩니다.
  AWS SDK를 이용하시면 개발과 연동해서 AWS를 사용할 수 있게됩니다.

  - SDK 다운로드

    - **[코드스니펫] 윈도우 URL**

      ```bash
      https://awscli.amazonaws.com/AWSCLIV2.msi
      ```

    - **[코드스니펫] 맥 URL**

      ```jsx
      https://awscli.amazonaws.com/AWSCLIV2.pkg
      ```

  - SDK 사용하기

    - **[코드스니펫] 설치 후 확인**

      ```jsx
      aws --version
      ```

    - **[코드스니펫] 설정**

      ```jsx
      aws configure
      ```

- 21. SDK를 이용한 S3 파일업로드

  자! 이제 SDK를 설정까지 했으니 컴퓨터에 있는 파일을 S3에 업로드 해볼까요
  걱정하지 마세요 자세한 설명을 사이트에서 참조 할수 있습니다.
  🙏 그럼 SDK를 통해 업로드를 해볼께요

  - **[코드스니펫] 복사 명령어 설명**

    ```jsx
    https://docs.aws.amazon.com/cli/latest/reference/s3/cp.html
    ```

  - **[코드스니펫] 업로드**

    ```bash
    aws s3 cp {파일명} s3://{버킷이름} --acl public-read
    ```

## 05. **[한 걸음 더** 🏃**]** 프로그램 언어와 연동

---

**한 걸음 더** 부분은 실무와 좀더 가까운 부분을 다뤄봅니다.

- 22. S3 파이썬 연동 - Flask를 사용하여 S3 업로드 웹페이지 구현

  AWS 서비스의 모든 제품들은 SDK 라이브러리를 거의 모든 언어에 제공하기
  때문에 개발언어와 연동해서 사용합니다.

  예제는 파이썬을 다루었지만 사용하시는 모든 언어에 비슷하게 사용하실 수
  있습니다.

  - **[코드스니펫] index.html**

    ```jsx
    <!Doctype html>
    <html lang="ko">

    <head>
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css"
              integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm"
              crossorigin="anonymous">

        <!-- JS -->
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js"
                integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q"
                crossorigin="anonymous"></script>

        <!-- 구글폰트 -->
        <link href="https://fonts.googleapis.com/css?family=Stylish&display=swap" rel="stylesheet">

        <title>핵심 쏙쏙 AWS</title>

        <!-- style -->
        <style type="text/css">
            * {
                font-family: 'Stylish', sans-serif;
            }

            .wrap {
                width: 900px;
                margin: auto;
            }

            .comment {
                color: blue;
                font-weight: bold;
            }

            #post-box {
                width: 500px;
                margin: 20px auto;
                padding: 50px;
                border: black solid;
                border-radius: 5px;
            }
        </style>
        <script>
            function save() {
                var form_data = new FormData($('#upload-file')[0]);
                $.ajax({
                    type: 'POST',
                    url: '/fileupload',
                    data: form_data,
                    processData: false,
                    contentType: false,
                    success: function (data) {
                        alert("파일이 업로드 되었습니다!!");
                    },
                });
            }
        </script>

    </head>

    <body>
    <div class="wrap">
        <div class="jumbotron">
            <h1 class="display-4">나홀로 이미지 메모장!</h1>
            <p class="lead">중요한 이미지를 저장해두고, 나중에 볼 수 있는 공간입니다</p>
            <hr class="my-4">
        </div>
        <div id="post-box" class="form-post">
            <div>
                <div class="form-group">
                    <form id="upload-file">
                        <label for="post-url">이미지 파일</label>
                        <input type="file" name="file"/>
                    </form>
                </div>
                <button type="button" class="btn btn-primary" onclick="save()">저장</button>
            </div>
        </div>
        <div id="cards-box" class="card-columns">
            <div class="card">
                <img class="card-img-top"
                     src="https://www.eurail.com/content/dam/images/eurail/Italy%20OCP%20Promo%20Block.adaptive.767.1535627244182.jpg"
                     alt="Card image cap">
                <div class="card-body">
                    <a href="#" class="card-title">여기 기사 제목이 들어가죠</a>
                    <p class="card-text">기사의 요약 내용이 들어갑니다. 동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라만세 무궁화 삼천리 화려강산...</p>
                    <p class="card-text comment">여기에 코멘트가 들어갑니다.</p>
                </div>
            </div>
            <div class="card">
                <img class="card-img-top"
                     src="https://www.eurail.com/content/dam/images/eurail/Italy%20OCP%20Promo%20Block.adaptive.767.1535627244182.jpg"
                     alt="Card image cap">
                <div class="card-body">
                    <a href="#" class="card-title">여기 기사 제목이 들어가죠</a>
                    <p class="card-text">기사의 요약 내용이 들어갑니다. 동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라만세 무궁화 삼천리 화려강산...</p>
                    <p class="card-text comment">여기에 코멘트가 들어갑니다.</p>
                </div>
            </div>
            <div class="card">
                <img class="card-img-top"
                     src="https://www.eurail.com/content/dam/images/eurail/Italy%20OCP%20Promo%20Block.adaptive.767.1535627244182.jpg"
                     alt="Card image cap">
                <div class="card-body">
                    <a href="#" class="card-title">여기 기사 제목이 들어가죠</a>
                    <p class="card-text">기사의 요약 내용이 들어갑니다. 동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라만세 무궁화 삼천리 화려강산...</p>
                    <p class="card-text comment">여기에 코멘트가 들어갑니다.</p>
                </div>
            </div>
            <div class="card">
                <img class="card-img-top"
                     src="https://www.eurail.com/content/dam/images/eurail/Italy%20OCP%20Promo%20Block.adaptive.767.1535627244182.jpg"
                     alt="Card image cap">
                <div class="card-body">
                    <a href="#" class="card-title">여기 기사 제목이 들어가죠</a>
                    <p class="card-text">기사의 요약 내용이 들어갑니다. 동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라만세 무궁화 삼천리 화려강산...</p>
                    <p class="card-text comment">여기에 코멘트가 들어갑니다.</p>
                </div>
            </div>
            <div class="card">
                <img class="card-img-top"
                     src="https://www.eurail.com/content/dam/images/eurail/Italy%20OCP%20Promo%20Block.adaptive.767.1535627244182.jpg"
                     alt="Card image cap">
                <div class="card-body">
                    <a href="#" class="card-title">여기 기사 제목이 들어가죠</a>
                    <p class="card-text">기사의 요약 내용이 들어갑니다. 동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라만세 무궁화 삼천리 화려강산...</p>
                    <p class="card-text comment">여기에 코멘트가 들어갑니다.</p>
                </div>
            </div>
            <div class="card">
                <img class="card-img-top"
                     src="https://www.eurail.com/content/dam/images/eurail/Italy%20OCP%20Promo%20Block.adaptive.767.1535627244182.jpg"
                     alt="Card image cap">
                <div class="card-body">
                    <a href="#" class="card-title">여기 기사 제목이 들어가죠</a>
                    <p class="card-text">기사의 요약 내용이 들어갑니다. 동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리나라만세 무궁화 삼천리 화려강산...</p>
                    <p class="card-text comment">여기에 코멘트가 들어갑니다.</p>
                </div>
            </div>
        </div>
    </div>
    </body>

    </html>
    ```

  - **[코드스니펫] app.py**

    **boto3** 라이브러리를 활용하면 AWS와 연동이 가능해요

    ```jsx
    import boto3
    from flask import Flask, render_template, request, jsonify

    app = Flask(__name__)

    @app.route('/')
    def main():
        return render_template('index.html')

    @app.route('/fileupload', methods=['POST'])
    def file_upload():
        file = request.files['file']
        s3 = boto3.client('s3')
        s3.put_object(
            ACL="public-read",
            Bucket="{버킷이름}",
            Body=file,
            Key=file.filename,
            ContentType=file.content_type)
        return jsonify({'result': 'success'})

    if __name__ == '__main__':
        app.run()
    ```

  - Flask + 파이참을 이용한 테스트

    1. 프로젝트 구성

       ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.04.05.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.04.05.png)

    2. 테스트

       ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.04.51.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__9.04.51.png)

## 06. **S3** 정적호스팅 기능을 이용하여 외부에 공개하기

---

S3 기능에는 단순히 저장하는 기능 이외에 정적 웹 사이트 호스팅 기능이 있어요.
이 기능을 이용해서 프론트 페이지를 구성해 보도록 할게요.

- 23. 속성 > 정적웹호스팅

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/option.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/option.png)

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/hosting.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/hosting.png)

- 24. 편집 > 활성화 시키기

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/static.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/static.png)

  - 호스팅 유형
    - 정적 웹 사이트 호스팅 - 저장된 파일을 웹사이트 처럼 만들어줍니다.
  - 인덱스 문서 - 기본 페이지를 설정합니다. 대부분 index.html 입니다.
  - 오류 문서 - 에러가 발생했을 때 해당 문서로 이동합니다.
    - 단순 HTML 구성일 때는 개발 환경에 맞게 구성합니다.
    - React, Vuejs 구성일 때는 index.html을 입력합니다.

- 25. 정적 웹 사이트 호스팅 확인

  기능이 활성화가 되었고,
  버킷 웹 사이트 엔드 포인트가 생겼어요~
  엔드 포인트 URL을 이용하면 브라우저에서 사이트를 볼 수 있어요~
  현재 index.html 파일을 업로드하지 않았기 때문에 403에러 페이지를 볼 수 있어요.

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/site.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/site.png)

  ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/403.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/403.png)

- 26. index.html 파일 업로드 & 확인

  그럼 index.html 파일을 업로드한 후 확인해보도록 할게요
  업로드 이후 파일의 권한을 퍼블릭하게 변경하셔야 해요~

  - 파일

    [index.html](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/index.html)

  - 결과

    - 웹사이트가 보여요!!

      ![AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__8.52.23.png](AWS%20BASIC%20Course%20WEEK%201%20a5b6f47dbcbc444f8f827a8003ec3ee4/_2021-04-08__8.52.23.png)

## 07. **S3 비용 계산**

---

AWS 의 모든 서비스는 비용 계산이 복잡해요.
S3는 저장된 파일의 용량과 파일을 호출하는 트래픽에 따라 비용이 부과되요.

🔥 비용계산을 대략적으로 해놓지 않으면,
생각보다 많이 부과된 비용에 당황하실꺼에요

- **[코드스니펫] 참고 문서**

  ```jsx
  https://calculator.aws/#/createCalculator/S3
  ```

## 08. 정리

---

☁️ AWS는 클라우드 서비스 중에 제일 잘나가는 서비스입니다.

☁️ AWS가 제공하는 서비스들이 엄청 많기 때문에 잘 사용하기 위해서는
먼저 잘 사용하고 있는 회사들이 어떻게 사용하고 있는지 잘 봐야 합니다.

☁️ S3는 파일을 저장하는 서비스입니다.

☁️ IAM은 AWS의 내의 계정을 관리하는 서비스입니다.

☁️ SDK는 AWS의 서비스를 좀 더 프로그래밍 하게 사용하게 해주는 라이브러리입니다.

☁️ S3 의 정적 호스팅 기능을 이용하면 웹서버 없이도 정적페이지를 웹사이트로 만들 수 있습니다.
