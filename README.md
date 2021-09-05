Media streaming with ExoPlayer
===
The code in this repository accompanies the [Media streaming with ExoPlayer codelab](https://codelabs.developers.google.com/codelabs/exoplayer-intro). If you are looking to get started with [ExoPlayer](https://exoplayer.dev) the codelab is a great place to start.  

## 라이브 커머스 공부 시작

[HLS](https://ko.wikipedia.org/wiki/HTTP_%EB%9D%BC%EC%9D%B4%EB%B8%8C_%EC%8A%A4%ED%8A%B8%EB%A6%AC%EB%B0%8D)는 무엇일까?

애플에서 만든 HTTP 라이브 스트리밍 서비스로 스트림을 작은 단위의 Http 파일형태로 쪼개서 보내준다. 쪼개진 파일들은 2~10초 정도의 트랙으로 끊임없이 전달되며 해상도 등 네트워크 대역폭에 따른 적응형 스트리밍 서비스를 제공해준다.
따라서 클라이언트는 실시간으로 대역폭 혹은 네트워크 상태에 따라 더 좋은 세그먼트로 전환하면 된다.


예) skiing.m3u8, `m3u8` 확장자로 hls의 **마스터 매니페스트 파일**이다. 720p, 360p, 480p, 1080p 해상도 마다의 **미디어 매니페스트** 파일을 가지고 있는 모습

```
  #EXTM3U

  #EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=2000000,CODECS="mp4a.40.2, avc1.4d401f"
  skiing-720p.m3u8

  #EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=375000,CODECS="mp4a.40.2, avc1.4d4015"
  skiing-360p.m3u8

  #EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=750000,CODECS="mp4a.40.2, avc1.4d401e"
  skiing-480p.m3u8

  #EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=3500000,CODECS="mp4a.40.2, avc1.4d401e"
  skiing-1080p.m3u8
```


예) skiing-480p, `ts` 확장자가 2~10초 길이의 하나의 세크먼트
```
#EXTM3U
#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:3
#EXT-X-MEDIA-SEQUENCE:0
#EXT-X-PLAYLIST-TYPE:VOD
#EXTINF:9.97667,
file000.ts
#EXTINF:9.97667,
file001.ts
#EXTINF:9.97667,
file002.ts
#EXTINF:9.97667,
file003.ts
#EXTINF:9.97667,
file004.ts
```


### Android에서는 HLS를 어떻게 사용할까?

Apple에서 만든 이유 덕에 iOS 앱에는 별도의 라이브러리 추가할 필요 없이 그냥 사용이 가능하다고 한다. Android에서는 `Exoplayer`에서 지원해준다.

Exoplayer
- Android 프레임워크에서 제공해주는 것이 아닌 별도의 라이브러리로 제공줌으로써 버전 제어 가능
- HLS 같은 적응형 스트리밍 서비스를 제공해준다.
- MediaPlayer보다 더 좋은 성능, 확장성을 가지고 있다.

단점
- 단순 음악 플레이어 같은 앱이라면 MediaPlayer보다 배터리 효율이 안나옴
- APK 파일의 용량 적지않게 증가







참고
- PIP 모드
