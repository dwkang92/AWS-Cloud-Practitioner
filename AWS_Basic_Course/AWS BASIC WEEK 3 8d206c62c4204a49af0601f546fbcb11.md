# AWS BASIC WEEK 3

---

## **01. 클라우드 시대의 데이터베이스 관리**

클라우드의 시대 이전에는 DB의 역할이 매우 중요했어요.
왜냐하면 사용자 정보, 구매 정보 등을 저장하고 있는 데이터베이스가 
어플리케이션에서는 가장 중요한 부분이었거든요. 

하지만 아키텍처의 변화로 인해 데이터베이스가 가벼워지게 됩니다.
그리고 데이터베이스도 클라우드에서 **매니지드 되는** 서비스를 사용하면서 
데이터베이스를 직접 돌보아야 하는 일들이 조금 줄어 들게 됩니다.

🔥 그래서 좀 더 개발에 집중할 수 있게 됩니다.

- 01) 아키텍처의 변화

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/2tire.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/2tire.png)

                                                                                  **2Tier 아키텍처**

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/MSA.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/MSA.png)

                                                                                    **MSA 아키텍처**

## 02. RDBMS(SQL) 알아보기

RDBMS는 현업에서는 흔히 관계형 데이터베이스라고 해요.
다른 데이터베이스 종류에는 NoSql 이 있어요.
관계형 데이터베이스가 중요한 이유는 거의 모든 서비스의 메인 데이터베이스는 
NoSql이 아니라 RDBMS 입니다.

🔥 그렇기 때문에 관계형 데이터 베이스는 서비스를 운영하는데 있어서 엄청 중요해요.

- 02) RDBMS vs NoSql
    - RDBMS
        1. 엑셀과 같은 표의 형태로 데이터가 저장됩니다. 테이블을 만들때 컬럼이 고정되어 있기때문에 데이터가 실제로 저장되면 컬럼을 수정하기가 쉽지 않습니다.

            ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__7.06.05.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__7.06.05.png)

        2. 테이블을 여러개 만들어서 테이블끼리 연결됩니다. 그래서 네이밍에 R(Relation)이 붙습니다.
        3. 제품에는 Oracle, MySql, postgreSQL, Mssql 이 있습니다.
    - NoSql

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/Untitled.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/Untitled.png)

        1. JSON 형태로 데이터가 저장됩니다. 도큐먼트라는 RDBMS의 테이블과 비슷한 곳에 저장됩니다.
        2. 도큐먼트는 생성될때 컬럼이 고정되지 않기 때문에 변경이 용이합니다. 그렇기 때문에 정형화된 데이터 보다는 비정형화된 데이터를 저장하는 용도로 사용합니다.

## 03. RDS 설치

RDS는 AWS에서 매니지드 되는 관계형 데이터베이스 서비스예요.
직접 운영하면 까다로운 RDBMS를 관리해줍니다.

🔥  비용은 좀 들지만 서비스 운영시 개발에만 집중하게 해줍니다.

- **[코드스니펫] 참고 문서**

    ```jsx
    https://docs.aws.amazon.com/rds/?id=docs_gateway
    ```

- 03) 메뉴찾기
- 04) 메인 구경하기

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__7.17.22.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__7.17.22.png)

