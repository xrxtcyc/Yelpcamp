１．서론 

본 논문은 웹 기반 캠프사이트 관리 시스템의 설계 및 구현을 주제로 합니다. 이 시스템은 JavaScript, Express, MongoDB (Atlas), Node.js를 사용하여 개발되었으며, 사용자 인증 및 보안, 지도 시각화 및 클라우드 기반 이미지 관리를 포함한 기능을 제공합니다.

２. 프로젝트 구조


<img width="256" height="368" alt="image" src="https://github.com/user-attachments/assets/f0348376-d019-4585-a740-25b79858b987" /> 

(그림 3. 프로젝트 구조)

이 Node.js 및 Express 기반 웹 애플리케이션 프로젝트는 모듈화된 디렉토리 구조로 구성되어 있습니다. cloudi-nary는 이미지 업로드 설정을, controllers는 비즈니스 로직을, models는 데이터베이스 스키마를 담당합니다. routes는 URL 경로와 로직을 연결하고, views는 서버에서 렌더링할 템플릿을 포함합니다. public에는 정적 파일이, utils에는 재사용 가능한 헬퍼 함수가 있습니다. seeds는 초기 데이터를 삽입하는 스크립트, .env는 환경 변수 파일입니다. app.js는 서버 설정 및 진입점 파일, middleware.js는 공통 미들웨어 함수, package.json은 프로젝트 정보와 종속성을 정의하며, schemas.js는 데이터 검증에 사용됩니다.
1. cloudinary: Cloudinary와 관련된 설정이나 모듈 파일이 포함된 디렉토리로, 이미지 업로드 및 저장에 사용될 가능성이 있습니다. 
2. controllers: 애플리케이션의 비즈니스 로직이 포함된 디렉토리로, 요청을 처리하고 데이터를 조작하거나 반환하는 코드가 여기에 있을 것입니다. 
3. models: 데이터베이스 스키마와 모델을 정의하는 디렉토리입니다. 주로 Mongoose를 사용하여 MongoDB 스키마와 연결하는 코드가 포함됩니다. 
4. public: 정적 파일(예: CSS, JavaScript, 이미지 등)을 포함하는 디렉토리입니다. 클라이언트 측에서 액세스할 수 있는 리소스를 여기에 저장합니다.
5. routes: 각 요청 URL과 컨트롤러의 기능을 연결하는 라우터 파일이 들어 있는 디렉토리입니다. Express 라우팅 로직이 여기에 있습니다.
6. seeds: 데이터베이스에 초기 데이터(시드 데이터)를 넣기 위한 스크립트가 포함된 디렉토리입니다.
7. utils: 유틸리티 함수나 헬퍼 모듈을 저장하는 디렉토리로, 프로젝트 전반에 걸쳐 반복적으로 사용되는 코드가 포함될 수 있습니다.
8. views: 서버 측에서 렌더링할 뷰 파일(HTML, EJS 등)이 포함된 디렉토리입니다. 주로 클라이언트에게 전달할 페이지 템플릿이 여기에 위치합니다


  이 프로젝트는 JavaScript, Express, MongoDB (Atlas), Node.js 를 사용하여 
구축된 포괄적인 캠프사이트 관리 웹 애플리케이션입니다. 초기 데이터베이스는 기본 
캠프사이트로 시딩되어 있으며, 사용자가 직접 콘텐츠를 생성할 수 있는 기능을 
제공합니다. 등록된 사용자들은 자신만의 캠프장을 생성하고, 리뷰를 작성 및 수정할 수 
있으며, 자신의 콘텐츠에 대한 수정 및 삭제 권한을 갖습니다. Passport 를 통해 사용자 
인증 및 권한 부여를 구현하여 보안을 강화하였고, Helmet 을 이용해 HTTP 헤더 
설정으로 보안을 추가하며, Express-Mongo-Sanitize 를 사용해 삽입 공격을 방지합니다. 
시각적 요소는 Mapbox를 통해 풍부하게 표현되며, 각 캠프장의 위치를 보여주는 지도와 
클러스터 지도가 제공됩니다. 모든 사용자 업로드 이미지와 애플리케이션 생성에 사용된 
이미지는 Cloudinary 에 저장 및 관리되어 효율적인 미디어 제공을 지원합니다. 이러한 
구성은 사용자가 원활하게 이미지를 가져와 볼 수 있게 하며, 웹 개발의 최신 기술과 
모범 사례에 기반한 보안적이고 사용자 친화적인 캠프사이트 플랫폼을 제공합니다.

