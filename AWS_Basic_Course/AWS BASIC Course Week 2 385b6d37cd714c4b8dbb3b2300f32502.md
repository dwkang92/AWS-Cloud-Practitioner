# AWS BASIC Course Week 2

## **01. 왜 프론트와 백엔드를 분리하는가?**

---

2주차에서는 AWS에 대해서 좀 더 깊이있게 들어가 보도록 할께요.
1주차때 AWS를 더 잘 활용하기 위해서는 AWS를 사용하는 회사들이 어떻게 사용하고 
있는지 눈여겨 봐야 된다는 부분 잊지 않으셨죠 ❓

또한, AWS를 좀 더 잘쓰려면 AWS가 만들어진 사상을 이해하면 좀 더 도움이 됩니다.
이 사상을 이해하기위해 아키텍쳐 얘기를 조금만 해보도록 할께요.

- 1) Monolithic vs MSA

    ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/archi.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/archi.png)

    - Monolithic
        - 프로젝트에 관한 모든 부분을 하나의 서버에 배치하는 방법입니다.
    - MSA
        - 가장 간단하게는 프론트, 백엔드를 물리적으로 다른 서버에 배치하는 방법입니다.
    - AWS의 사상

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/vogel.jpg](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/vogel.jpg)

        아마존닷컴은 10년전 (1995년) 웹 서버와 데이터베이스 백엔드를 가지는 모놀리식(Monolithic) 애플리케이션으로 시작하였습니다.
         
        5년전(2001년) 아마존은 주요한 아키텍쳐 변화가 있었는데 2 티어(tier)기반에서 
        서로 다른 애플리케이션 기능을 제공하는 분산 서비스 플랫폼으로 변화하였습니다. 

        여러분이 지금 Amazon.com의 첫화면에 들어온다면, 
        그 페이지를 생성하기 위해 100여개가 넘는 서비스를 호출하여 만들고 있습니다.

        - 위의 인터뷰는 아마존의 CTO 버너 보겔스의 인터뷰 내용입니다.
        AWS는 아마존이 사용하던 인프라를 그대로 서비스로 만들어 놓은 것입니다.
        그렇기에 아마존 닷컴의 아키텍처와 같이 블록처럼 조립해서 쓸 수 있게 
        서비스를 구성해 놓았습니다.
        - 🔥 AWS를 사용한다는 것은 단순히 클라우드 사용을 넘어 
        개발 방식도 클라우드 철학에 맞게 변해야 한다는 것을 알 수 있습니다.
        - 결론은 분리해야 할 부분은 무조건 분리하는 것입니다.
        - 예시

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/services.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/services.png)

## **02.** 프론트 구성해보기

---

CloudFront는 CDN 서비스와 유사한 기능을 합니다.
S3를 사용해서 [www.example.com](http://www.example.com) 도메인으로 글로벌 서비스를 해야하는 상황입니다.
어떻게 해야할까요?

S3의 버킷은 생성할때 리전이 정해져있습니다.
서울리전에 있는 버킷을 호스팅 기능을 이용해서 미국에 서비스 한다고 하면 
엄청나게 사이트가 늦게 뜰꺼에요~ 

그러면 똑같은 S3 버킷을 서비스하는 나라의 가까운 리전 마다 생성해줘야 할까요 ❓
그럼 비용이 더 들겠죠 좋은 방법이 있어요!! CloudFront를 사용하는 거에요 😀

- **[코드스니펫] 참고 문서**

    ```jsx
    https://docs.aws.amazon.com/cloudfront/?id=docs_gateway
    ```

- 2) **CloudFront** CDN 기능 이해하기

    ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/cdn.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/cdn.png)

- 3) **CloudFront** 만들기
    1. 메뉴 찾기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__8.42.08.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__8.42.08.png)

    2. 메인구경하기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__8.53.56.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__8.53.56.png)

    3. 배포 생성하기

        Step 1 에서는 CloudFront를 사용하면 좋아지는 부분이 설명되어 있어요.

        Step2 에서는 옵션들을 설정하면 바로 생성을 할 수 있습니다.
        옵션이 무수히 많기 때문에 Origin Domain Name만 설정하고 생성할께요.
        그리고 필요한 부분은 생성후 수정이 가능합니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__8.55.08.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__8.55.08.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.00.52.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.00.52.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.07.13.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.07.13.png)

    4. 생성 확인

        생성후 리스트 에서 확인할 수 있어요.

        **ID**는 자동으로 부여되는 값이구요. 나중에 배포할때 사용할꺼에요.
        **Domain name**은 URL이고 브라우저에서 호출할수 있어요.
        **Origin**은 이전에 생성한 S3 URL 이에요.
        **Status**가 In Progress인 이유는 그림에서 봤던 edge location이라는 곳에 배포중이기 때문이에요 배포가 다되면 Deployed 상태가 됩니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.10.11.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.10.11.png)

    5. CloudFront URL을 이용하여 브라우저에서 호출

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.16.28.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.16.28.png)

    6. 설정 확인

        리스트 페이지에서 선택하면 현재 설정된 옵션들을 볼 수 있어요.
        Default Root Object라는 부분이 비어 있는것을 볼 수 있어요.
        이 부분을 수정해 주어야 S3에 업로드한 파일인 index.html을 인식할 수 있어요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.24.06.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.24.06.png)

    7. 설정 변경

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.28.27.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-29__9.28.27.png)

    8. 페이지 확인

        index.html 파일이 보여요!!

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-10__6.44.23.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-10__6.44.23.png)