- 05) 생성하기 - 데이터베이스 생성 클릭
    1. 데이터베이스 생성 방식 선택

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__7.23.36.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__7.23.36.png)

        - **표준생성**은 ****사용자가 구성을 직접 설정해 보는 방법입니다.
        - **손쉬운 생성**은 권장하는 구성을 사용하는 방법입니다.
    2. 엔진옵션

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.45.04.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.45.04.png)

        - **엔진유형**은 MySQL을 선택합니다.
        - **버전**은 MySQL의 버전을 선택합니다. 최신버전인 MySQL 8 버전을 선택합니다.
    3. 템플릿

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.47.30.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.47.30.png)

        - **프로덕션**은 RDS 에서 제공하는 기본적인 설정값을 사용하도록 하는 옵션입니다.
        데이터베이스 제품들에 따라 설정하는 옵션값들이 많이 있습니다. 
        최적화된 옵션을 실제 운영하는 환경이라는 전재하에 제공합니다.
        - **개발/테스트**는 개발/테스트에
        - **프리티어**는 말그대로 공짜로 경험할수 있습니다.

            ```bash
            https://aws.amazon.com/ko/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc
            ```

    4. 설정

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.52.40.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.52.40.png)

        - **DB 클러스터 식별자**는 데이터베이스 이름을 붙이는 부분입니다.
        - **자격 증명 설정**은 데이터베이스 최고 관리자의 계정 ID와 비밀번호를 설정하는 부분입니다.
        관리자 계정정보가 설정되어야 접속할 수 있습니다.
    5. DB 인스턴스 크기

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.53.57.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.53.57.png)

        - **DB 인스턴스 클래스**는 인스턴스의 스팩을 선택하는 부분입니다.
        RDBMS를 RDS가 관리해 준다고 해도 어딘가에는 서버 컴퓨터가 존재하겠죠
        어딘가에 존재하는 서버 컴퓨터의 스팩을 선택합니다. 고사양의 스팩을 선택할수록 비용이 많이 나오겠죠.
    6. 스토리지

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.03.51.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.03.51.png)

        - **스토리지 자동 조정**은 데이터베이스의 데이터가 늘어남에따라 저장공간을 알아서 늘려주는 기능입니다. 최대 스토리지 임계값으로 설정된 용량만큼 디스크 사이즈를 늘려줍니다.
    7. 연결

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-12__8.55.42.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-12__8.55.42.png)

        - **퍼블릭 엑세스 가능**을 ****예로 선택하면 외부에서도 접속할 수 있습니다.

    8. 데이터베이스 인증

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.09.12.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.09.12.png)

        - **데이터베이스 인증 옵션**은 데이터베이스에 접속할때 인증방법을 선택합니다.
    9. 월별 추정 요금

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.27.55.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.27.55.png)

    10. 생성 클릭 & 생성 확인

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.36.54.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.36.54.png)

        - 생성이 완료되었습니다.
    11. 보안그룹 소스 변경

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__8.33.07.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__8.33.07.png)

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__8.34.59.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__8.34.59.png)

    12. 생성 완료!!

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__8.34.19.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__8.34.19.png)

## 04. RDS 사용

- 06) 연결하기
    - 파이참을 이용해 데이터베이스 접속

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.50.34.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.50.34.png)

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.54.11.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__11.54.11.png)

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__2.42.44.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__2.42.44.png)

- 07) 스키마 추가
    - **[코드스니펫] 스키마 추가**

        ```jsx
        create database sparta default character set utf8 collate utf8_general_ci;
        ```

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-10__7.44.26.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-10__7.44.26.png)

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-10__7.45.32.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-10__7.45.32.png)

- 08) 데이터베이스에 테이블 추가

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.18.06.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.18.06.png)

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.19.30.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.19.30.png)

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.20.53.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.20.53.png)

- 09) 쿼리 실행해보기
    - [코드스니펫] 저장

        ```sql
        insert into file(file_name) value('test.jpg');
        ```

    - [코드스니펫] 조회

        ```bash
        select * from file;
        ```

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.22.10.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.22.10.png)

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.30.44.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.30.44.png)

## 05. **[한 걸음 더** 🏃**]** RDS, Python 연동해보기

이제 데이터베이스 만들었으니 파이썬과 연동해 봐야겠죠.
이전에 만들었던 EB에 배포해서 잘 동작하는지 확인해볼게요.

- 10) RDS 보완그룹 수정

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-17__12.55.25.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-17__12.55.25.png)

