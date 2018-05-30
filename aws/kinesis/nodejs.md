# Node.js

```sh
>nvm use 8.10
>mkdir node-kinesis
>cd node-kinesis
>npm init
>npm install aws-sdk --save
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN kinesis-test@1.0.0 No description
npm WARN kinesis-test@1.0.0 No repository field.

+ aws-sdk@2.247.1
added 15 packages in 6.613s
```

연결
```js
var AWS = require('aws-sdk');

// 로컬일 경우 region은 아무곳이나
var kinesis = new AWS.Kinesis({endpoint: 'http://localhost:7000',region:'ap-northeast-1'});

kinesis.listStreams(console.log.bind(console));

---
null { StreamNames: [ 'testStream' ], HasMoreStreams: false }
```