## 03. GIT 연습

---

GIT은 형상관리 툴이라고 해요. 간단하게는 소스저장소 에요.
예전에는 SVN, CVS를 많이 썻었는데 요즘은 GIT으로 거의 천하통일 되었어요.

🔥 처음 사용해보면 어렵지만 내가 만든 소스를 날려버리지 않기 위해 
꼭!! 기본기능은 알고 있으면 좋습니다. 

- 4) Git & Github이란
    - 버전 관리가 안되어 힘든 경험 다들 있지 않으신가요? 아래처럼 말이죠!

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/Untitled.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/Untitled.png)

    - **Git** 은 작업 기록을 남기고 이력을 **추적**해서 코드를 손쉽게 관리하도록 도와줍니다. 버전 관리도 매우 간편합니다.
        - 어떤 버전부터 버그가 생긴 걸까? 어떤 내용이 변경되었는지 한 눈에 보고 싶다!
        - 여러 사람 / 컴퓨터에서 코드 작업을 동시에 하고 있다면 변경된 내역을 어떻게 합칠까?
        - 이력 추적하기 예시 👉[헌법 개정안 비교](https://github.com/puzzlet/constitution-kr/pull/1/files)
    - **Github** 은  작업 기록과 파일을 저장하는 Git 원격 저장소를 지원해주는 사이트입니다.
        - 그 외에도 최근 트렌드인 오픈소스 찾기, 프로젝트 issue 관리처럼 다양한 부가 기능을 제공하고 있어요. (비슷한 곳으로는 Gitlab, bitbucket 등이 있습니다.)
- 5) Git의 commit / pull / push 란

    혼자 개발 할 때에도 git을 쓰면 무척 편리합니다. 
    만약 작성 중이던 코드가 한참 잘못돼서 일주일 전 버전으로 돌리고 싶을 때, git이 없다면 난감하겠죠?

    - 우리는 앞으로 주로 '내 컴퓨터(로컬 저장소)에 작업 내역을 반영하고, 원격 저장소(예. Github)에 작업 내역을 올리기' 를 많이 사용해볼거에요. 이제 Git 에서 가장 많이 쓰이는 commit / pull / push 를 살펴볼게요!

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/Untitled%201.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/Untitled%201.png)

    1. 내 로컬 저장소에 작업 내역을 반영하고 → `commit`
        - commit 앞에 파일을 새로 추적하는  `add`  과정이 있습니다. 우리가 쓰는 Github Desktop  처럼 GUI 툴을 사용하게 되면, 보통 commit 작업에 포함되어 있습니다.
    2. 원격 저장소에 작업 내역을 업로드하는 것 → `push`
        - 보통은 여러 사용자가 올린 것이라도 작업 내역에 겹치는 게 없다면 자동으로 합쳐줍니다.
        - 여러 사용자가 하나의 파일의 동일한 부분을 고쳤다면, 어떤 부분을 어떻게 반영해야할까요? Git이 충돌(conflict)났다고 알려주고 사용자에게 직접 수정하라고 알려줍니다.
    3. 원격 저장소 작업 내역을 내 로컬 저장소로 가져오는 것 → `pull`
        - 다른 사람의 작업내역을 가져오거나, 다른 컴퓨터에서 작업한 내용을 가져올 수 있습니다.
        - 보통 나의 작업 내역을 `commit` 하고 , `pull` 해오면 좋습니다. 그렇지 않으면 다른 사람의 작업 내역으로 내 작업 내역이 덮어쓰기가 되어버립니다.
            - 임시로 파일의 작업 내역을 보관해두는  `stash` 도 있습니다. 하지만 우리는 처음 배우니까 요건 나중에 git에 익숙해지면 써 보세요!
- 6) GitHub Action 이란?

    Git Action은 Github에서 제공하는 배포 서비스에요.
    GIthub가 MS에 인수되면서 기존의 소스저장소의 기능에서 DevOps플랫폼으로
    으로 발전하고 있어요.  
    비슷한 서비스로는 Gitlab, Bitbucket등이 있어요.

    🔥  요즘 트랜드는 CI/CD의 통합입니다. 소스저장소와 배포시스템을 통합하는 것입니다.
    아키텍처의 변화로 작아진 어플리케이션들을 부담없이 자주 배포하기 위함이죠.

    ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/vmeforsb7sbldnxw0v58.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/vmeforsb7sbldnxw0v58.png)

    - GitHub Action은 간단하게는 서버에 소스를 배포하는 서비스 입니다.
    - 사용법

        GitHub 소스 리파지토리에 .github/workflows/main.yml
        파일만 추가하시면 되요 

        - **[코드스니펫] GitAction 문서**

            ```bash
            https://docs.github.com/en/actions
            ```

## 04. **[한 걸음 더** 🏃**]** GitHub Action을 이용한 자동 배포 만들기

---

- 7) IAM 권한 추가
    1. IAM > 사용자 > 클릭

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/iam.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/iam.png)

    2. CloudFront 권한 추가

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/add.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/add.png)

    3. 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/cloudFront.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/cloudFront.png)