- 11) 벡엔드 코드 추가
    - **[코드스니펫] 백엔드 코드 `application.py`**

        ```python
        import boto3
        from flask import Flask, render_template, request, jsonify
        from flask_cors import CORS
        import os
        from flaskext.mysql import MySQL

        application = Flask(__name__)

        # cors
        cors = CORS(application, resources={r"/*": {"origins": "*"}})

        # mysql
        mysql = MySQL()
        application.config['MYSQL_DATABASE_USER'] = os.environ["MYSQL_DATABASE_USER"]
        application.config['MYSQL_DATABASE_PASSWORD'] = os.environ["MYSQL_DATABASE_PASSWORD"]
        application.config['MYSQL_DATABASE_DB'] = os.environ["MYSQL_DATABASE_DB"]
        application.config['MYSQL_DATABASE_HOST'] = os.environ["MYSQL_DATABASE_HOST"]
        mysql.init_app(application)

        @application.route('/')
        def main():
            return "핵심 쏙쏙 AWS"

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

            conn = mysql.connect()
            cursor = conn.cursor()
            cursor.execute("insert into file(file_name) value('" + file.filename + "')")
            conn.commit()
            conn.close()

            return jsonify({'result': 'success'})

        @application.route('/files', methods=['GET'])
        def files():
            conn = mysql.connect()
            cursor = conn.cursor()
            cursor.execute("SELECT file_name from file")
            data = cursor.fetchall()
            conn.close()

            return jsonify({'result': 'success', 'files':data})

        if __name__ == '__main__':
            application.debug = True
            application.run()
        ```

    - **[코드스니펫] 프론트 코드 `index.html`**

        ```html
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

            <title>스파르타코딩클럽 | 나홀로 메모장111</title>

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
                $(document).ready(function(){
                    getFiles();
                })

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
                            location.reload();
                        },
                    });
                }

                function getFiles() {
                    $.ajax({
                        type: 'GET',
                        url: '{EB URL}/files',
                        success: function (data) {
                            for(let i = 0 ; i < data['files'].length ; i++){
                                makeCard(data['files'][i]);
                            }
                        },
                    });
                }

                function makeCard(data){
                    let card = ` <div class="card">
                                        <div>
                                            <img class="card-img-top"
                                                 src="http://djocwjyh5wkd4.cloudfront.net/${data}"
                                                 alt="Card image cap">
                                            <p class="card-text comment">${data}</p>
                                        </div>
                                    </div>`;
                    $("#cards-box").append(card);
                }
            </script>

        </head>

        <body>
        <div class="wrap">
            <div class="jumbotron">
                <h1 class="display-4">나홀로 이미지 메모장! 완료!!</h1>
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
            </div>
        </div>
        </body>

        </html>
        ```

- 12) 라이브러리 추가
    - [코드스니펫] 로컬

        ```bash
        pip install install flask-mysql
        ```

    - [코드스니펫] EB 배포용

        ```bash
        pip freeze > requirements.txt
        ```

- 13) EB 환경변수 추가

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__7.33.32.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-11__7.33.32.png)

## 06. EC2, RDS **비용 계산**

- **[코드스니펫] EC2 비용 계산 참고 문서**

    ```bash
    https://calculator.aws/#/createCalculator/EC2
    ```

- **[코드스니펫] RDS 비용 계산 참고 문서**

    ```bash
    https://calculator.aws/#/createCalculator/RDSMySQL
    ```

## 07. Redis 알아보기

Redis는 인메모리 디비에요. 
RDBMS가 파일에 데이터를 저장하는 것에 비해 인메모리 디비는 
메모리에 데이터를 저장하기 때문에 RDBMS에 비해 속도가 빠르답니다. 

🔥  RDBMS의 부하를 덜어주기 위해 Redis를 많이 사용합니다.

- 14) 사용중인 서비스

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.43.23.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.43.23.png)

## 08. ElastiCache 사용해보기

- **[코드스니펫] 참고 문서**

    ```jsx
    https://docs.aws.amazon.com/elasticache/?id=docs_gateway
    ```

- 15) 메뉴 찾기

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.49.05.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.49.05.png)

- 16) 메인 구경하기

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.55.28.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__4.55.28.png)

- 17) 생성하기
    - 보안그룹 만들기

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-17__2.49.03.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-17__2.49.03.png)

    - 클러스터 엔진 & 위치선택

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__5.21.48.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__5.21.48.png)

        - 클러스터 엔진에는 Redis 선택합니다.
        - 위치는 Amazon 클라우드를 선택합니다.

    - Redis 설정

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__5.23.59.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__5.23.59.png)

        - 노드 유형은 프리티어 스팩인 t2.micro 선택합니다.
        - 복제본 개수는 0으로 조절 하지 않습니다.
    - 보안그룹 변경

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-17__2.52.13.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-17__2.52.13.png)

    - 생성 & 확인

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__5.36.36.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__5.36.36.png)

## 09. ElastiCache, Python 연동해보기

RDS 와 달리 ElastiCache는 외부에서 접속이 되지 않도록 되어있습니다.
그래서 배포를 해서 같은 VPC내의 인스턴스에서 확인해야합니다.

