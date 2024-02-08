# Flutter installing

### 1. 설치 및 환경설정
1. [Flutter Download](https://docs.flutter.dev/get-started/install) // Flutter 다운로드 후 설치
2. [Android Studio Download](https://developer.android.com/studio) // Android Studio 다운로드 후 설치
3. "Android Studio" 실행 후, 왼쪽 바에서 "Plugins" 클릭
   1) "Flutter" 설치
   2) "Atom OneDark" 설치
4. "Android Studio" 왼쪽 바에서 "Projects" 클릭 -> "More Actions" 클릭 -> "SDK Manager" 클릭 -> 바 - "SDK Tools" -> "Android  SDK Command-line Tools" 설치 후 확인
5. 시스템 환경변수 편집 -> 환경변수 -> "PATH" 더블 클릭 -> "새로 만들기" 클릭 -> `flutter 폴더 내 bin의 경로` 추가 후 확인
6. [Visual Studio 설치](https://visualstudio.microsoft.com/downloads/) // VS 다운로드 후 설치
   1) `Desktop development with C++` 체크 후 필수 설치
       
<br>

### 2. VS - Flutter 연동
1. VS 실행 후 "확장(Extentions)" 클릭
2. 검색창에 "Flutter" 입력 후 설치
3. `Ctrl + Shift + P` 누르고, "Flutter: Run Flutter Doctor" 클릭 및 설치
4. 터미널 창에 `flutter doctor --android-licenses` 입력 및 y
   1) 안될시, `!` 또는 `X`로 표시된 부분 읽고 문제 해결하기
   2) Visual Studio - C++ 설치되었는지 확인
   3) '설정 - 개발자 모드' 설정 되어있는지 확인
6. `Ctrl + Shift + P` 누르고, "Flutter: New Project" 클릭 및 "Application" 클릭
7. 프로젝트 폴더 생성 및 이름 설정
8. 실행할 때에는 `F5` 또는 `Ctrl + F5` 누르기

<br>

### 3. 프로젝트 생성
1. "Android Studio" 또는 "VS CODE" 프로그램 실행
2. "New Flutter Project" 클릭
3. Flutter 선택 후 "Flutter SDK path - flutter 설치 경로" 맞는지 확인
4. 프로젝트 명 작성 + 위치 확인 후 프로젝트 생성
5. "프로젝트 명" -> "lib 폴더" -> "main.dart" (== 메인 페이지) // 소문자 + 언더바(_)만 가능
   
// Android Studio는 6, 7번까지 모두 시행

6. test -> analysis_options.yaml -> rules에 다음 코드 입력 // Lint를 끄는 코드
   1) `$ prefer_typing_uninitialized_variables : false`
   2) `$ prefer_const_constructors_in_immutables : false`
   3) `$ prefer_const_constructors : false`
   4) `$ avoid_print : false`
7. main() 아래 다 지우고, `stless 입력 후 탭키` 후 `MyApp` 입력 + `return MaterialApp( home : );` 작성


```
void main(){
   runApp(const MyApp());
}

//stless 입력 후 Tap키
class MyApp extends StatelessWidget{
   const MyApp({Key? key}) : super(key: key);
   @override
   Widget build(BuildContext context) {
      return MaterialApp(
         home:
      );
   }
}
```

<br>

### 4. 프로젝트 시작
1. 실행
   1) 웹 화면으로 실행 (Chrome) : "F5" 또는 "Ctrl + F5"
   2) 휴대폰 화면으로 실행 (Android) : Emulator 실행
      [다음을 참고](https://parkjh7764.tistory.com/172)
2. 기본 위젯
   1) 글자
      `$ home: Text('...')`
   2) 이미지
      `$ home: Image.asset('...이미지 경로...')` // 주의할점 : 이미지 넣을 땐 폴더 하나 만들어야함
      1) 프로젝트 이름 우클릭 -> new -> Directory -> 이름 "assets" 입력
      2) "asset" 폴더에 이미지 파일 저장
      3) pubspec.yaml 파일 -> flutter: 에 해당 이미지 등록 // 외부 패키지, 파일 등 모두 저장
         ```
         //flutter -> windows -> pubspec.yaml 파일
         
         flutter:
            assets:
               - assets/      // assets의 모든 파일을 쓰겠다는 뜻
         ```

   4) 아이콘
      `$ home: Icon(Icons.star)` // 아이콘 표 참고
   6) 박스
      1) `$ home: Container( width: 50, height: 50, color: Colors.blue )` // 투명한 박스 보임 주의 + 1LP 단위
      2) `$ home: SizedBox()`
      ```
      // child는 부모 박스의 크기를 따라감
      return MaterialApp(
         home: Center( // 정중앙에 위치함
            child: Container( width : 50, height: 50, color: Colors.blue )
      )
      ```

<br>
