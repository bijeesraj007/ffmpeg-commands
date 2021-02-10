## merge mp4 and mp3
ffmpeg -i dsa_dashboard.mp4 -i music.mp3 -c:v copy -c:a aac output.mp4
