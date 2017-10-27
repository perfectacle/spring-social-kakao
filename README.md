# spring-social-kakao
spring-social-facebook 을 모방하여 만든 kakao api 호출을 위한 library.

추가 작업 필요 항목
------------------------------------------------------
- 이미지 파일 업로드 시 n개의 파일 업로드 과정에 gif animation 파일이 포함 되었을때 gif animation 파일을 제외한 나머지 파일 필터링

이슈사항
------------------------------------------------------
- <s>프로젝트가 MS949 인코딩으로 생성되었음. UTF-8으로의 변경 필요</s> clear
- [<s>Authorization: KakaoAK {adminKey} 400 에러에 의해 기능 사용불가 버그(admin key를 사용하는 모든 API)</s>](https://github.com/bongki/spring-social-kakao/issues/1) clear

### maven으로 변경 (2017.10.27)
---
jcenter에 링크를 대행해주는 bintray에 업로드하기 위해 maven으로 변경.  

모든 설명은 mac os 기준으로 설명하겠다.  
bintray에 업로드 하기 위해서는 우선 maven을 설치해야한다.  
brew로 설치하는 게 가장 간편한 것 같다.  
```bash
brew update
brew install maven
```

bintray의 api키를 프로젝트 디렉토리에 넣으면 깃헙에 올라 갈 위험이 있다.  
그리고 아래 디렉토리에 settings.xml을 만들자.  
```bash
touch ~/.m2/settings.xml
```

아래 내용을 복붙하자.  
```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd"
        xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
    <servers>
        <!-- server 부분은 bintray에 맞게 수정해야한다. -->
        <server>
            <id>lib_name</id>
            <username>user_name</username>
            <password>api_key</password>
        </server>
    </servers>
    <profiles>
        <profile>
            <repositories>
                <repository>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <id>central</id>
                    <name>bintray</name>
                    <url>http://jcenter.bintray.com</url>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <id>central</id>
                    <name>bintray-plugins</name>
                    <url>http://jcenter.bintray.com</url>
                </pluginRepository>
            </pluginRepositories>
            <id>bintray</id>
        </profile>
    </profiles>
    <activeProfiles>
        <activeProfile>bintray</activeProfile>
    </activeProfiles>
</settings>
```

bintray에 deploy 하려면 아래 명령어를 실행하자.  
```bash
mvn clean deploy
```

2015.02.12
------------------------------------------------------
- spring social facebook을 참고하여 만든 RestTemplate 이외에 admin key 사용을 위한 RestTemplate 객체 추가
- admin key를 사용하는 api 호출 부분 추가한 RestTemplate 사용하도록 수정
- 버전 넘버링 0.4.0 에서 1.0.0으로 변경
- MS949 인코딩 상태에서 개발되었던 소스 UTF-8 인코딩 으로 변경. 변경시 깨지는 한글데이터 복구

2015.02.11
------------------------------------------------------
- admin key 사용 방식 변경 (필요 메서드 파라메터에서 KakaoTemplate 생성자 파라메터로 변경)
- 사용자 관리 > 사용자 리스트 요청 API호출 추가 (admin key 사용)
- 사용자 관리 > 사용자 정보 요청 API호출 추가 (admin key 사용)
- 푸시 알림 > 모든 API 호출 추가 (admin key 사용)

2015.02.10
------------------------------------------------------
- 사용자 관리 사용자 정보 저장 API호출 추가
- 사용자 정보에 추가하는 Custom field에 대하여 사용자 정보 조회 시 응답 데이터에 맵핑이 정상처리 될 수 있도록 KakaoObject 에 어노테이션(@JsonAnySetter, @JsonAnyGetter) 추가
- 사용자 관리 로그아웃 API호출 추가
- 사용자 관리 앱연결 API호출 추가

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
