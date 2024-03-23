# build.gradle ERROR

### 1. `app_plugin_loader 오류`
1. 오류 코드
```
You are applying Flutter's app_plugin_loader Gradle plugin imperatively using the apply script method, which is deprecated and will be removed in a future release. Migrate to applying Gradle plugins with the declarative plugins block: https://flutter.dev/go/flutter-gradle-plugin-apply
```
2. 해결 방법
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
