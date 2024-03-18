# How to create Galaxy Emulator

유의할 점 : `RESTAPI POST 기준`

### 1. 과정 정리
1. pubspec.yaml - http 추가
```
(pubspec.yaml)
dependencies:
  flutter:
    sdk: flutter
  http: ^1.1.0 # 백엔드 API 호출
```
2. import
```
import 'dart:convert'; // API 호출
import 'package:http/http.dart' as http; // API 호출 2
```
3. [JSON to DART 함수(1) 생성](https://javiercbk.github.io/json_to_dart/)
```
// 회원 가입 API (1) : 데이터 저장
class signUpAPI {
  String? userEmail;
  String? userName;
  String? userId;
  String? userPassword;
  String? userPasswordCheck;

  signUpAPI(
      {this.userEmail,
      this.userName,
      this.userId,
      this.userPassword,
      this.userPasswordCheck});

  signUpAPI.fromJson(Map<String, dynamic> json) {
    userEmail = json['userEmail'];
    userName = json['userName'];
    userId = json['userId'];
    userPassword = json['userPassword'];
    userPasswordCheck = json['userPasswordCheck'];
  }

  Map<String, dynamic> toJson() {
    // 토큰 또는 (String)아이디 / 이메일로 구분?
    final Map<String, dynamic> data = new Map<String, dynamic>();
    data['userEmail'] = this.userEmail;
    data['userName'] = this.userName;
    data['userId'] = this.userId;
    data['userPassword'] = this.userPassword;
    data['userPasswordCheck'] = this.userPasswordCheck;
    return data;
  }
}
```
5. JSON to DART 함수(2) - API 연결 + 매개변수(데이터) 전달 함수
```
// 회원 가입 API (2) : 데이터 저장 변수 호출 및 API 연결, 매개변수 필수
Future<void> fetchsignUpAPI(email, name, id, password, passwordcheck) async {
  // 데이터 저장 변수 : signUpAPI
  final signUpUser = signUpAPI(
    userEmail: email,
    userName: name,
    userId: id,
    userPassword: password,
    userPasswordCheck: passwordcheck,
  );

  // API 연결
  final response = await http.post(
    Uri.parse('RESTAPI URL 삽입'),
    headers: {"Accept": "application/json"},
    body: signUpUser.toJson(),
  );

  // 회원가입 처리 과정
  // 오류 200 : 미연결
  // 오류 400 : 데이터 처리 오류
  // 201 : 성공
  if (response.statusCode == 201) {
    // 회원가입 성공 시의 처리
    print('회원가입 성공');
    return; // 반환값이 없을 경우 void 반환
  } else {
    // 회원가입 실패 시의 처리
    print('회원가입 실패');
    throw Exception('회원가입 실패: ${response.statusCode}');
  }
}
```
6. State 내 변수 생성
```
  // 변수
  String role = ""; // 사용자 OR 관리자
  String userEmail = "";
  String userName = "";
  String userId = "";
  String userPassword = "";
  String userPasswordCheck = "";
```
8. 함수 생성 + 호출 및 매개변수(데이터) 전달
```
await fetchsignUpAPI(userEmail, userName, userId, userPassword, userPasswordCheck);
```




### 2. 도움 받은 블로그 링크
1. [Flutter RESTAPI 연결, 가장 자세하고 정확하게 설명해줌](https://leteu.tistory.com/7)
2. [RESTAPI 연결 코드 참고, 부과 설명용으로만. 코드가 부정확함](https://jellybeanz.medium.com/how-to-use-flutters-rest-api-f2658b4336cc)
3. [RESTAPI 400 오류 - 데이터 전달 문제](https://velog.io/@asroq1/%EC%97%90%EB%9F%AC%ED%95%B4%EA%B2%B0-React-SpringBoot-%ED%9A%8C%EC%9B%90%EA%B0%80%EC%9E%85-400error-issue)
4. [Encode, Decode, Parse 개념 설명](https://sjoongh.tistory.com/entry/Decode-Encode-Parse-Stringify-%EA%B0%9C%EB%85%90%EA%B3%BC-%EC%82%AC%EC%9A%A9)

      
<br>
