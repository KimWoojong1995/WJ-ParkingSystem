# 주차장 무인 결제 시스템 <br />

평소 주차장 이용 시 무인 결제 시스템의 원리와 구조가 궁금했습니다.<br />
단순한 호기심으로 시작해 UML을 작성해보고 MySQL DB 구조를 만들었습니다.<br />
<img width="584" alt="주차장EERDiagram" src="https://user-images.githubusercontent.com/65944245/101730741-ebac3300-3afd-11eb-80ad-6e453cfe1fae.png"><br />
View는 Nunjucks를 사용해 만들었으며 latout.html을 상속해서 전체적인 구조 틀과 로그인, 회원가입, 로그아웃, 정기권 만기일, 관리자 페이지를 보여줍니다.<br />
정규표현식을 사용해 input 값의 차량번호를 입력할 수 있으며 숫자 2~3자리,한글 한 글자,숫자 4자리 조합으로 입력 가능합니다.<br />
결제는 Front에서 현금과 카드결제 로직을 만들었습니다. 현금 결제시 거스름돈을 돌려주고 카드 결제시 실제 카드 결제 작동처럼 setTimeout을 사용하였습니다.<br />
결제는 Front에서 현금과 카드결제 로직을 만들었습니다. 현금 결제시 거스름돈을 돌려주고 카드 결제시 실제 카드 결제 작동처럼 setTimeout을 사용하였습니다.<br />
서버는 Node.js의 express를 사용하였습니다.<br />
비밀번호는 bcrypt를 사용해 DB에 저장되어 안전하게 암호화할 수 있게 하였습니다.<br />
express-session과 express-cookie를 사용해 로그인 상태를 관리합니다.<br />
![만기일표시](https://user-images.githubusercontent.com/65944245/101732269-49da1580-3b00-11eb-8c7d-44e48a9b6e4d.png)<br />
DB는 Sequelize를 사용하며 해당 유저에 대한 테이블을 체크 후 관리자와 회원, 정기권 만료일 등 조건에 따라 view 상단에 표시합니다.<br />
<img width="553" alt="주차기록" src="https://user-images.githubusercontent.com/65944245/101731839-9709b780-3aff-11eb-800c-6b4f30c207fa.png"><br />
<img width="1113" alt="회원기록" src="https://user-images.githubusercontent.com/65944245/101731855-9b35d500-3aff-11eb-8088-87b173a01060.png"><br />
차량 주차 시 주차기록 테이블의 해당 차량 번호와 주차시간, 결제 유무를 체크하며 이미 주차한 차량인지 판별 후 결과 값을 view에 보여줍니다.<br />
차량 출차 시 주차기록 테이블의 출차 시간 유무와 회원 판별, 정기권 보유를 체크 후 이미 출차한 차량인지, 회원 할인 차량인지 일반 차량인지 판별 후 결과 값을 view에 보여줍니다.<br />
정기권 등록 시 회원 테이블의 정기권 만기일을 확인 후 정기권을 보유한 사람이라면 선택한 개월 수 만큼 연장하고 신규라면 선택한 개월 수 만큼 등록 하도록 하였습니다.<br />
![관리자헤더](https://user-images.githubusercontent.com/65944245/101732270-4a72ac00-3b00-11eb-8687-5ea21f710602.png)<br />
관리자의 아이디는 회원 테이블의 admin 유무를 체크 후 로그인 시 view 상단에 관리자 메뉴가 생성되며 관리자 메뉴 선택 시 주차 기록과 회원 기록을 볼 수 있습니다.<br />
![관리자주차기록](https://user-images.githubusercontent.com/65944245/101732267-49417f00-3b00-11eb-91db-1ef80a0339b2.png)<br />
![관리자회원기록](https://user-images.githubusercontent.com/65944245/101732263-4777bb80-3b00-11eb-898f-fe4707e93e88.png)<br />
주차기록과 회원기록은 페이징 기능을 구현하였으며 해당 row 삭제 시 DB에서 삭제되고 삭제 시 접속되있던 페이지로 redirect합니다.<br /><br /><br />

페이징 처리 기능을 구현하면서 잦은 에러와 코드의 문제점 등을 경험하면서 더 많은 학습과 경험이 필요하다 느꼈습니다.<br />
이번 프로젝트로 개발 초기 단계의 구상부터 웹 개발의 전체적인 흐름을 알 수 있었으며 정규표현식의 이해와 session과 cookie에 대한 학습을 하게 되었습니다.<br />
MySQL을 사용함으로써 DB의 작동 순서와 원리, 쿼리 등 많은 경험을 얻었고 앞으로의 개발 시 큰 원동력이 될 것이라 생각합니다.<br />
