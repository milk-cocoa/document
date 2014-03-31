document
========

milkcocoaのドキュメント


# milkcocoa仕様

## 1,ログイン機能
milkcocoaは、ユーザーに対して、以下の機能を提供する。

- milkcocoaにログイン機能を提供し、milkcocoaのAPI利用、およびmilkcocoaバックエンド管理画面を提供する。

- ログイン機能は、サインアップ、サインイン、サインアウトからなる。

- サインアップは、ユーザのサインイン用のメールアドレス、パスワードを登録する。

- サインインは登録されたメールアドレス、パスワードと入力を照合し、milkcocoaの機能の利用を可能にする。

- サインインしたユーザはサインアウトしない限り、再びサインインすることができない。

- サインアウトは、milkcocoa機能の利用を終了し、サインインを可能にする。

## 2, バックエンド管理機能

milkcocoaはユーザに対し、バックエンドの管理機能を提供する。

- App Keyの発行、管理、削除
- DataStore管理機能
- 許可ドメイン管理
- Account管理
- Rule Script利用

### 2,1 App Key


- milkcocoaはログイン後、Appキーを発行することにより、Appキーに対するDataStore、Accountの結び付けを行なう。

- 



## 3,  milkcocoaのAPI機能

- 


#チュートリアル
###MilkCocoaとのコネクションの確立

    var milkcocoa = new MilkCocoa('https://mlkcca.com', 'app id', function() {/*onconnected*/});

###データストアオブジェクトの取得

    var messageDataStore = milkcocoa.dataStore("messages");

###データの書き込み

    messageDataStore.push({title : "タイトル", content : "内容"});
    //または
    messageDataStore.child('messageid').set({title : "タイトル", content : "内容"});

###データの読み込み

    //クエリをかける。
    messageDataStore.query({}).done(function(message){});
    //データを一つとってくる。
    messageDataStore.child('messageid').get(function(message){});

###イベントを受け取る

    //他の誰かがデータをpushした時に呼ばれる。
    messageDataStore.on('push', function(message) {});

###複雑なクエリ

    //titleでソートして、５個だけとってくる。
    messageDataStore.query({}).sort("title").limit(5).done(function(message){});


#リファレンス
##プラットフォーム
###Javascript

    <script src="http://cdn.mlkcca.com/v2.1/milkcocoa.js"></script>
    <script>
      var milkcocoa = new MilkCocoa("https://mlkcca.com", "app id", function() {});
    </script>


###Android

https://github.com/milk-cocoa/milkcocoa_for_android

    this.milkcocoa = new MilkCocoa();
    this.milkcocoa.init("https://mlkcca.com", "chatapp", new Callback() {
        @Override
        public void callback(Object err) {
        
        }
    });

