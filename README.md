１．	서론 – Introduction
본 논문은 웹 기반 캠프사이트 관리 시스템의 설계 및 구현을 주제로 합니다. 이 시스템은 JavaScript, Express, MongoDB (Atlas), Node.js를 사용하여 개발되었으며, 사용자 인증 및 보안, 지도 시각화 및 클라우드 기반 이미지 관리를 포함한 기능을 제공합니다.

 
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
  <img width="474" height="461" alt="image" src="https://github.com/user-attachments/assets/6dd71e8a-8ff8-424a-b052-b67400e8256a" /><img width="433" height="472" alt="image" src="https://github.com/user-attachments/assets/8ac69eb5-d9e1-410b-af9f-1caea76fab8b" />

(그림 14 회원가입)                  (그림15 경고 메시지 표시)
Username에 사용자 이름 Email에 이메일 주소 Password에 비밀번호를 등록할 수 있다. 부트스트랩을 이용하여 UI를 디자인하였다. Form Validation을 이용하여 미 입력 시 경고 메시지를 출력한다.
 
(그림 16 인덱스 페이지(모든 캠프장 표시) 및 클러스터 지도 화면)
Navbar에 있는 Campgrounds클릭 시 등록된 모든 Campground 표시 및 View 버튼을 통해 평점 확인 가능하다. 
  
(그림 17 등록 아이디 로그인 시 평점 화면)       (그림 18 다른 아이디 로그인 시 평점 화면)
등록 아이디로 로그인한 경우 수정 및 삭제 가능하며 다른 아이디인 경우 수정 및 삭제는 불가하지만 평점 확인 가능하다. 
 
(그림 19 Register 버튼 클릭 시 나오는 화면)
Register 버튼 클릭 시 이름, 주소, 사진, 가격, 설명 등 세부 사항 등록 가능하다.
 
(그림 20로그인 안 하고 Register 버튼 클릭 시 나오는 세션 메시지)

 
(그림 21로그인 시 나오는 세션 메시지)
 
(그림 22 캠핑 사이트 등록 후 나오는 페이지)
 
(그림 23 캠핑 사이트 등록 후 All Campgrounds나오는 화면)
 
(그림 24등록 후 나오는 Mapbox 화면)

