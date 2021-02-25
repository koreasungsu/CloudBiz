# AWS EC2 

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash

. ~/.nvm/nvm.sh
nvm install node

node -e "console.log('Running Node.js ' + process.version)"



aws ecr create-repository --repository-name get-customer --image-scanning-configuration scanOnPush=true

docker tag get-customer:latest <accountID>.dkr.ecr.ap-northeast-2.amazonaws.com/get-customer:latest
docker tag get-customer:latest 704431722182.dkr.ecr.ap-northeast-2.amazonaws.com/get-customer:latest # 한국 아직 지원 안됨
docker tag get-customer:latest 704431722182.dkr.ecr.ap-northeast-1.amazonaws.com/get-customer:latest 


aws ecr get-login-password | docker login --username AWS --password-stdin 704431722182.dkr.ecr.ap-northeast-1.amazonaws.com


docker push <accountID>.dkr.ecr.<region>.amazonaws.com/get-customer:latest
docker push 704431722182.dkr.ecr.ap-northeast-1.amazonaws.com/get-customer:latest




