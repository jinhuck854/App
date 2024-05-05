# [Geolocator 11.0.0 (24.05.05 기준)](https://pub.dev/packages/geolocator/install)

### 1. Installing
1. `$ flutter pub add geolocator`
2. pubspec.yaml
  ```
  dependencies:
    geolocator: ^11.0.0
  ```
3. `import 'package:geolocator/geolocator.dart';`
4. android/app/src/main/AndroidManifest.xml
```
manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- 코드 추가 !! 사용자 권한 : 위치 정보 제공 -->
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    ...
</manifest>
```

<br>

### 2. 사용자 위치 권한 설정
1. 오류 : PermissionDeniedException (User denied permissions to access the device's location.)
2. 해결 : `LocationPermission permission = await Geolocator.requestPermission(); // 사용자 위치 권한`

<br>

### 3. VSCode에서 사용법
```
`import 'package:geolocator/geolocator.dart';`

class PostCard extends StatefulWidget {
  @override
  _PostCardState createState() => _PostCardState();
}

class _PostCardState extends State<PostCard>{
  @override
  void initState() {
    super.initState();
    getLocation(); // 1. 사용자 위치 확인
  }

  // getLocation() : 현재 위치 정보 얻기
  Future<void> getLocation() async {
    LocationPermission permission = await Geolocator.requestPermission(); // 사용자 위치 권한
    Position position = await Geolocator.getCurrentPosition(
        desiredAccuracy: LocationAccuracy.high);
    print("위도 + 경도 : ");
    print(position); // 위도 + 경도
  }
}
```

<br>