- 8) GitHub Action을 이용한 배포준비
    1. 리파지토리 만들기 & 파이참 연동
    2. 문서보기
        - **[코드스니펫] GitAction CloudFront 문서**

            ```bash
            https://github.com/marketplace?type=actions&query=cloudfront
            ```

    3. 프론트 코드를 Github에 업로드
        - **[코드스니펫]** 사용할 [💻 코드 `index.html`]

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

                <title>스파르타코딩클럽 | 나홀로 메모장</title>

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
                        alert("파일이 업로드 되었습니다!!");
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

    4. 배포 스크립트 추가
        - **[코드스니펫]** 사용할 [💻 코드 `./github/workflows/main.yml`]

            ```yaml
            name: my-front
            on:
              push:
                branches:
                  - main
            jobs:
              build:
                runs-on: ubuntu-latest
                env:
                  AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
                  AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
                  AWS_REGION: 'ap-northeast-2'

                steps:
                  - name: Checkout source code.
                    uses: actions/checkout@master

                  - name: Upload binary to S3 bucket
                    uses: jakejarvis/s3-sync-action@master
                    with:
                      args: --acl public-read --exclude '*' --include 'index.html'
                    env:
                      AWS_S3_BUCKET: ${{ secrets.BUCKET_NAME }}

                  - name: Invalidate cache CloudFront
                    uses: chetan/invalidate-cloudfront-action@master
                    env:
                      DISTRIBUTION: ${{ secrets.DISTRIBUTION_ID }}
                      PATHS: '/index.html'
                    continue-on-error: true
            ```

    5. Github의 리파지토리에서 Settings로 이동

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.40.46.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.40.46.png)

    6. AWS 연동 준비 - Settings > Secrets 

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.42.37.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.42.37.png)

    7. AWS Key 저장
        - DISTRIBUTION_ID, BUCKET_NAME 추가

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/22.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/22.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.45.49.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.45.49.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__8.18.17.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__8.18.17.png)

    8. 소스추가 PUSH

        ```yaml
        {프로젝트 폴더}/.github/workflows/main.yml
        ```

    9. 배포 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/deploy.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/deploy.png)

## **05. 네트워크 1 - VPC, 서브넷, 라우팅 테이블,** 인터넷 게이트웨이

---

클라우드를 사용하면서 네트워크 지식의 중요성이 예전보다는 중요하지 않게되었습니다.
하지만 최소한 클라우드에서 제공하는 부분은 알아야 인프라를 구성할 수 있습니다.

🔥  당장은 개발과 상관없을 수 있지만
      서비스가 확장되고 인프라가 복잡해질수록 꼭 알아야 하는 지식이에요.

- **[코드스니펫] VPC 문서**

    ```jsx
    https://docs.aws.amazon.com/ko_kr/vpc/
    ```

- 9) VPC 알아보기

    AWS 클라우드내의 네트워크로, 사용자가 논리적으로 네트워크를 만들어서
    서비스에 적용할 수 있습니다. 개념이 조금 어렵죠 😅

    1. 메뉴 찾기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__12.54.35.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__12.54.35.png)

    2. 메인 구경하기

        **IPV4 CIDR**은 IP의 범위를 지정하는 방법입니다.
        예를 들어 172.32.0.0/16 이라고 하면 IP의 범위가
        172.32.0.0 ~ 172.32.255.255 지정되게 됩니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__12.55.28.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__12.55.28.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.15.49.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.15.49.png)

    3. 간단한 사용 예시

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.09.22.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.09.22.png)

- 10) 서브넷
    - 서브넷은 연결되는 서버 컴퓨팅 자원들에 내부 IP를 할당합니다.
    - 메인 구경하기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.20.28.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.20.28.png)

- 11) 라우팅 테이블
    - 연결된 서브넷들을 라우팅 합니다.
    - 메인 구경하기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.44.00.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.44.00.png)

    - 서브넷과 연결되어 있습니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.42.27.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__1.42.27.png)

- 12) 인터넷 게이트웨이
    - 인터넷과 VPC를 연결합니다. 인터넷 게이트웨이가 연결된 VPC 만이 외부와 통신이 가능합니다.
    - 메인 구경하기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__2.03.55.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-03__2.03.55.png)

## 06. 네트워크 2 -  보안그룹, 탄력적 IP

---

보안그룹은 이제부터 계속적으로 볼수 있어요. 그러니 꼭 알아둬야겠죠.
탄력적 IP는 말그대로 IP 인데요. 고정 IP입니다.

🔥  보안그룹과 탄력적 IP는 꼭 알아야 해요.

- 13) 보안그룹
    - 보안그룹은 방화벽과 비슷한 역할을 합니다. 보안그룹과 연결된 인스턴스들의 접근을 제안합니다.
    - 메인 구경하기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__10.25.51.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__10.25.51.png)

- 14) 탄력적 IP
    - 인스턴스에 고정된 IP를 부여할 수 있게 해줍니다.
    - 예시
        1. 생성된 EC2 인스턴스 IP 확인 

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/1.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/1.png)

        2. 인스턴스 중지 & 시작

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/2.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/2.png)

        3. IP 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/3.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/3.png)

## 07. 백엔드 구성해보기 - EC2

---

**EC2**는 AWS의 가장 기본적인 서비스에요.
하나의 서버 컴퓨터라고 보시면 되고, 서버 컴퓨터를 하나 빌려서 
프로그램들을 설치하고 사용하시면 됩니다.

