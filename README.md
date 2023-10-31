# github-action-nodejs

## 첫번째 커밋 추가 
```sh
echo "# github-action-nodejs" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/xide-projext/github-action-nodejs.git
git push -u origin main
```

## ec2에 접속하기 

```sh
chmod 400 ../aws/yangjo2023.pem
ssh -i "../aws/yangjo2023.pem" ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com
```

### 폴더 준비
```
# 폴더 준비하기 
.
├── aws
│   └── yangjo2023.pem
├── github-action-nodejs (현재 폴더)
│   ├── README.md
│   └── hsw.md
```

## ec2에 파일 전송하기 

# local 
```sh
touch hongsw.md
touch $(GITHUB_ID).md

scp  -i "../aws/yangjo2023.pem" hongsw.md ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com:/home/ec2-user
scp  -i "../aws/yangjo2023.pem" $(GITHUB_ID).md ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com:/home/ec2-user
```