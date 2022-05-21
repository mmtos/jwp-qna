# 요구사항 정리
## 1단계 
  - 주어진 DDL에 맞게 엔티티 클래스 작성
  - 주어진 DDL에 맞게 리포지토리 클래스 작성
  - DataJpaTest로 테스트를 작성한다.
## 2단계 
  - 객체지향적인 설계로 엔티티를 리팩토링한다.

# 연관관계(연관관계 매핑 전략)
  - Answer : Question = N : 1 (양방향, 외래키관리자 = Answer)
  - Answer : User = N : 1 (단방향, 외래키관리자 = Answer)
  - Question : User = N : 1 (단방향, 외래키관리자 = Question)
  - DeleteHistory : Answer = 1 : 1 (필요시 추후 매핑)
  - DeleteHistory : Question = 1 : 1 (필요시 추후 매핑)
  - DeleteHistory : User = N : 1 (단방향, 외래키관리자 = DeleteHistory)

# 작업로그
 - [X] Answer에서 시작하는 연관관계 매핑
 - [X] 테스트 코드 리팩토링
   - [X] 테스트코드에만 사용되던 생성자 제거 (identity 키생성 전략에선 필요없음)
     - [X] User
     - [X] Answer
     - [X] Question
   - [X] 테스트 클래스의 테스트 픽스처 상수 제거 ( 테스트 메서드에서 작업한 내역들이 해당 픽스처에 남아 있는 문제 )
     - [X] AnswerTest
     - [X] QuestionTest
     - [X] UserTest
   - [X] QnaServiceTest의 Mock Repository 제거 후 JpaRepository로 변경
 - [X] Question에서 시작하는 연관관계 매핑
   - 연관관계 편의메서드 작성
 - [X] DeleteHistory에서 시작하는 연관관계 매핑

# 리뷰 내용 반영
## 1단계 
  - [X] BaseEntity에서 id제외하기
  - [X] Exception 패키지 생성 
  - [X] Test 클래스에 @DirtiesContext 제거
  - [X] 테스트 실행시 @EnableJpaAuditing 적용되도록 변경