🙏 그럼 차례대로 만들어볼께요

- **[코드스니펫] EC2 문서**

    ```jsx
    https://docs.aws.amazon.com/ec2/?id=docs_gateway
    ```

- 15) EC2 생성하기
    1. 메뉴 찾기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ec2.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ec2.png)

    2. 메인 구경

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ec2_main.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ec2_main.png)

    3. 생성된 인스턴스 보기

        인스턴스 페이지에서 생성된 인스턴스 리스트를 볼수있어요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ec2_instance.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ec2_instance.png)

    4. 인스턴스 만들기

        인스턴스 시작 버튼을 클릭하면 인스턴스 생성 화면을 볼수 있어요.
        인스턴스 생성 첫단계는 AMI 선택이에요.

        AMI는 인스턴스에 설치할 OS 이미지라고 생각하시면 되요.
        PC, 노트북을 사면 OS를 설치해야 하듯이 EC2를 생성하기 위해 OS를 선택해야 해요.

        우리는 Ubuntu Server 18.04 이미지를 선택하도록 할께요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/AIM.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/AIM.png)

    5. 인스턴스 유형 선택

        **유형 선택**은 컴퓨터를 살때 스팩을 고르는 것과 같아요.
        CPU, 메모리 성능이 높아질수록 가격이 비싸진다고 생각하면 되요.

        우리는 t2.micro를 선택해 볼께요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/spec.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/spec.png)

    6. 인스턴스 구성

        **인스턴스 구성** 페이지에는 엄청나게 많은 옵션이 존재해요.
        하지만 처음부터 다 알고 있을 필요는 없어요.
        기능이 필요할때 찾아서 적용하면 되요.

        그럼 옵션들을 수정하지 않고 다음 단계를 진행해볼께요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/instance_detail.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/instance_detail.png)

    7. 스토리지 추가

        **스토리지**는 컴퓨터에 하드디스크를 추가하는 기능과 유사하다고 보시면 되요.
        디스크의 크기와 볼륨 유형을 지정할 수 있고, 
        새 볼륨을 추가할수도 있어요.

        이부분도 수정하지 않고 다음 단계로 넘어갈께요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/storage.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/storage.png)

    8. 태그추가

        **태그**는 생성한 인스턴스를 구별할때 쓰는 태그를 지정하는 기능이에요.
        인스턴스가 많아졌을때 태깅을 잘 해놓으면 유용하게 쓰일수 있어요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/tag.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/tag.png)

    9. 보안 그룹 구성

        **보안그룹**은 PC의 방화벽과 같은 기능을 합니다.
        해당 인스턴스에 들어오고 나가는 포트를 제어할 수 있어요.

        기본적으로 SSH 포트인 22번 포트는 열려있게 설정되어 있어요.
        왜냐하면 인스턴스가 생성된 후 SSH 를 이용해서 인스턴스에 
        접속할 예정이기 때문이죠.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/security.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/security.png)

    10. 검토

        오래 기다리셨어요.
        마지막 검토 페이지 입니다.
        지정한 옵션들을 검토한후 인스턴스를 생성하시면 됩니다.

        혹시 옵션을 잘못 지정했다고 해도 걱정하지 마세요.
        인스턴스가 생성된 후에도 수정이 가능합니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/review.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/review.png)

    11. 생성하기

        생성하기를 클릭하시면 키페어 관련 팝업 창이 보여요.
        키페어라는 것은 서버에 접속하기 위한 키라고 보시면 됩니다.
        그래서 키를 지정하고 나면 절대 잊어버리시면 안되요!!

        기존의 키페어가 있으시면 사용하시면 되고, 없으시면 새 키 페어 생성을 하셔야 해요.
        이름을 적고 다운로드 하시면 .pem 파일이 다운로드 됩니다.
        그리고 인스턴스 시작을 하시면 되요. 

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__7.54.05.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__7.54.05.png)

    12. 드디어 시작

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__7.54.47.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__7.54.47.png)

- 16) EC2 접속하기

    인스턴스가 생성되었으니 접속을 해서 사용해볼께요.
    리눅스라 조금 어려울 수도 있지만 걱정하지 마세요.

    1. IP 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.04.34.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.04.34.png)

    2. SSH 를 이용하여 인스턴스에 접속
        - 맥
            - 방금 받은 내 Keypair의 접근 권한을 바꿔주기

                ```bash
                sudo chmod 400 받은키페어를끌어다놓기 
                ```

            - 접속하기

                ```bash
                ssh -i 받은키페어를끌어다놓기 ubuntu@퍼블릭 IPv4 주소
                ```

                예) 아래와 비슷한 생김새!

                ```bash
                ssh -i /path/my-key-pair.pem ubuntu@13.125.251.58
                ```

        - 윈도우
            - 윈도우 10은 SSH 를 실치 해주시고, 이하버전은 git bash라는 프로그램을 이용합니다.
            - 접속하기

                ```bash
                ssh -i 받은키페어를끌어다놓기 ubuntu@AWS에적힌내아이피
                ```

                예) 아래와 비슷한 생김새!

                ```bash
                ssh -i /path/my-key-pair.pem ubuntu@13.125.251.58
                ```

    3. 접속 확인
        - 최초 접속시 fingerprint를 확인합니다. yes 엔터 하시면 되요.

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.23.45.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.23.45.png)

        - 정상 접속 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.26.00.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.26.00.png)

    4. 리눅스 명령어 연습

        ls: 내 위치의 모든 파일을 보여준다.

        pwd: 내 위치(폴더의 경로)를 알려준다.

        mkdir: 내 위치 아래에 폴더를 하나 만든다.

        cd [갈 곳]: 나를 [갈 곳] 폴더로 이동시킨다.

        cd .. : 나를 상위 폴더로 이동시킨다.

        cp -r [복사할 것] [붙여넣기 할 것]: 복사 붙여넣기

        rm -rf [지울 것]: 강제로 지우기. 이 명령어로 지우면 복구가 안되니 조심하세요!

        sudo [실행 할 명령어]: 명령어를 관리자 권한으로 실행한다.
        sudo su: 관리가 권한으로 들어간다. (나올때는 exit으로 나옴)

        조금만 연습하다 보면 적응될꺼에요 😀

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.28.42.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__8.28.42.png)

