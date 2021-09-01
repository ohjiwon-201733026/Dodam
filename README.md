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

