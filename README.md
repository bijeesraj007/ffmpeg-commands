## merge mp4 and mp3
ffmpeg -i dsa_dashboard.mp4 -i music.mp3 -c:v copy -c:a aac output.mp4


### Cut video
ffmpeg -i output.mp4 -ss 00:00:00 -t 00:00:20 -async 1 cut.mp4

## Merge 2 files and stop at the shortest input length
ffmpeg -i dsa_dashboard.mp4 -i music.mp3  -c:v copy -c:a aac -shortest output7.mp4


## Merge operations
https://stackoverflow.com/questions/11779490/how-to-add-a-new-audio-not-mixing-into-a-video-using-ffmpeg/11783474#11783474
