document
========

document of milkcocoa


#ドキュメント
##MilkCocoaとのコネクションの確立

    var milkcocoa = new MilkCocoa('https://mlkcca.com', 'app id', function() {/*onconnected*/});

##データストアオブジェクトの取得

    var messageDataStore = milkcocoa.dataStore("messages");

##データの書き込み

    messageDataStore.push({title : "タイトル", content : "内容"});
    //または
    messageDataStore.child('messageid').set({title : "タイトル", content : "内容"});

##データの読み込み

    //クエリをかける。
    messageDataStore.query({}).done(function(message){});
    //データを一つとってくる。
    messageDataStore.child('messageid').get(function(message){});

##イベントを受け取る

    //他の誰かがデータをpushした時に呼ばれる。
    messageDataStore.on('push', function(message) {});

##複雑なクエリ

    //titleでソートして、５個だけとってくる。
    messageDataStore.query({}).sort("title").limit(5).done(function(message){});
