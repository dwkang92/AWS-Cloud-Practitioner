# Review Notes 1

This chapter will zero in on the reviewing all courses, related with AWS Cloud Practitioner Certificate. Mainly go over jargons, basic concepts of AWS Services. 

## 1. What is Cloud Service?

---

1. クラウドとは、AWSのようなクラウドサービスプラットフォームから**インターネット経由**でコンピューティング(仮想サーバ)、データベース、ストレージ、アプリケーションをはじめとした、**様々なITリソース**を**オンデマンド**で利用できるサービスの総称です。
2. AWS Cloud Computingには6つのメリットがあります。
    1. 固定費(設備投資費用) → 柔軟な変動費として、投資が必要とする適所に投資できます。
    2. スケールによる大きなコストメリット：規模の経済をイメージすると理解しやすいです。
    3. キャパシティ予測が不要になります。伸縮性と弾力性のコンセプトを理解するとより理解が深まるでしょう。
    4. 速度と俊敏性の向上：最新リソースを従来のオンプレミス方法より早い段階で便利に利用可能。
    5. データセンターの運用と補修への投資はAWSが担当するので、ユーザーは投資不要です。
    6. 数分で世界中にデプロイできます。クリック数回で完成です。
3. **Iaas / Paas / Saas の概念はしっかりと理解する必要がある。**
    1. **SaaS**
        1. Software as a Service
        2. Application, Platform (OS), Hardware (Infrastructure)まで提供するサービスのこと。
        3. SNS (Facebook, Instagram), Dropbox, G Suite
        4. す部に使うことができ、手間が少ないので便利である反面、自由度は低い。
        5. 特別な専門知識などは要らない。I/O端末だけ用意してインストールすれば良い。
    2. **PaaS**
        1. Platform as a Service
        2.  Platform (OS), Hardware (Infrastructure)を提供するサービスのこと。
        3. レンタルサーバーなどが当てはまる。
        4. 好きなアプリケーションを入れられるが、未対応アプリケーションもある。
        5. サーバーを管理する必要があり、場合によってはアプリケーションを用意する必要がある。
    3. **IaaS**
        1. Infrastructure as a Service
        2. Hardware (Infrastructure)だけが必要である。
        3. 使用するためにセッティングが必要で、サーバー管理のための知識が必要である。
        4. 場合によってはアプリケーションの用意が必要な場合もある。
        5. Infrastructure as a service (IaaS) is a type of cloud computing service that offers essential compute, storage, and networking resources on demand, on a pay-as-you-go basis. IaaS is one of the four types of cloud services, along with software as a service (SaaS), platform as a service (PaaS), and serverless.

            ![Untitled](Review%20Notes%201%20debb2d7310bb4b6bb2fc3e12bcc1f36b/Untitled.png)

## 2. Cloud Architecture

---

1. Design for Failure & SPOF
    1. 時間が経てばいつかは故障するということを認識し、故障に備えた設計を実現する。
    2. 単一障害点を無くす必要がある。
2. コンポーネントの分離
    1. クラウドはサービス指向アーキテクチャの設計原理を踏襲する。
    2. 疎結合と密結合について
    3. **Amazon SQS (Simple Queue Service)**
        1. Simple Queue Serviceの略で、フルマネージドのキューイングサービス。キューイングとは異なるソフトウェア間でデータの送受信する手法の一つで、ソフトウェア間を直接データを渡すのではなく、第三者経由でデータを渡すことで、送信側と受信側が好きなときに処理を行うことができます。そのキューイングができるサービスがSQSになります。

            [https://qiita.com/miyuki_samitani/items/e46ef9452fcd73f9d240](https://qiita.com/miyuki_samitani/items/e46ef9452fcd73f9d240)

            [https://www.fenet.jp/aws/column/aws-beginner/299/#AWSの「Amazon_SQS（Simple_Queue_Service）」とは？](https://www.fenet.jp/aws/column/aws-beginner/299/#AWS%E3%81%AE%E3%80%8CAmazon_SQS%EF%BC%88Simple_Queue_Service%EF%BC%89%E3%80%8D%E3%81%A8%E3%81%AF%EF%BC%9F)

3. 弾力性・伸縮性
    1. ユースケースによるスケーリングの3種類
        1. 巡回：一定間隔に発生する定期的なスケーリング
        2. イベントベース：予定されているビジネスイベントなど、スポット的なトラフィック増減
        3. オンデマンドの自動スケーリング：監視サービスを利用することにより、監視項目に基づいてトリガーを送信しスケールアウト/スケールインを行う。
4. 並列化
    1. ロードバランサー(ELB)を利用して複数の非同期のwebサーバー全体で受信リクエストを分散。
    2. スケールアップ/スケールアウト
5. 動的コンテンツはコンピュータの近くに、静的コンテンツはエンドユーザーの近くに保管
    1. 従来のオンプレミスのシステムでは、伝送遅延を回避するためにデータをコンピュータまたは処理要素のできるだけ近くに保管していた。
    2. クラウドはインターネット経由で利用するため、配信のオーバーヘッドやボトルんネック対策は必須である。
    3. RDBMSを用いてデータを保管、検索するWEBアプリの場合は、データベースとアプリケーションサーバーをクラウドに一度にまとめて以降する必要がある。
    4. 静的コンテンツはCDNなどのサービスを利用して配布するとii.で説明した不安要素が軽減可能。
    5. 動的コンテンツはプログラムから出力されたページで、様々な要因によって表示される内容がユーザーによって変わることをイメージすると理解しやすい。
    6. 静的コンテンツは、世界どこでいつアプリケーションを稼働しても、表示される基本内容とかフォーマットが変わらないことをイメージすると理解しやすい。
    7. つまり、動的コンテンツはデータベースやアプリケーションサーバーをクラウドに一度にまとめる必要があるだろう。代わりに静的コンテンツは基本フォーマットのようなものなので、ユーザーの近くに置いてあっても構わないと考えられる。

## 3. AWS Well-Architected Framework

---

1. 運用上の優秀性
2. セキュリティ
3. 信頼性
4. パフォーマンス効率
5. コスト最適化