🔥  내 컴퓨터에서는 접속할 수 없습니다.
꼭 AWS 에 배포해서 정상작동을 테스트 해보아야 합니다.

- 18) 코드 추가
    - **[코드스니펫] `application.py`**

        ```python
        import boto3
        from flask import Flask, render_template, request, jsonify
        from flask_cors import CORS
        import os
        from flaskext.mysql import MySQL
        import redis

        application = Flask(__name__)

        # cors
        cors = CORS(application, resources={r"/*": {"origins": "*"}})

        # mysql
        mysql = MySQL()
        application.config['MYSQL_DATABASE_USER'] = os.environ["MYSQL_DATABASE_USER"]
        application.config['MYSQL_DATABASE_PASSWORD'] = os.environ["MYSQL_DATABASE_PASSWORD"]
        application.config['MYSQL_DATABASE_DB'] = os.environ["MYSQL_DATABASE_DB"]
        application.config['MYSQL_DATABASE_HOST'] = os.environ["MYSQL_DATABASE_HOST"]
        mysql.init_app(application)

        # redis
        db = redis.Redis(os.environ["REDIS_HOST"], decode_responses=True)

        @application.route('/')
        def main():
            return "핵심 쏙쏙 AWS"

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

            conn = mysql.connect()
            cursor = conn.cursor()
            cursor.execute("insert into file(file_name) value('" + file.filename + "')")
            conn.commit()

            cursor.execute("SELECT count(*) from file")
            data = cursor.fetchone()
            conn.close()
            db.set("fileCount", data[0])

            return jsonify({'result': 'success'})

        @application.route('/files', methods=['GET'])
        def files():
            conn = mysql.connect()
            cursor = conn.cursor()
            cursor.execute("SELECT file_name from file")
            data = cursor.fetchall()
            conn.close()

            return jsonify({'result': 'success', 'files':data})

        @application.route('/file/count', methods=['GET'])
        def file_count():
            return jsonify({'result': 'success', 'count':db.get("fileCount")})

        if __name__ == '__main__':
            application.debug = True
            application.run()
        ```

    - **[코드스니펫] `index.html`**

        ```html
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

            <title>스파르타코딩클럽 | 나홀로 메모장111</title>

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
                $(document).ready(function(){
                    getCount();
                    getFiles();
                })

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
                            location.reload();
                        },
                    });
                }

                function getFiles() {
                    $.ajax({
                        type: 'GET',
                        url: '{EB URL}/files',
                        success: function (data) {
                            for(let i = 0 ; i < data['files'].length ; i++){
                                makeCard(data['files'][i]);
                            }
                        },
                    });
                }

                function makeCard(data){
                    let card = ` <div class="card">
                                        <div>
                                            <img class="card-img-top"
                                                 src="http://djocwjyh5wkd4.cloudfront.net/${data}"
                                                 alt="Card image cap">
                                            <p class="card-text comment">${data}</p>
                                        </div>
                                    </div>`;
                    $("#cards-box").append(card);
                }

                function getCount() {
                    $.ajax({
                        type: 'GET',
                        url: '{EB URL}/file/count',
                        success: function (data) {
                            $("#count").html(data.count);
                        },
                    });
                }
            </script>

        </head>

        <body>
        <div class="wrap">
            <div class="jumbotron">
                <h1 class="display-4">나홀로 이미지 메모장! 완료!!</h1>
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
            <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <a class="navbar-brand" href="#">총 파일갯수:<span id="count"></span></a>
            </nav>
            <div id="cards-box" class="card-columns">
            </div>
        </div>
        </body>

        </html>
        ```

- 19) 라이브러리 추가
    - **[코드스니펫] 로컬**

        ```bash
        pip install redis
        ```

    - **[코드스니펫] EB 배포용**

        ```bash
        pip freeze > requirements.txt
        ```

- 20) EB 환경변수 추가

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/redis.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/redis.png)

## 10. ElastiCache **비용 계산**

- **[코드스니펫] ElastiCache 비용 계산 참고 문서**

    ```jsx
    https://calculator.aws/#/createCalculator/ElastiCache
    ```

## 11. 클라우드 시대의 로그 관리

