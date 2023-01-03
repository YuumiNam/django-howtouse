['간단한 게시판만들기' 초기설정 참고](https://github.com/YuumiNam/django-howtouse/blob/master/BulletinProject/%EA%B2%8C%EC%8B%9C%ED%8C%90%EC%B4%88%EA%B8%B0%EC%84%A4%EC%A0%95.md)

# django 설치방법

### 1. django 설치
1 terminal에서 새 가상환경 생성 => conda create -n web-env python=3.8 \
![화면 캡처 2023-01-02 175845](https://user-images.githubusercontent.com/114986610/210210982-6187dad6-ce5a-4bdd-aa9d-70a3461a2a71.png)

2 새 가상환경 접속 => conda activate web-env 

3 django 설치 (미리 mysql도 설치) \
conda install -c anaconda django=3.2 \
conda install -c anaconda pymysql


4 파이참 실행 => new project => location설정 => previously configured interpreter체크 \
=> add Interpreter 체크 후 conda Environment => web-env 선택 후 프로젝트 실행 \
![화면 캡처 2023-01-02 181323](https://user-images.githubusercontent.com/114986610/210212351-83bf1b63-23c8-45f2-b800-cc282d25eb6c.png) 


5 (web-env에서 원하는 폴더로 가서) django 프로젝트 생성 \
django-admin startproject board .


6 (web-env에서 프로젝트 생성폴더로 가서) python manage.py startapp bulletin_board
<br/><br/><br/>



### 2. MariaDB database 생성
1 (Root DB에서)
create database django_db default character set utf8mb4;

create user 'django'@'localhost' identified by 'django';
create user 'django'@'%' identified by 'django';

grant all privileges on django_db.* to 'django'@'localhost';    <<<    localhost에서만 접속가능
grant all privileges on django_db.* to 'django'@'%';    <<<    다른 곳에서도 접속 가능

flush privileges;

2 홈으로 가서 만든 DB의 connection 생성
<br/><br/><br/>



### django 사용시 주의할점
data 말고 schema가 변경되는 작업(column변경, table변경 등등)은 mariaDB에서 변경하지말고 \
무조건 jango에서 변경해야함!! \
안그러면 둘 사이의 충돌이생길수있음
