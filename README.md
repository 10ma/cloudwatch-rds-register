# CloudWatch-RDS-Register

RDSメトリクスを利用したアラーム設定を作成する



## Usage

```shell
$ ansible-playbook -i localhost, site.yml
```



## Default

- sns_topic.name: 'alarms' - CloudWatchAlarmのアクション先となるSNSトピック名
- sns_topic.mail: 'alarms@example.com' - CloudWatchAlarmのアクション送信先メールアドレス
- cloudwatch_metrics_DBInstanceIdentifier: 'rds_instance_name' - 監視対象RDSのインスタンス識別子
- rds_disk_sizeGiB: 20 - 監視対象RDSのディスクサイズ(GiB)
- db_class: 'db.t2.micro' - 監視対象RDSのインスタンスクラス



## Metrics

- 開放可能なメモリ(FreeableMemory)
- 空きストレージ容量(FreeStorageSpace)
- データベース接続数(DatabaseConnections)
- CPUクレジット残高(CPU CreditBalance) ※T2インスタンスのみ



## Alarms

- FreeableMemory - インスタンスクラス毎の最大メモリの20％未満
- FreeStorageSpace - 割り当てたディスクサイズ最大値の20％未満
- DatabaseConnections - max_connections設定値の80％以上
- CPU CreditBalance - インスタンスクラス毎のCPUクレジット最大値の50%未満

## 

## Author

@10ma
