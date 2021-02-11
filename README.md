## merge mp4 and mp3
ffmpeg -i dsa_dashboard.mp4 -i music.mp3 -c:v copy -c:a aac output.mp4


### Cut video
ffmpeg -i output.mp4 -ss 00:00:00 -t 00:00:20 -async 1 cut.mp4

## Merge 2 files and stop at the shortest input length
ffmpeg -i dsa_dashboard.mp4 -i music.mp3  -c:v copy -c:a aac -shortest output7.mp4


## Merge operations
https://stackoverflow.com/questions/11779490/how-to-add-a-new-audio-not-mixing-into-a-video-using-ffmpeg/11783474#11783474


## wave
https://stackoverflow.com/questions/32254818/generating-a-waveform-using-ffmpeg


## Wave with image bg
ffmpeg -i music.mp3 -i bg.jpg -filter_complex "[0:a]showwaves=s=1280x720:mode=line:colors=White,colorkey=0x000000:0.01:0.1,format=yuva420p[v];[1:v]scale=1280:720[bg];[bg][v]overlay[outv]" -map "[outv]" -map 0:a -c:v libx264 -pix_fmt yuv420p -b:a 360k -r:a 44100 video.mp4

# all
https://gist.github.com/tayvano/6e2d456a9897f55025e25035478a3a50