- 17) EC2에 파이썬 배포하기
    1. 파이썬 설정

        ```bash
        # python 이라는 명령어로 3 버전 이상을 실행하도록 하는 명령어입니다.
        sudo update-alternatives --install /usr/bin/python python /usr/bin/python3 10
        ```

    2. 리눅스 패키지 설치

        ```bash
        # pip3 설치
        sudo apt-get update
        sudo apt-get install -y python3-pip

        # 버전 확인
        pip3 --version

        # pip3 대신 pip 라고 입력하기 위한 명령어
        # 아래 명령어를 입력하면 pip 라고 쳐도 pip3를 작동시킬 수 있습니다.
        sudo update-alternatives --install /usr/bin/pip pip /usr/bin/pip3 1

        # 파이썬 개발에 필요한 라이브러리 설치
        pip install flask boto3 flask-cors
        ```

    3. git 연동
        - git 체크

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.32.37.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.32.37.png)

        - git 연동
            - git 저장소 사용

                ```bash
                # git 저장소 url
                https://github.com/uphiller/allaboutaws-backend
                ```

            - 소스 클론

                ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.35.17.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.35.17.png)

            - 폴더 확인 & 파이썬 파일 실행

                ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.36.36.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.36.36.png)

            - 백그라운드 실행

                ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.37.32.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__7.37.32.png)

    4. 포트 열기
        - 보안 그룹 찾기 & 클릭

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__9.14.40.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__9.14.40.png)

        - 인바운드 규칙 확인 & 인바운드 규칙 편집 클릭

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__9.17.23.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-30__9.17.23.png)

        - 5000번 포트 추가

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/sg_edit.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/sg_edit.png)

        - 포트 추가 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/sg_confirm.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/sg_confirm.png)

    5. 브라우저에서 확인

        ```bash
        http://[내 EC2 퍼블릭 IP]:5000/
        ```

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.31.07.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.31.07.png)

## 08. 백엔드 구성해보기 - EC2 + ELB

---

**ELB**는 여러대의 EC2를 묶어서 사용하기 위한 서비스에요.
클라우드를 사용하지 않을때도 LB(로드발란서)를 구입해서 사용했어요.

- **[코드스니펫] EC2 + ELB 문서**

    ```jsx
    https://docs.aws.amazon.com/ec2/?id=docs_gateway
    ```

- 18) ELB 사용 장점
    - 서비스중에 EC2의 성능이 부족한 경우 인스턴스를 추가 할 수 있어요

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elbec2.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elbec2.png)