빅데이터의 시대입니다. 예전에 로그는 파일에 쌓아났다가 에러났을때만 봤습니다.
하지만 이제 로그로도 유의미한 데이터를 분석하는게 가능해졌습니다.

🔥 그래서 클라우드 시대에는 로그도 분석하게 되었습니다.

- 21) 파일로 관리

    ```verilog
    127.0.0.1 - - [03/Apr/2021 18:42:59] "GET /?__debugger__=yes&cmd=resource&f=style.css HTTP/1.1" 200 -
    127.0.0.1 - - [03/Apr/2021 18:42:59] "GET /?__debugger__=yes&cmd=resource&f=jquery.js HTTP/1.1" 200 -
    127.0.0.1 - - [03/Apr/2021 18:42:59] "GET /?__debugger__=yes&cmd=resource&f=debugger.js HTTP/1.1" 200 -
    127.0.0.1 - - [03/Apr/2021 18:42:59] "GET /?__debugger__=yes&cmd=resource&f=console.png HTTP/1.1" 200 -
    127.0.0.1 - - [03/Apr/2021 18:42:59] "GET /?__debugger__=yes&cmd=resource&f=ubuntu.ttf HTTP/1.1" 200 -
    127.0.0.1 - - [03/Apr/2021 18:42:59] "GET /?__debugger__=yes&cmd=resource&f=console.png HTTP/1.1" 200 -
     * Detected change in '/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/app.py', reloading
     * Restarting with stat
    pydev debugger: process 31805 is connecting
     * Debugger is active!
     * Debugger PIN: 306-791-020
     * Detected change in '/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/app.py', reloading
     * Restarting with stat
    pydev debugger: process 31859 is connecting
     * Debugger is active!
     * Debugger PIN: 306-791-020
     * Detected change in '/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/app.py', reloading
     * Restarting with stat
    pydev debugger: process 31907 is connecting
    File "/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/venv/lib/python3.8/site-packages/redis/client.py", line 1801, in set
        return self.execute_command('SET', *pieces)
      File "/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/venv/lib/python3.8/site-packages/redis/client.py", line 898, in execute_command
        conn = self.connection or pool.get_connection(command_name, **options)
      File "/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/venv/lib/python3.8/site-packages/redis/connection.py", line 1192, in get_connection
        connection.connect()
      File "/Users/younghokwak/Desktop/sparta/allaboutaws/allaboutaws-backend/venv/lib/python3.8/site-packages/redis/connection.py", line 563, in connect
        raise ConnectionError(self._error_message(e))
    redis.exceptions.ConnectionError: Error 60 connecting to redis-sparta.8imnfo.0001.apn2.cache.amazonaws.com:6379. Operation timed out.
    ```

    - 예전에는 파일로 관리했습니다.
    파일로만 관리하니 데이터 분석, 수집, 검색 등을 하기가 힘들어서 
    로그는 죽어있는 데이터로 치부되었습니다.
- 22) 다양한 분석도구들의 등장

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__9.34.06.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__9.34.06.png)

## 12. Elasticsearch 알아보기

Elasticsearch 는 검색엔진 오픈소스 입니다.
이전에는 검색엔진만으로 사용하였습니다. 그러나 아키텍처의 변화와 분산환경에서 
로그의 중요성이 부각되면서 로그를 데이터화하는 ELK 스택으로 발전하였습니다.

🔥  ELK는 최근에 가장 많이 사용하는 로그분석 제품입니다.

- 23) 오픈소스 검색엔진

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__9.54.06.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__9.54.06.png)

    - 출발은 검색엔진이었습니다. 검색엔진만을 위해 만들어졌지만 이제는 로그를 쌓고 
    검색을 하는데 유용하게 쓰이고 있습니다.
- 24) ELK 스택으로 발전

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.08.23.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.08.23.png)

    - 클라우드의 아키텍처 변화에서 살펴봤듯이 컴퓨팅 환경이 분산되면서 
    ELK와 같은 제품들이 더욱더 각광받고 있다.

## 13. Elasticsearch Service 사용해보기

- **[코드스니펫] 참고 문서**

    ```jsx
    https://docs.aws.amazon.com/elasticsearch-service/index.html
    ```

- 25) 메뉴찾기

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.10.38.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.10.38.png)

- 26) 메인 구경하기

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.11.49.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.11.49.png)

