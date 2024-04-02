# Flutter webview

### 1. 비교 대상
1. [앱에서 웹 브라우저로 이동해서 페이지 보기 - 공식 문서](https://pub.dev/packages/url_launcher)
2. [앱 안에서 웹 브라우저 페이지 보기 - 공식 문서](https://pub.dev/packages/webview_flutter)
  +) [안드로이드 확장판](https://pub.dev/packages/webview_flutter_android)
3. [위와 동일하지만, 다른 라이브러리 - 공식 문서](https://pub.dev/packages/flutter_inappwebview)

<br>

### 2. webView vs flutter_inappwebview
1. webView
   1) WebViewController 사용 가능
   2) IOS, Android 전용 확장 라이브러리 존재
   3) LocalHost 구동 불가능
   4) 스크롤 컨트롤 불가능 // 아직 사용 안 해봐서 모름

2. flutter_inappwebview
   1) 무거운 라이브러리 // 속도, 일처리 등
   2) 사용하지 않는 기능 많이 보유함
   3) LocalHost 구동 가능
   4) JavaScriptChannel 방식 지원
   5) 각 플랫폼 옵션 지원

<br>

### 3. [webview 사용 방법](https://velog.io/@tygerhwang/Flutter-WebView-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-1%ED%8E%B8) // 위에 언급한 공식 문서를 참고하는 것을 추천함
1. `$ flutter pub add webview_flutter`
2. pubspec.yaml 파일 확인
```
dependencies:
  webview_flutter: ^4.7.0
```
3. `$ import 'package:webview_flutter/webview_flutter.dart';` 사용
4. 예시 코드
```
import 'package:webview_flutter/webview_flutter.dart';

final Uri url = Uri.parse('URL 넣으세요');

class ChatBotPage extends StatefulWidget {
  @override
  ChatBotPageState createState() => ChatBotPageState();
}

class ChatBotPageState extends State<ChatBotPage> {
  WebViewController? _webViewController; // webview_flutter 변수 선언

  void initState() {
    _webViewController = WebViewController() // webview_flutter 사용
      ..loadRequest(Uri.parse(
          'https://langchaindaegutour-y99rwahhnv9tmrvkrin8sb.streamlit.app/'))
      ..setJavaScriptMode(JavaScriptMode.unrestricted);
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Flutter Simple Example1')),
      body: WebViewWidget(controller: _webViewController!), // 컨트롤러 사용
    );
  }
}

```



<br>

### 3. 참고
1. [Library 모음 블로그](https://nomad-programmer.tistory.com/256)
