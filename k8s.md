### 설치 및 운영
#### 설치 순서 1
```
eksctl create cluster --name=shinman --version 1.15 --region=ap-northeast-2 --zones=ap-northeast-1a,ap-northeast-1c --without-nodegroup # 한국 리전 Error, 미국리전 가능

eksctl create cluster --name=sungsumart --version 1.15 --region=ap-northeast-2 --without-nodegroup
```
#### 설치 순서 2
```
eksctl utils associate-iam-oidc-provider --region ap-northeast-2 --cluster sungsumart --approve
```
#### 설치 순서 3
### - On-Demand 인스턴스
```
eksctl create nodegroup --cluster=sungsumart --region=ap-northeast-2 --name=data1mart-ng-public1 --node-type=t3.small --nodes=2 \
 --nodes-min=2 --nodes-max=4 --node-volume-size=20 --ssh-access --ssh-public-key=corpseoul --managed --asg-access --external-dns-access --full-ecr-access --appmesh-access --alb-ingress-access 
```
#### - Spot 인스턴스 
```
eksctl create nodegroup --cluster=sungsumart --region=ap-northeast-2 --name=data2mart-ng-public1  --nodes=2 \
 --nodes-min=2 --nodes-max=4 --node-volume-size=20 --ssh-access --ssh-public-key=corpseoul --managed --spot --instance-types=t3.small,t3.medium --asg-access --external-dns-access --full-ecr-access --appmesh-access --alb-ingress-access 



kubectl get nodes -o wide 
```

#### 4

EC2 Security group all open 

#### 5
```
eksctl delete nodegroup --cluster=<clusterName> --name=<nodegroupName>
eksctl delete nodegroup --cluster=sungsumart --name data2mart-ng-public1 
eksctl drain nodegroup --cluster=sungsumart --name=data2mart-ng-public1


eksctl delete --cluster=sungsumart --region ap-northeast-2 # not working

eksctl delete cluster --name sungsumart --region ap-northeast-2 
```