- 19) ELB 생성하기
    1. 메뉴 찾기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/loadb.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/loadb.png)

    2. 메인 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ELB.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/ELB.png)

    3. 생성하기 - HTTP HTTPS 선택

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb_type.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb_type.png)

    4. Load Balancer 구성

        **기본구성**에는 이름, 체계, ip 주소 유형이 있어요.
        **이름**은 규칙대로 정하시면 되요.
        **체계**에서 인터넷 경계는 외부의 접근을 허용한다라는 것이고요.
        내부는 외부와 상관없이 내부 서비스들 끼리 사용하겠다는 것입니다.
        **IP 주소 유형**은 ipv4를 유지하시면 되요.

        **리스너**에는 어떤 프로토콜을 사용하여 접근하게 할 것인지를 설정하면 되요.
        HTTP, HTTPS 중에 하나를 선택하시면 되요.

        **가용영역**은 1주차 처음부분에 배운 존을 지칭하는 단어입니다.
        여기서는 2개의 가용영역만 선택하면 됩니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb-1.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb-1.png)

    5. 보안설정구성

        보안 설정 구성으로 넘어가시면 경고문구가 하나 보여요.
        이 부분은 이전 페이지에서 리스너를  HTTPS로 선택하지 않아서 발생하는 현상이에요.
        외부로 허용된 로드밸런서기 때문에 좀 더 보안적으로 안전한 HTTPS를 
        사용하라는 경고입니다.

        👌하지만 지금은 테스트 하는중이기 때문에 괜찮아요

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/sc2.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/sc2.png)

    6. 보안 그룹 구성

        EC2에서 봤던 보안그룹이에요.
        새 보안 그룹 생성을 선택하고, 리스너로 선택했던 HTTP 80 포트가 
        추가 되었는지 확인합니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb3.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb3.png)

    7. 라우팅 구성

        라우팅 구성은 ELB에서 EC2로 연결되는 부분에 대해 설정하는 부분 이에요.

        **대상그룹**은 ELB에 EC2를 연결하기 위해서는 먼저 그룹을 만들어 놓고 
        그룹에 EC2를 추가하는 방식이에요. 그래서 대상그룹을 먼저 생성합니다.

        **대상 유형**에는 EC2를 대상으로 하기 때문에 인스턴스를 선택합니다.
        우리가 만든 EC2에서 사용할 포트는 5000번이기 때문에 
        **프로토콜**은 HTTP, **포트**는 5000을 선택해주시면 되요.

        **상태검사**는 연결된 EC2 인스턴스의 상태를 계속 검사해서 
        만약에 EC2에 문제가 있으면 해당 EC2에는 트래픽을 보내지 않습니다.
        보통 **헬스체크**라고 합니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb-4.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb-4.png)

    8. 대상등록

        현재 생성된 인스턴스 중에 ELB와 연결할 대상을 선택하는 부분이에요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb-5.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb-5.png)

    9. 등록된 항목에 추가

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb5-1.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb5-1.png)

    10. 검토

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-10__6.34.38.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-10__6.34.38.png)

    11. 생성확인 & DNS 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb_last.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/elb_last.png)

    12. 브라우저에서 접속해보기

        브라우저에서 호출해도 정상적인 화면이 보이지 않을 수가 있어요.
        ELB, EC2 가 연결되기 위해서는 조금 시간이 필요합니다.
        조금 기다리시다가 다시 해보면 정상적으로 화면이 보일거에요. 

        ```jsx
        http://[ELB DNS 이름]/
        ```

- 20) EC2 수동으로 추가하기

    EC2 하나를 더 추가하기 위한 가장 간단한 방법은
    이전에 작업했던것처럼 EC2를 만들어서 추가하는 것이에요.

    - 대상 그룹 메뉴 찾기 - EC2 메인화면 우측 메뉴에서 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/menu.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/menu.png)

    - 대상 그룹 리스트 확인 & 선택

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/group.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/group.png)

    - 인스턴스 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/add_instance.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/add_instance.png)

    - 추가

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/group_register.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/group_register.png)

- 21) EC2 자동으로 추가하기

    수동으로 EC2 추가 가능하지만 자동으로 되면 훨씬 편하겠죠!!

    - AMI 만들기

        EC2를 자동생성 해서 추가되게 만들려면 
        우리가 EC2 생성할때 지정한 이미지 처럼 베이스 이미지가 필요해요
        그래서 우리가 추가하고자 하는 EC2의 디스크를 이용해 
        베이스 이미지를 만들어 보도록 할께요

        1. 이미지 생성 실행

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.00.02.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.00.02.png)

        2. 이미지 생성 - 이미지명 입력 후 생성

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.03.30.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.03.30.png)

        3. 이미지 확인 - EC2 왼쪽 메뉴 > 이미지 > AMI

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.07.39.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.07.39.png)

    - Auto Scaling 시작구성 만들기
        1. 메인 구경 - EC2 왼쪽 메뉴 > Auto Scaling > 시작 구성

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.09.45.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.09.45.png)

        2. 시작 구성 생성 - 이름, AMI(나의 AMI - 내가 만든 AMI 선택), 인스턴스 유형

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.43.29.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.43.29.png)

        3. 보안그룹 - 기존의 EC2에서 사용하는 보안그룹 선택

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/333.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/333.png)

        4. 키페어 - 기존의 EC2에서 사용하는 키페어 선택

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.15.20.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.15.20.png)

        5. 생성 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.45.46.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.45.46.png)

    - Auto Scaling 그룹 만들기
        1. 메인 구경 - EC2 왼쪽 메뉴 > Auto Scaling > Auto Scaling 그룹

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.18.48.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.18.48.png)

        2. 시작 템플릿 또는 구성 선택 - 시작 구성으로 전환 클릭

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.25.37.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.25.37.png)

        3. 설정 구성

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.47.26.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.47.26.png)

        4. 고급 옵션 구성 - 기존 로드벨런서에 연결

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.11.49.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.11.49.png)

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.12.23.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.12.23.png)

        5. 그룹 크기 및 조정 정책 구성

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.34.39.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__6.34.39.png)

        6. 생성 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.57.33.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__8.57.33.png)

    - 인스턴스 헬스 체크 확인
        1. 대상 그룹 리스트 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.29.04.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.29.04.png)

        2. 인스턴스 정보 보기

            추가된 인스턴스가  unhealthy 상태이기 때문에 인스턴스 내부에 
            접속해서 원인을 찾아봐야 해요.

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.27.18.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.27.18.png)

        3. 인스턴스로 접속

            ```bash
            $ ps -ef | grep python
            ```

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__10.10.05.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-03-31__10.10.05.png)

        4. 파이썬 실행

            ```bash
            $ nohup python app.py &
            ```

        5. 상태 확인

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.31.10.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__7.31.10.png)

## 09. **ElasticBeanstalk** 를 이용하여 좀 더 편하게 관리하기

---

ELB + Auto Scaling + EC2 한번에 관리할 수 있는 서비스에요.
이전 실습에서 보았듯이 따로 관리 하면 설정 값도 많고 무척 까다로워요.

