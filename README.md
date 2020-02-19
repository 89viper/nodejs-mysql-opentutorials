# Nodejs + MySQL

## 01. 실습 준비

강의 링크: https://opentutorials.org/course/3347/21175

1. Nodejs 코드 설정(CRUD - 생성, 읽기, 수정, 삭제)
```
npm install //필요한 모듈 다운로드
```
```
pm2 start main.js --watch		//코드 변동사항 자동 적용
pm2 log			//로그 표시
```
2. 데이터베이스 설정(MySQL 이용)
```
opentutorials 데이터베이스 내에
author 테이블과 topic 테이블 생성
각 테이블에 데이터를 추가
```

## 02. mysql 모듈

강의 링크: https://opentutorials.org/course/3347/21185

1. mysql 모듈 설치
```
npm install --save mysql
```
2. mysql.js파일 생성 후 mysql 예제 붙여넣기

## 03. MySQL로 홈페이지 구현

1. main.js에 mysql 모듈 불러오기
```
var mysql = require('mysql');
```

2. mysql에 연결하기
```
var db = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: '...',
    database: 'opentutorials'
});

db.connect();
```

3. 쿼리를 이용해서 테이블의 데이터 가져오기
```
db.query(`SELECT * FROM topic`, function (err, topics) {
              var title = 'Welcome';
              var description = 'Hello, Node.js';
              var list = template.list(topics);
              var html = template.HTML(title, list,
              `<h2>${title}</h2>${description}`,
              `<a href="/create">create</a>`
              );
              response.writeHead(200);
              response.end(html);
          });
```
