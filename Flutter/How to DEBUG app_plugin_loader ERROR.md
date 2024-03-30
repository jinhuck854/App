# build.gradle ERROR

### [+수정) 24.03.30. 온전한 오류 해결 방법](https://github.com/jinhuck854/App/blob/main/Flutter/Flutter%20build.gradle%20Error%20Debuging.md)
1. [해결 방법 참고 블로그](https://velog.io/@koyk0408/Fix-flutter-gradle-%EC%97%90%EB%9F%ACSupport-in-stable-release-3.16.0-Recommended-in-stable-release-3.19.0)
2. [flutter 공식 사이트](https://docs.flutter.dev/release/breaking-changes/flutter-gradle-plugin-apply)

<br>

### 1. 불완전한 해결 방법
1. 오류 코드
```
You are applying Flutter's app_plugin_loader Gradle plugin imperatively using the apply script method, which is deprecated and will be removed in a future release. Migrate to applying Gradle plugins with the declarative plugins block: https://flutter.dev/go/flutter-gradle-plugin-apply
```
2. 해결 방법 (불완전한 방법)
   1) build.gradle 파일 이동
   2) 코드 추가
   ```
   plugins {
    id "com.android.application"
    id "kotlin-android"
    id "dev.flutter.flutter-gradle-plugin"
    // 아래 코드 추가
    id 'app_plugin_loader'
   }
   ```
   3) 빌드 후 다시 빌드할 때, 위 오류가 뜨면 build.gradle 코드에서 추가한 부분을 다시 넣는다.


<br>