그래서 AWS 에서는 통합해서 관리할수 있는 서비스인 ElasticBeanstalk 를 제공하고 있어요.
구글의 앱엔진이라는 서비스와 비슷하게 환경에는 신경쓸 필요없이 간단한 옵션만 조절하고, 어플리케이션만 배포하면 되는 형태입니다.  
🍯  ElasticBeanstalk라는 이름이 너무 길어서 보통 **EB**라고 불러요.

- **[코드스니펫] EB 참고 문서**

    ```jsx
    https://docs.aws.amazon.com/elastic-beanstalk/?id=docs_gateway
    ```

- 23) **EB** 생성하기
    1. 메뉴찾기

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.35.48.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.35.48.png)

    2. 메인확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.52.37.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.52.37.png)

    3. 애플리케이션 이름

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.53.25.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.53.25.png)

    4. 플랫폼 선택

        플랫폼은 구축 하려는 서비스의 언어를 선택하시면 되요.
        예제로 Python 을 사용하고 있기 때문에 선택하고 생성합니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.54.52.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.54.52.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.55.47.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.55.47.png)

    5. 생성확인

        생성하는데 시간이 좀 걸려요
        ELB, EC2, Auto Scaling 을 같이 생성하기 때문이죠.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.14.12.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.14.12.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.58.29.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__7.58.29.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.16.00.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.16.00.png)

    6. 브라우저에서 접속 - 제공된 URL을 이용하여 접속해 봅니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.16.24.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.16.24.png)

- 24) 구성 변경해보기
    - 메인 구경하기 - 왼쪽 메뉴 > Pythonapp-env > 구성

        **소프트웨어 -** 운영환경
        **인스턴스 -** 인스턴스의 볼륨과 보안그룹
        **용량 -** 인스턴스 유형과 인스턴스 조절
        **로드밸런서 -** 로드밸런서에 관련된 설정
        **롤링 업데이트와 배포 -** 배포에 관련된 설정
        **보안 -** 키페어 설정
        **모니터링 -** 모니터링
        **알림 -** 알림설정
        **네트워크 -** 네트워크 설정
        **데이터베이스 -** 데이터베이스 연결

        옵션이 너~무 많아요!!
        하지만 중요한 옵션들만 알고 계시면 되고, 이외의 옵션들을 필요할때마다 
        찾아보시고 사용하시면 되요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__8.27.38.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__8.27.38.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__8.28.11.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-01__8.28.11.png)

    - 인스턴스 갯수 늘리기 - 용량 > 편집버튼 클릭

        인스턴스 최소, 최대 갯수를 조절 할 수 있어요.
        인스턴스를 임의로 2개로 만들려면 최소 2 로 저장하면 되요.

        2로 수정 하시고 아래쪽에 적용 버튼을 클릭합니다.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/size.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/size.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/saving.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/saving.png)

    - 확인

        인스턴스 갯수 확인을 위해서는 EC2 > 인스턴스 페이지로 이동해서 
        환경이름 Pythonapp-env 로 검색을 하면 2개의 인스턴스가 보여요.

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/instance.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/instance.png)

## 10. **[한 걸음 더** 🏃**]** GitHub Action을 이용한 자동 배포 만들기

---

- 25) IAM 권한 추가
    1. IAM > 사용자 > 클릭

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/iam%201.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/iam%201.png)

    2. CloudFront 권한 추가

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/add%201.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/add%201.png)

    3. 확인

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/confirm.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/confirm.png)