- 27) 생성하기
    1. 배포 유형 선택

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.17.33.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.17.33.png)

        - 배포 유형은 개발 및 테스트로 선택합니다.
        - 버전은 최신버전 설정을 그대로 유지합니다.
    2. 도메인 구성

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.21.33.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.21.33.png)

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__6.50.00.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__6.50.00.png)

        - 자동 튜닝은 테스트 상황이기 때문에 비활성화 합니다.
        - 인스턴스 유형은 t3.small을 선택합니다.
    3. 엑세스 및 보안구성

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.53.04.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__10.53.04.png)

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__6.52.10.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__6.52.10.png)

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__6.53.29.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__6.53.29.png)

        - **네크워크 구성**은 운영환경에서는 VPC 엑세스만 권장하지만 테스트 상황이기 때문에 퍼블릭 엑세스를 선택합니다.
        - **엑세스 정책**은 생성된 Elasticsearch Service에 엑세스를 허용하는 정책이다.
        사용자 지정 액세스 정책을 선택하고 IPv4 주소를 선택합니다.
    4. 생성 & 확인

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-04__9.33.07.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-04__9.33.07.png)

        - 엔드포인트는 Elasticsearch에 데이터를 저장, 조회 할때 사용하는 URL 입니다.
        - Kibana는 분석된 로그 데이터를 시각적으로 보여주는 페이지 입니다.
    5. 브라우저에서 접근

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__7.52.45.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-14__7.52.45.png)

- 28) logstash 설치
    1. EC2 생성
    2. JAVA 설치
        - [코드스니펫] 패키지 업데이트

            ```html
            sudo apt-get update
            ```

        - [코드스니펫] 설치

            ```html
            sudo apt-get install openjdk-8-jdk
            ```

    3. logstash 설치
        - [코드스니펫] logstash 설치 문서

            ```bash
            https://www.elastic.co/guide/en/logstash/current/installing-logstash.html
            ```

        - [코드스니펫] 다운로드

            ```bash
            wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
            ```

        - [코드스니펫] 패키지 설치

            ```bash
            sudo apt-get install apt-transport-https
            ```

        - [코드스니펫] 패키지 리파지토리 추가

            ```bash
            echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
            ```

        - [코드스니펫] 패키지 업데이트 & 설치

            ```bash
            sudo apt-get update && sudo apt-get install logstash
            ```

    4. logstash 실행
        - [코드스니펫] 설정파일 생성

            ```bash
            sudo vi /etc/logstash/conf.d/logstash-python.conf
            ```

        - [코드스니펫] 설정파일

            ```bash
            input {
              tcp {
                port => 5044
              }
            }

            output {
              elasticsearch {
                hosts => ["https://search-elasticsearch-sparta-tedvy7ev365r74opwxg2eumxn4.ap-northeast-2.es.amazonaws.com:443"]
                index => "flask-logs-%{+YYYY.MM.dd}"
                user => "admin"
                password => "Aa12345!"
                ssl => true
                ilm_enabled => false
              }
            }
            ```

        - [코드스니펫] 실행

            ```bash
            sudo systemctl start logstash.service
            ```

## 14. **[한 걸음 더** 🏃**]** Elasticsearch Service, Python 연동해보기

