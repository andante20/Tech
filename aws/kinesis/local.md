# Kinesis Local

### 설치
```sh
> npm install kinesalite
```

### 구동
```sh
> kinesalite --port 7000 --path .
Listening at http://:::7000
```

### AWS CLI
```sh
> aws kinesis create-stream --stream-name testStream --shard-count 1 --endpoint-url http://localhost:7000 --no-verify-ssl

>aws kinesis describe-stream --stream-name testStream --endpoint-url http://localhost:7000
{
    "StreamDescription": {
        "KeyId": null,
        "EncryptionType": "NONE",
        "StreamStatus": "ACTIVE",
        "StreamName": "testStream",
        "Shards": [
            {
                "ShardId": "shardId-000000000000",
                "HashKeyRange": {
                    "EndingHashKey": "340282366920938463463374607431768211455",
                    "StartingHashKey": "0"
                },
                "SequenceNumberRange": {
                    "StartingSequenceNumber": "49584880958946076604572174628188246884282034573115654146"
                }
            }
        ],
        "StreamARN": "arn:aws:kinesis:us-east-1:000000000000:stream/testStream",
        "EnhancedMonitoring": [
            {
                "ShardLevelMetrics": []
            }
        ],
        "StreamCreationTimestamp": 1527481611,
        "RetentionPeriodHours": 24
    }
}

>aws kinesis list-streams --endpoint-url http://localhost:7000
{
    "StreamNames": [
        "testStream"
    ]
}

>aws kinesis get-shard-iterator --shard-id shardId-000000000000 --shard-iterator-type TRIM_HORIZON --stream-name testStream --endpoint-url http://localhost:7000
{
    "ShardIterator": "AAAAAAAAAAGib91CGnokva9eTDL7BuJuOixGP3XjoOjq7VIPVy/AbNYXU5d64TtL0RIwEOc8XzKp23GrBNO651wcBCvjJLK+QuB820gZhYAvFHL3gum3lUxJubVc0tT3ijOAErtDSREsDZ+IEBzrOUuCLkVSjZ2c0RciMNULFQg8Qk6Tki5+FE+Qsj2ba5miamfZozmoEb8="
}

>aws kinesis get-records --shard-iterator AAAAAAAAAAGib91CGnokva9eTDL7BuJuOixGP3XjoOjq7VIPVy/AbNYXU5d64TtL0RIwEOc8XzKp23GrBNO651wcBCvjJLK+QuB820gZhYAvFHL3gum3lUxJubVc0tT3ijOAErtDSREsDZ+IEBzrOUuCLkVSjZ2c0RciMNULFQg8Qk6Tki5+FE+Qsj2ba5miamfZozmoEb8= --endpoint-url http://localhost:7000
{
    "Records": [],
    "NextShardIterator": "AAAAAAAAAAEAyPIdAO0UzEa3hJSUx1TjouEn+yEDdlAfHLARMnOKRNG4vYX1TWdAeGNIHpcga5Fxojw+UtWNTeMLPxLcGC6q5xNR5QyyGAJmNIvkzDerlzGRrvjKczNQ1ap5Ff9kNMBnizvgfLUxnjVDyv7BR8jsFDBtkHfEdG6fCaIuVEaFfa6Igx1PiAMpAfHYUzBY67o=",
    "MillisBehindLatest": 0
}

>aws kinesis put-record --stream-name testStream --partition-key 123 --data '{"test":"1111"}' --endpoint-url http://localhost:7000
{
    "ShardId": "shardId-000000000000",
    "SequenceNumber": "49584880958946076604572174628188246884286735603799687170"
}
>aws kinesis get-records --shard-iterator AAAAAAAAAAGxzBdODklyPaMGAffqwLNMk5SgW6pwur+sQgfL3xGYyBb/v3dbD0STstt3mWp5UlVAYue4gVn0GssHUvCwd4i6SA8zxvUvAWrG/SAXQ+eDZZXpBrP02V0M+p9JvY4+KF3q6DujFsJ9Bcs3w3WeMWglkPmFtRf/0YHTTf2WPGH65JKpQjZ3k7ujdLPpW4cf7Y4= --endpoint-url http://localhost:7000
{
    "Records": [
        {
            "Data": "e3Rlc3Q6MTExMX0=",
            "PartitionKey": "123",
            "ApproximateArrivalTimestamp": 1527550020.837,
            "SequenceNumber": "49584880958946076604572174628188246884286735603799687170"
        }
    ],
    "NextShardIterator": "AAAAAAAAAAFlLHly1owkxx7hu9nuQiSsJXW3xhSNeNgrohxvR7PdcdrH5Kw4r8EUobRCVE/nxgy9lK90bOtxOjOzZ82+NAuI6SmxgAoU5Ac9LgbjdBtgH17y/mvwSs9kv1PHwy6SE9NRWTc8ezu3iUgs0FBFATHyY4d2TB5tQcyHCnaOMXQB+ouyFybRew28B01Gc/qeIx8=",
    "MillisBehindLatest": 0
}

>aws kinesis delete-stream --stream-name testStream --endpoint-url http://localhost:7000
>aws kinesis list-streams --endpoint-url http://localhost:7000
{
    "StreamNames": []
}
```

### 참조
* kinesalite https://github.com/mhart/kinesalite
* AWS CLI 설치 https://docs.aws.amazon.com/ko_kr/cli/latest/userguide/awscli-install-windows.html