# Kinesis Local

설치
```sh
> npm install kinesalite
> npm install aws-sdk
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN kinesis-test@1.0.0 No description
npm WARN kinesis-test@1.0.0 No repository field.

+ aws-sdk@2.247.1
added 15 packages in 6.613s
```

구동
```sh
> kinesalite --port 7000 --path .
Listening at http://:::7000
```

스트림 생성
```sh
> aws kinesis create-stream --stream-name testStream --shard-count 1 --endpoint-url http://localhost:7000 --no-verify-ssl
```

연결
```js
var AWS = require('aws-sdk');

var kinesis = new AWS.Kinesis({endpoint: 'http://localhost:7000',region:'apnortheast-1'});

kinesis.listStreams(console.log.bind(console));

---
null { StreamNames: [ 'testStream' ], HasMoreStreams: false }
```


### 참조
* [kinesalite](https://github.com/mhart/kinesalite)