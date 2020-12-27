# AWS SNS(Simple Notification Service)

## SNS CLI 
```
aws sns create-topic --name email-notifications
{
    "TopicArn": " " 
}
```


```
aws sns subscribe --topic-arn arn:aws:sns:ap-northeast-2: :email-notifications --protocol email --notification-endpoint .com 
```
 E-mail 구독 확인

### 클라우드 와치 RDS 알람 설정
aws cloudwatch put-metric-alarm --alarm-name "--alarm-name rds-storage-alarm-warning" --alarm-description "Alarm when storage less than 25GB" --metric-name "FreeStorageSpace" --namespace "AWS/RDS" --statistic "Average" --unit "Bytes" --period 300 --threshold "26843545600" --comparison-operator "LessThanThreshold" --evaluation-periods 1 --alarm-actions "arn " --dimensions Name=InstanceId,Value=mysql-db01 


