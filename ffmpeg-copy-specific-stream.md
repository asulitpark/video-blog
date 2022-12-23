If your input file has multiple audio streams, you can use map parameters to select a specific audio stream.

##  File information by ffprobe

### Command
The input file consists of one video stream encoded with the h264 video codec and two audio streams encoded with the ac audio codec.
```
ffprobe a.mkv

Input #0, matroska,webm, from 'a.mkv':
Stream #0:0(eng): Video: h264 (High), yuv420p(progressive),
Stream #0:1(eng): Audio: ac3, 48000 Hz, 5.1(side), fltp, 640 kb/s (default)
Stream #0:2(kor): Audio: ac3, 48000 Hz, 5.1(side), fltp, 640 kb/s
```


## Copy By ffmpeg
you can copy video and audio stream by ffmpeg 
### Command
```
ffmpeg -i a.mkv -map 0:0 -c:v copy -map 0:2 -c:a copy a.mp4
```

### Parameter
- `-i a.mkv` : input file
- `-map 0:0 -c:v copy` : copy video stream without transcoding.
- `-map 0:2 -c:a copy` : copy audio stream without transcoding.
- `a.mp4` : output file

## Copy Video And Transcode Audio By AAC

### Command
```
ffmpeg -i a.mkv -map 0:0 -c:v copy -map 0:2 -c:a aac a.mp4
```

### Parameter
- `-i a.mkv` : input file
- `-map 0:0 -c:v copy` : copy video stream without transcoding.
- `-map 0:2 -c:a aac` : transcode audio stream by aac audio codec.
- `a.mp4` : output file
