# How to create Galaxy Emulator

1. [삼성 개발자 사이트 접속](https://developer.samsung.com/)
2. 상단 네비게이션 바 -> `Support` -> `Galaxy Emulator Skin` 클릭
3. 원하는 UI 선택 및 파일 다운로드
   1) Display : 인치 확인
   2) Resolution : 가로 세로 픽셀 확인
   3) DOWNLOAD SKIN 클릭
4. 파일 압축 풀기
   1) Window : `C:\users\이름\AppData\Local\Android\Sdk\skins`
   2) Mac : `~/Library/Android/Sdk/skins`
5. 안드로이드 스튜디오 열기
   1) Create Virtual Device 클릭
   2) New Hardware Profile 클릭
   3) Device Name / Screen size / Resolution 입력
   4) Default Skin -> `... 클릭` -> 다운로드 받은 파일 받기(DOWNLOAD SKIN
   +) 에뮬레이터 디바이스 모양 없애려면, Device Frame 체크 해제
6. VSCode 실행
   1) Ctrl + Shift + P
   2) Flutter: Select
   3) 방금 만든 Emulator 클릭 및 실행
      
<br>
