# DoDam-Java
[2020 졸업작품 프로젝트] - 병원예약 웹서비스

## 프로젝트 내용  
> 사용자 위치 주변의 병원, 약국들의 정보를 제공하고 사용자가 병원에 직접 가서 대기할 필요없이 예약을 신청하고 병원 관리자가 예약을 수락되고 병원 방문, 예약 정보도 따로 관리해주는 웹 페이지  

### Video : [https://youtu.be/Zwg7hQlaQZU](url)

### Member
- 오지원
- 서유진

### Skill  
> - 개발 언어 : Java, JavaScript  
> - SpringBoot Gradle  
> - DB : MySQL, AWS RDS  
> - API : Kakao Map Api  
> - 기타 : Tiles   

<br>

### 주요기능  (내가 구현한)
> + 사용자 계정 기능    
>   - 주변 병원, 약국 지도에 보여주고 정보 제공  
>   - 사용자가 선택한 병원 예약 신청  
>   - 마이 페이지에서 사용자의 예약 방문 병원 기록 관리  
>   - 공지/ 자유 게시판  

<br>

### 개발 중 문제 기록
**20.05.04**
>   게시판  
>     + insert에서 공지/자유 설정 가능하도록 -> input 추가, DTO에 컬럼 추가하기  
>     + delete하고나서 테이블이 안보임 -> redirect + category값을 넘겨주기.  
>     + insert하고 취소버튼 누르고 list로 갈때 category번호 넘겨서 리스트 보여주기   
>     + 수정에서 공지/자유 변경 불가능하게 -> disabled 추가해주면 해결   

**20.05.05**  
> 게시판     
>   + 게시물 삽입, 수정 textArea에서 띄어쓰기 Detail 페이지에서 적용 안된다.      
    <pre><code> BoardVo boardDetail = boardMapper.boardDetail(vo.getDd_board_no());boardDetail.setDd_board_contents(boardDetail.getDd_board_contents().replaceAll("\r\n","<br>"));</pre></code>  
>      -> 컨트롤러에서 replace해주기  
>   + 삽입 required  
>   + 게시판 댓글 DB 설계, ReplyVo(댓글 DTO)  
>   + 게시판 댓글 형식(html)   

**20.05.11**  
> + 게시판 완성  
> + KakaoMap 지도 가져오기  
<br>

**20.05.12**
> + 병원, 약국 위치 정보  
> + 내위치 GPS   

<br>

**20.05.13~**
> 게시판  
>   + update 날짜 수정 안됨  
>   + 댓글 순서 반대로 -> sql 쿼리 다시 짜기  
>   + 예약자 테이블을 만들어야하는가?? X  
>       User, Reserve 테이블 join해서 사용 ( 문제 : 병원, 유저, 예약 정보가 필요할 때는 join이 너무 많이 일어난다 )  

<br>

**20.05.21**
> Map 기능  
>       + maps.jsp sweet alert 띄우기  
>       + 같은 시간대 예약하면 sweet alert 띄우기 -> 같은 날짜, 시간대 예약 테이블에 있는지 조회해보기  
>       + main 페이지 만들기  O  

<br>

**문제사항( 회의 결과 )**  
- 사용자가 예약하면 바로 예약되는 것은 X -> 병원이 수락해야 예약이 확정 나는 것으로 하자  
    + Reserve 테이블에 컬럼을 추가해서 예약 상태를 확인할 수 있도록 하자 ( 예약 확정, 예약 거절, 예약 대기 상태 3가지로 )  
    + admin 페이지를 만들자 -> 병원이 이를 수락할 수 있도록  
 <br>

**20.05.25~**  
> myPage 구현  
>       + calendar 넣기  
>           - url이 변하지 않고 DB를 조회해와야한다. ->???   
>           - **AJAX로 비동기 통신** -> url 넘어가지 않고 예약 테이블 조회해와야하므로  
>       + 예약 삭제 기능 - reserve table update
>       + 이전 예약 보기 - reserve table select
>       + 내 정보 수정 - user table update



###개발 도중 일어난 문제들 해결 
1.  
  - 사용자가 예약하면 바로 예약되는 것은 X -> 병원이 수락해야 예약이 확정 나는 것으로 하자   
    + Reserve 테이블에 컬럼을 추가해서 예약 상태를 확인할 수 있도록 하자 ( 예약 확정, 예약 거절, 예약 대기 상태 3가지로 )   
    + admin 페이지를 만들자 -> 병원이 이를 수락할 수 있도록   
 <br>  
2. 많은 join :   
    
    - 예약자 테이블을 만들어야하는가?? X    
         User, Reserve 테이블 join해서 사용 ( 문제 : 병원, 유저, 예약 정보가 필요할 때는 join이 너무 많이 일어난다 )  
    -  해결 방법 : resultMap, lazy Loading  
                 한번에 조회해서 객체에 저장해두기  
