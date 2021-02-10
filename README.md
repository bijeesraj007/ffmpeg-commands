## merge mp4 and mp3
ffmpeg -i dsa_dashboard.mp4 -i music.mp3 -c:v copy -c:a aac output.mp4


### Cut video
ffmpeg -i output.mp4 -ss 00:00:00 -t 00:00:20 -async 1 cut.mp4
