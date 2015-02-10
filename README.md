# spring-social-kakao
spring-social-facebook 을 모방하여 만든 kakao api 호출을 위한 library.

추가 작업 필요 항목
------------------------------------------------------
- 이미지 파일 업로드 시 n개의 파일 업로드 과정에 gif animation 파일이 포함 되었을때 gif animation 파일을 제외한 나머지 파일 필터링

구현 필요 API 목록
------------------------------------------------------
- 사용자 관리 > 로그아웃 : https://developer.kakao.com/docs/restapi#사용자-관리-로그아웃
- 사용자 관리 > 앱연결 : https://developer.kakao.com/docs/restapi#사용자-관리-앱-연결
- 사용자 관리 > 사용자 리스트 요청 (admin) : https://developer.kakao.com/docs/restapi#사용자-관리-사용자-리스트-요청
- 사용자 관리 > 사용자 정보 요청 (admin) : https://developer.kakao.com/docs/restapi#사용자-관리-사용자-정보-요청
- 푸시 알림 > 모든 API : https://developer.kakao.com/docs/restapi#푸시-알림

2015.02.10
------------------------------------------------------
- 사용자 정보 저장 API호출 추가
- 사용자 정보에 추가하는 Custom field에 대하여 사용자 정보 조회 시 응답 데이터에 맵핑이 정상처리 될 수 있도록 KakaoObject 에 어노테이션(@JsonAnySetter, @JsonAnyGetter) 추가

2015.02.09
------------------------------------------------------
- access token의 상태 조회 API 호출 추가
- 응답 데이터 맵핑을 위한 dmain 객체 KakaoObject 상속 받도록 수정
- KakaoObject.java 에 toJsonString 메서드 추가

2015.01.29
------------------------------------------------------
- 하나의 내 스토리 정보 가져오기 API호출 추가
- 복수의 내 스토리 정보 가져오기 API호출 추가
- 내 스토리 삭제 API호출 추가

2015.01.28
------------------------------------------------------
- 스토리 일반 글 포스팅 API호출 추가
- 스토리 외부 링크 정보 조회 API호출 추가
- 스토리 외부 링크 글 포스팅 API호출 추가
- 스토리 이미지 업로드 API호출 추가
- 스토리 이미지 글 포스팅 API호출 추가

2015.01.27
------------------------------------------------------
- code, accessToken 획득 기능 추가
- 카카오, 카카오 스토리, 카카오 톡 프로파일 정보 조회 API호출 추가 (me)