3. 결과 분석

그림들은 구현 결과물이다. 본 섹션에서는 구현된 로그인 및 로그아웃, 회원가입 ,메인페이지, 새 캠핑장 등록, 캠핑장 평점, 인덱스 페이지(모든 캠프장 표시) 및 클러스터 지도 화면들에 대해 소개한다.

 <img width="938" height="503" alt="image" src="https://github.com/user-attachments/assets/71d876a4-5cde-45b3-8665-2a634a55dad3" />

(그림 13 홈페이지)

앱 초기 진입 시 나오는 페이지로 가운데 있는 View Campgrounds 클릭 시 인덱스 페이지(모든 캠프장 표시) 및 클러스터 지도 화면으로 이동한다. 오른쪽 상단에 있는 navbar을 통해서 Home, Campground , Login, Register 로 이동 할 수 있다. 
 
<img width="474" height="461" alt="image" src="https://github.com/user-attachments/assets/6dd71e8a-8ff8-424a-b052-b67400e8256a" />

(그림 14 회원가입)

<img width="433" height="472" alt="image" src="https://github.com/user-attachments/assets/8ac69eb5-d9e1-410b-af9f-1caea76fab8b" />

(그림15 경고 메시지 표시)

Username에 사용자 이름 Email에 이메일 주소 Password에 비밀번호를 등록할 수 있다. 부트스트랩을 이용하여 UI를 디자인하였다. Form Validation을 이용하여 미 입력 시 경고 메시지를 출력한다.

 <img width="1089" height="487" alt="image" src="https://github.com/user-attachments/assets/89d1c240-8044-44de-8624-76d57d90f3e7" />

(그림 16 인덱스 페이지(모든 캠프장 표시) 및 클러스터 지도 화면)

Navbar에 있는 Campgrounds클릭 시 등록된 모든 Campground 표시 및 View 버튼을 통해 평점 확인 가능하다. 
  
<img width="511" height="579" alt="image" src="https://github.com/user-attachments/assets/bfa720dc-f6a1-4b45-a368-bb5fd42c2f53" />
(그림 17 등록 아이디 로그인 시 평점 화면)

<img width="533" height="588" alt="image" src="https://github.com/user-attachments/assets/8e1a2eb9-ef38-4c53-b7f6-94241828bd94" />

(그림 18 다른 아이디 로그인 시 평점 화면)
등록 아이디로 로그인한 경우 수정 및 삭제 가능하며 다른 아이디인 경우 수정 및 삭제는 불가하지만 평점 확인 가능하다. 
 <img width="432" height="588" alt="image" src="https://github.com/user-attachments/assets/0a0c0b50-dc08-408a-8188-6fa625cbeba8" />

(그림 19 Register 버튼 클릭 시 나오는 화면)
Register 버튼 클릭 시 이름, 주소, 사진, 가격, 설명 등 세부 사항 등록 가능하다.
 <img width="646" height="517" alt="image" src="https://github.com/user-attachments/assets/689dbf3c-1cd7-4228-9657-81659646eabe" />
<img width="646" height="517" alt="image" src="https://github.com/user-attachments/assets/c675ca7d-8d70-487f-8168-bde8ca2f6950" />

(그림 20로그인 안 하고 Register 버튼 클릭 시 나오는 세션 메시지)

 <img width="658" height="165" alt="image" src="https://github.com/user-attachments/assets/57d22ea9-c61e-43c5-b67a-af2b69466911" />

(그림 21로그인 시 나오는 세션 메시지)
 <img width="598" height="691" alt="image" src="https://github.com/user-attachments/assets/32a78682-0f68-42ab-9ac2-dbf8337524ca" />

(그림 22 캠핑 사이트 등록 후 나오는 페이지)
 <img width="666" height="266" alt="image" src="https://github.com/user-attachments/assets/cc829876-8f5e-48bf-a0d4-060fea82003c" />

(그림 23 캠핑 사이트 등록 후 All Campgrounds나오는 화면)
 <img width="759" height="567" alt="image" src="https://github.com/user-attachments/assets/27e18bbd-5f91-4fb0-994f-00b598126f21" />

(그림 24등록 후 나오는 Mapbox 화면)