- 29) 코드 추가
    - **[코드스니펫] `application.py`**

        ```python
        import boto3
        from flask import Flask, request, jsonify
        from flask_cors import CORS
        import os
        from flaskext.mysql import MySQL
        import redis
        import logging
        from logstash_async.handler import AsynchronousLogstashHandler

        application = Flask(__name__)

        # cors
        cors = CORS(application, resources={r"/*": {"origins": "*"}})

        # mysql
        mysql = MySQL()
        application.config['MYSQL_DATABASE_USER'] = os.environ["MYSQL_DATABASE_USER"]
        application.config['MYSQL_DATABASE_PASSWORD'] = os.environ["MYSQL_DATABASE_PASSWORD"]
        application.config['MYSQL_DATABASE_DB'] = os.environ["MYSQL_DATABASE_DB"]
        application.config['MYSQL_DATABASE_HOST'] = os.environ["MYSQL_DATABASE_HOST"]
        mysql.init_app(application)

        # redis
        db = redis.Redis(os.environ["REDIS_HOST"], decode_responses=True)

        #logstash
        python_logger = logging.getLogger('python-logstash-logger')
        python_logger.setLevel(logging.INFO)
        python_logger.addHandler(AsynchronousLogstashHandler(os.environ["LOGSTASH_HOST"], 5044, database_path=''))

        @application.route('/')
        def main():
            python_logger.info('main')
            return "핵심 쏙쏙 AWS"

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

            conn = mysql.connect()
            cursor = conn.cursor()
            cursor.execute("insert into file(file_name) value('" + file.filename + "')")
            conn.commit()

            cursor.execute("SELECT count(*) from file")
            data = cursor.fetchone()
            conn.close()
            db.set("fileCount", data[0])

            python_logger.info(file.filename)
            return jsonify({'result': 'success'})

        @application.route('/files', methods=['GET'])
        def files():
            conn = mysql.connect()
            cursor = conn.cursor()
            cursor.execute("SELECT file_name from file")
            data = cursor.fetchall()
            conn.close()

            return jsonify({'result': 'success', 'files':data})

        @application.route('/file/count', methods=['GET'])
        def file_count():
            return jsonify({'result': 'success', 'count':db.get("fileCount")})

        if __name__ == '__main__':
            application.debug = True
            application.run()
        ```

- 30) 라이브러리 추가
    - [코드스니펫] 로컬

        ```bash
        pip install python-logstash-async
        ```

    - [코드스니펫] EB 배포용

        ```bash
        pip freeze > requirements.txt
        ```

- 31) EB 환경변수 추가

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-15__8.51.09.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-15__8.51.09.png)

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-15__8.56.20.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-15__8.56.20.png)

- 32) Kibana 인덱스 추가
    1. 로그인

        ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/11.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/11.png)

    2. 인덱스 패턴 만들기
        - 메뉴

            ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/Untitled%201.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/Untitled%201.png)

        - Create index pattern 클릭!!

            ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/create.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/create.png)

        - 패턴 정하기

            ```html
            input {
              tcp {
                port => 5044
              }
            }

            output {
              elasticsearch {
                hosts => ["https://search-elasticsearch-sparta-tedvy7ev365r74opwxg2eumxn4.ap-northeast-2.es.amazonaws.com:443"]
                index => "flask-logs-%{+YYYY.MM.dd}"
                user => "admin"
                password => "Aa123456!"
                ssl => true
                ilm_enabled => false
              }
            }
            ```

            ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/patt.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/patt.png)

        - Time field 정하기

            ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/22.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/22.png)

        - 생성!!

            ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/444.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/444.png)

- 33) Kibana 조회

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-15__9.01.08.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-15__9.01.08.png)

## 15. Elasticsearch Service **비용 계산**

- **[코드스니펫] 가격 테이블**

    ```jsx
    https://aws.amazon.com/ko/elasticsearch-service/pricing/
    ```

- **[코드스니펫] 가격 계산**

    ```jsx
    https://calculator.aws/#/createCalculator/ElasticsearchService
    ```

## 16. 우리가 3주동안 배운것들

3주동안 AWS에 대하여 정신없이 많은것들을 배워봤어요~
어떠셨나요 ⁉️

🔥  이제 개발자가 클라우드를 모르면 안되는 세상이 되었습니다.
자신의 서비스를 만들기 위해서도 클라우드를 꼭 아셔야합니다.

- 34) 클라우드를 사용하는 이유

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__9.01.05.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-03__9.01.05.png)

- 35) 클라우드에 흥미를 가지셨다면

    ![AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-04__2.46.25.png](AWS%20BASIC%20WEEK%203%208d206c62c4204a49af0601f546fbcb11/_2021-04-04__2.46.25.png)

## 17. 정리

### 정리

☁️  클라우드에서 데이터베이스를 다루는 기술을 알아봤습니다.

☁️  RDS 는 RDBMS를 쉽게 운영하여 개발에 집중하게 해주는 서비스입니다.

☁️  ElastiCache 는 Redis를 쉽게 다루도록 하여 RDBMS + Cache 를 사용하여 
      서비스를 좀 더 안정적으로 운영하게 해주는 서비스입니다.

☁️  클라우드에서 로그를 다루는 기술을 알아봤습니다.

☁️  Elasticsearch Service 는 로그를 저장하고, 데이터화를 할수있게 해주는 데이터베이스 서비스입니다.