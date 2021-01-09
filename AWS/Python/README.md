- EC2
```
### Shinsegae Cloud Biz Team. All right reserved.
#### All region and Instance information ### 단일 계정 EC2 확인 
import boto3
session = boto3.session.Session(profile_name="default")
ec2_cli = boto3.client('ec2')
for region in ec2_cli.describe_regions()["Regions"]:
    ec2_cli = session.client(service_name="ec2", region_name=region["RegionName"])
    print(region["RegionName"])
    try:
        response = ec2_cli.describe_instances()
        for reservation in response["Reservations"]:
            for instance in reservation["Instances"]:
                if 'terminated' == str(instance.get('State').get('Name')) or 'pending' == str(instance.get('State').get('Name')):
                    print("############" + instance.get('State').get('Name'))
                else:
                    try:
                        for tags in instance['Tags']:
                            if tags["Key"] == 'Name':
                                vTag = tags["Value"]
                                print(vTag)
                                print(instance.get('PrivateIpAddress'))
                                print(instance.get('InstanceId'))
                                print("#####################################")
                            else:
                                print("No Tag!!!")
                                print(instance.get('PrivateIpAddress'))
                                print(instance.get('InstanceId'))
                                print("************************************")
                    except Exception as e:
                        print(e)
     except Exception as e1:
        print(e1)
```
- CloudWatch 
```
```

-CloudTrail 

```

```
