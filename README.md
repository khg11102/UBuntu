# Ubuntu 명령어

## 핵심명령어

```
#현재위치
$ pwd

#명령창 지우기
$ claer

#패키지 업데이트, 설치, 업그레이드, 지우기, 찾기
$ sudo apt-get update
$ sudo apt-get install
$ sudo apt-get upgrade
$ sudo apt-get remove [패키지명]
$ sudo apt-cache serch [패키지명]

#소스코드 다운
$ sudo wget -o [파일명] [url]
#git code 다운
$ git clone [url] [디렉토리명]

# USB장치 확인
$ sudo lsusb
$ sudo lsusb -v

#USB캠 확인
$ ls -l /dev/video*

#카메라 포맷확인
$ v4l2-ctl -d /dev/video2 --list-formats-ext

#프로세스 확인
$ ps

#프로세스 강제종료
$ kill [pid]
```



## 디렉토리명령어

```linux
#파일리스트
$ ls
#숨겨진 파일목록 ex) .bashrc
$ ls -al
$ ls -l

#디렉토리 이동
$ cd [디렉토리명]
#뒤로
$ cd ..

#디렉토리 생성
$ sudo mkdir [디렉토리명]
#여러 디렉토리 생성
$ sudo mkdir -p [디렉토리명/디렉토리명/디렉토리명]

#디렉토리 삭제, 관련된 패키지도 삭제, 파일과 설정도 삭제
$ sudo rm -r [디렉토리명]
$ sudo apt remove --auto-remove [패키지명]
$ sudo purge [패키지명]
```



## 파일명령어

```linux
#파일생성
$ sudo touch [파일명]

#파일 삭제
$ sudo rm [디렉토리명]

#파일 복붙
$ sudo cp [파일이름] [복사 후 파일이름]

#파일 이동
$ sudo mv [파일이름] [목적지 파일이름]
$ sudo mv [원래이름] [바꿀이름]

#파일 내용
$ sudo cat [파일명]

#파일편집
$ sudo vi [파일명]
$ sudo nano [파일명]
$ sudo gedit [파일명]
```



## 디스크명령어

```
#장착된 디스크 출력
$ sudo fdisk -l

#마운트된 파티션 리스트
$ df-h

#하드디스크 파티션


#하드디스크 마우트
$ sudo nano /etc/fstab
#맨 밑에다 ex) /dev/sda1(HDD경로)			/home/linux/data(마운트할경로)		auto 		noatime		0		0
$ sudo mount -a

#하드디스크 권한설정
$ cd/data
$ sudo chown User:User .
```



## Tools

```
#CPU 모니터링
$ sudo apt-get install htop
$ htop

#VGA 확인
$ nvidia-smi

#VGA 온도, 메모리 모니터링
$ sudo nvidia-smi daemon
$ gpustat -i

#CPU,VGA 온도, 메모리 모니터링
$ sudo apt-get install -y python-pip; sudo pip install glances[gpu]
$ sudo glances

#크롬설치
$ wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
$ sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
$ sudo apt-get update
$ sudo apt-get install google-chrome-stable
$ sudo rm -rf /etc/apt/sources.list.d/google.list

#터미널 분할툴
$ sudo apt-get install terminator
* 수평 분할 : Ctrl + Shift + O

* 수직 분할 :  : Ctrl + Shift + E

* 다음 창 활성화 : Ctrl + Tab   or   Ctrl + Shift + N

* 이전 창 활성화 : Ctrl + Shift + Tab   or   Ctrl + Shift + P

* 현재 활성화 된 창 닫기 : Ctrl + Shift + W

* 터미네이터 실행 : Ctrl + Alt + T

* 터미네이터 종료 : Ctrl + Shift + Q

* 전체화면 : F11


```
# Ubuntu SSH

## SSH 연결

```
ssh -p622 [계정ID]@ip
password : 계정ID 비밀번호
```



## 업로드, 다운로드

```
#파일 업로드 scp -P [포트번호] [업로드할폴더경로] [타겟서버경로]
scp -P 22 /home/linux/Desktop/test.txt aics@ip:/home/aics/Pictures/

#파일 다운로드 scp -P [포트번호] [다운받을서버경로] [타겟경로]
scp -P 22 aics@ip:/home/aics/Pictures/test.txt /home/linux/Desktop/test.txt
```

## 

## 공유기 연결시

1. 사용중인 공유기에서 포트포워딩 해주기
2. sudo gedit /etc/ssh/sshd_config파일 포트 번호도 변경
3. netstat -anp | grep LISTEM | grep tcp 포트확인
4. sudo service sshd restart

## NVIDIA
```
nvidia-smi
nvidia-smi nvlink -h
nvidia-smi nvlink --status
```

## SAMBA
```
#공유폴더 생성
#유저 추가
sudo smbpasswd -a linux
New SMB password:
Retype nes SMB password:
Added user linux.

#로컬컴퓨터
smb://[ip]
사용자 : linux
비밀번호 : ****
```

## Jupyter Notebook
```
#양방향 파일 변환
ipynb-py-convert in.ipynb out.py
ipynb-py-convert in.py out.ipynb

#주피터 테마설치
pip install jupyterthems
#테마 목록
jt -l
#테마 적용
jt -t monokai
#커스텀 테마
jt -t grade3 -f roboto -fs 12 -altp -tfs 12 -nfs 12 -cellw 80% -T -N
```