- 26) GitHub Action을 이용한 배포준비
    1. 벡엔드 코드를 Github에 업로드
        - [**코드스니펫]** `application.py`

            ```python
            import boto3
            from flask import Flask, render_template, request, jsonify
            from flask_cors import CORS
            import os

            application = Flask(__name__)
            cors = CORS(application, resources={r"/*": {"origins": "*"}})

            @application.route('/')
            def main():
                return render_template("index.html")

            @application.route('/fileupload', methods=['POST'])
            def file_upload():
                file = request.files['file']
                s3 = boto3.client('s3',
                                  aws_access_key_id=os.environ["AWS_ACCESS_KEY_ID"],
                                  aws_secret_access_key=os.environ["AWS_SECRET_ACCESS_KEY"]
                                  )
                s3.put_object(
                    ACL="public-read",
                    Bucket=os.environ["BUCKET_NAME"],
                    Body=file,
                    Key=file.filename,
                    ContentType=file.content_type
                )
                return jsonify({'result': 'success'})

            if __name__ == '__main__':
                application.debug = True
                application.run()
            ```

        - 인증키 코드에 넣기

            1주차에 배웠던 SDK를 사용하는 방식과 조금 다른 방법을 사용해 볼께요.
            AWS 설정키를 소스에 넣어주면 되요.

            ```python
            s3 = boto3.client('s3',
                                  aws_access_key_id=os.environ["AWS_ACCESS_KEY_ID"],
                                  aws_secret_access_key=os.environ["AWS_SECRET_ACCESS_KEY"]
                                  )
            ```

        - 환경변수 관리

            AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY 과 같은 환경변수들은 
            코드에 그대로 넣지 않아요 보안상 위험하기 때문이죠
            그래서 서버에 환경변수로 설정하고 코드에 환경변수를 읽어들이는
            부분을 넣어요

            ```python
            import os

            os.environ["AWS_ACCESS_KEY_ID"]
            ```

        - CORS 허용

            CORS는 Cross-Origin Resource Sharing 이라는 의미에요,
            쉽게 설명해서 다른 도메인간에 API 통신을 허용한다는 뜻이에요.
            프론트백엔드 간의 도메인이 다르기 때문에 API 통신을 하려면
            CORS를 허용해 주어야 해요.

    2. Github의 리파지토리에서 Settings로 이동

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/github.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/github.png)

    3. AWS 연동 준비 - Settings > Secrets 

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/secrets.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/secrets.png)

    4. AWS Key 저장

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.45.49.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.45.49.png)

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.47.01.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-04__12.47.01.png)

    5. 배포 스크립트 추가
        - **[코드스니펫]** `./github/workflows/main.yml`

            ```yaml
            name: backend
            on:
              push:
                branches:
                  - main
            jobs:
              build:
                runs-on: ubuntu-latest

                steps:
                  - name: Checkout source code.
                    uses: actions/checkout@master

                  - name: Set up Python 3.8
                    uses: actions/setup-python@v1
                    with:
                      python-version: "3.8"

                  - name: Generate deployment package
                    run: zip -r deploy.zip . -x '*.git*'

                  - name: Get timestamp
                    uses: gerred/actions/current-time@master
                    id: current-time

                  - name: Run string replace
                    uses: frabert/replace-string-action@master
                    id: format-time
                    with:
                      pattern: '[:\.]+'
                      string: "${{ steps.current-time.outputs.time }}"
                      replace-with: '-'
                      flags: 'g'

                  - name: Deploy to EB
                    uses: einaregilsson/beanstalk-deploy@v16
                    with:
                      aws_access_key: ${{ secrets.AWS_ACCESS_KEY_ID }}
                      aws_secret_key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
                      application_name: python-app
                      environment_name: Pythonapp-env
                      version_label: "python-${{ steps.format-time.outputs.replaced }}"
                      region: ap-northeast-2
                      deployment_package: deploy.zip
            ```

    6. 벡엔드 코드를 Github에 업로드
        - EB에 환경변수 설정 - 구성 > 소프트웨어 수정 > 환경속성

            ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__8.41.35.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-11__8.41.35.png)

    7. **EB** 배포를 위한 준비

        EB 같이 클라우드에서 관리해주는 서비스들은 배포 규칙이 있어요.
        하지만 걱정하지 않으셔도 되요 모든 설명들은 도큐먼트에 잘 나와있으니까요.

        **파이썬 파일**은 EB에서 실행될 파이썬 파일명은 [application.py](http://application.py) 입니다.
        **라이브러리 모음**은 기존에 pip 로 라이브러리를 설치했던 부분을 EB에서는
         requirements.txt 파일을 만들어서 배포합니다.

        1. 필요한 파일 만들기
            - **[코드스니펫] 참고 문서**

                ```yaml
                https://docs.aws.amazon.com/ko_kr/elasticbeanstalk/latest/dg/create-deploy-python-flask.html
                ```

            - 파이썬 파일 - application.py
            - 라이브러리 모음 파일 - requirements.txt

                이 부분은 이전에 EC2에 배포할때는
                pip install flask boto3 라이브러리를 수동으로 설치해 주었지만,
                EB라는 서비스에서 라이브러리 설치도 알아서 해요
                그래서 설치할 라이브러리 목록을 만들고 리파지토리에 포함시켜주어야 해요.

                ```bash
                pip freeze > requirements.txt
                ```

                ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-09__3.44.23.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-09__3.44.23.png)

- 27) 프론트 & 백엔드 연동확인
    1. 프론트 코드 변경

        ```jsx
        function save() {
                    var form_data = new FormData($('#upload-file')[0]);
                    $.ajax({
                        type: 'POST',
                        url: '{EB URL}/fileupload',
                        data: form_data,
                        processData: false,
                        contentType: false,
                        success: function (data) {
                            alert("파일이 업로드 되었습니다!!");
                        },
                    });
                }
        ```

    2. 배포 & 테스트

        ![AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.47.10.png](AWS%20BASIC%20Course%20Week%202%20385b6d37cd714c4b8dbb3b2300f32502/_2021-04-08__8.47.10.png)

## 11. 정리

### 정리

☁️   AWS를 좀 더 잘 사용하기 위해서는 AWS의 사상을 이해해야 합니다.

☁️   개발환경이 Monolithic 에서  MSA 로 변화한 부분을 이해해야 합니다.

☁️   CloudFront를 이용하여 S3 에 저장된 파일들을 지역에 관계없이 빠르게 접근이 가능하도록 할  수 있습니다.

☁️   EC2 는 AWS가 제공하는 서비스 중에 가장 기본적인 컴퓨팅 서비스 입니다.

☁️   ELB는 기존의 LB기능과 비슷하며 EC2 리소스를 좀 더 효율적으로 사용하게 해줍니다.

☁️   Auto Scaling은 ELB와 EC2의 연결을 좀 더 효율적으로 관리할 수 있게 해줍니다. 

☁️   ElasticBeanstalk을 사용하면 인프라 관리의 어려움은 줄이고 좀 더 개발에 집중할 수 있는 환경을 만들수 있습니다.