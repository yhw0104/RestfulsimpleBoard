# RestfulsimpleBoard

Controller 하나로만 만들었던 SimpleBoard를 Restful하게 바꿔보는 레파지토리


11/15
---
BoardController에 있던 게시글 추가 메서드를 Controller에는 RequestMapping를 RestController에는 PostMapping로 나눔

Write.html에 js를 삽입해 "등록"버튼을 클릭 할 때 DB에 data가 입력

11/16
---
BoardController에 있던 게시글 목록 메서드를 RestController에 삽입
  - 게시글 목록은 기본 localhost:8080 주소에 바로 데이터를 받아야 하므로 RequestMapping은 사용하지 않음

List.html에 js 삽입 -> vue.js를 사용하여 페이지 실행시 게시글 목록이 나오게 만듬

11/17~11/23
---
게시글 상세조회 페이지, 게시글 수정 페이지 완성
 - jquery를 사용하여 RestController의 GetMapping을 이용하여 데이터를 ajax로 받아옴
 - button태그 클릭시 다음 페이지로 넘어가게 js 작성
 - 게시글 수정 페이지로 넘어갈 때 get방식으로 데이터를 받아옴(value로 데이터를 받아와 input태그 안에 데이터 넣기)
 
 게시글 수정 RestController 작성
 - update.html에서 put 방식을 이용하여 데이터 수정 (작성중)

11/24
---
게시글 수정 완성
 - 게시글 수정페이지와 상세조회 페이지 get방식 호출 같아 게시글 수정페이지 GetMapping 삭제 (메모리 낭비 최소화)
 - 람다, 컬렉션 프레임워크 이용하여 BoardService.java에 수정 메서드 추가
 - ajax를 사용하여 데이터 

게시글 삭제
 - delete 메서드 RestController에 작성
 - detail.html에 ajax를 사용하여 delete 방식으로 게시글 삭제 코드 작성중
  - postman으로 게시글 삭제 됨(삭제 버튼 클릭시 메인 페이지로 안넘어감 -> ajax 수정 필요)

11/27
---
게시글 삭제
 - ajax 문제 (페이지 이동이 안됨)

11/28
---
게시글 삭제
 - detail.html 삭제 버튼이 \<form\>태그를 사용하고 있어서 ajax처리가 안되었었음
 - \<form\>태그 삭제
 - 게시글 삭제 완성
 
---
url 자원 낭비
 - url 자원을 낭비 하지 않게 location.href를 "/" 로 변경하여 BoardController.java의 삭제 메서드를 지움
 
게시글 삭제 메서드 return 값 생성
 - Object 타입 이용 return 값으로 데이터 삭제
 
 11/29
 ---
 게시글 삭제
 - Object 반환타입이 아니라 상태코드 반환을 위한 return 값을 주기 위해 변경
 - ResponseEntity를 사용하여 게시글 삭제 정상 처리 됐을 때는 OK 반환
 - 게시글 삭제 오류일 때는 BAD_REQUEST 반환
 
 12/4
 ---
 List.html 게시글 메인 페이지에서 사용한 vue.js 공부
