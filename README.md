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
/mnt/c/developments
├── aws
│   └── yangjo2023.pem
├── github-action-nodejs (현재 폴더)
│   ├── README.md
│   └── hsw.md
```

## ec2에 파일 전송하기 

### local (나의 노트북 터미널) 에서 ec2로 파일 전송하기
```sh
pwd
/mnt/c/developments/github-action-nodejs

touch hongsw.md
scp  -i "../aws/yangjo2023.pem" hongsw.md ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com:/home/ec2-user


touch $(GITHUB_ID).md
scp  -i "../aws/yangjo2023.pem" $(GITHUB_ID).md ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com:/home/ec2-user

```


## 압축된 파일을 local에서 ec2로 파일 전송하고, 올라간 압축된 파일을 압축푸는 명령을 local에서 실행
### 1.준비 : 로컬에 파일들을 압축파일로 준비해두고
```sh
mkdir hongsw_files
touch hongsw_files/hongsw_file1.md
touch hongsw_files/hongsw_file2.md
tar -cvf hongsw_files.tar hongsw_files
```

### 2. scp로 원격지로 파일보내기
```sh
scp  -i "../aws/yangjo2023.pem" hongsw_files.tar ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com:/home/ec2-user
```


### 3. ssh로 원격지에 있는 파일을 압축 풀기 
```sh
ssh -i "../aws/yangjo2023.pem" ec2-user@ec2-43-201-209-69.ap-northeast-2.compute.amazonaws.com "tar -xvf hongsw_files.tar"
```
