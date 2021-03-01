## merge mp4 and mp3
ffmpeg -i dsa_dashboard.mp4 -i music.mp3 -c:v copy -c:a aac output.mp4


### Cut video
ffmpeg -i output.mp4 -ss 00:00:00 -t 00:00:20 -async 1 cut.mp4

## Merge 2 files and stop at the shortest input length
ffmpeg -i dsa_dashboard.mp4 -i music.mp3  -c:v copy -c:a aac -shortest output7.mp4

## Repeat audio file until video ends and produce new video file [Worked]
ffmpeg -i xpresscue.mov -filter_complex "amovie=music.mp3:loop=0,asetpts=N/SR/TB[aud];[0:a][aud]amix[a]" -map 0:v -map '[a]' -c:v copy -c:a aac -b:a 256k -shortest output.mp4


## Merge operations
https://stackoverflow.com/questions/11779490/how-to-add-a-new-audio-not-mixing-into-a-video-using-ffmpeg/11783474#11783474

## Merge a video file that has audio , with another audio file
ffmpeg -i input.mp4 -i dsa_ad.mp3 -filter_complex "[0:a][1:a]amerge=inputs=2[a]" -map 0:v -map "[a]" -c:v copy -ac 2 -shortest final_dsa_ad.mp4


## Merge a video file that has audio with another audio file. The new Audio file should have low volume (background music)
ffmpeg -i video.mp4 -i religious_music.mp3 -c:v copy \
       -filter_complex "[0:a]aformat=fltp:44100:stereo,apad[0a];[1]aformat=fltp:44100:stereo,volume=.1[1a];[0a][1a]amerge[a]" \
       -map 0:v -map "[a]" -ac 2 -shortest output.mp4

## wave
https://stackoverflow.com/questions/32254818/generating-a-waveform-using-ffmpeg


## Wave with image bg
ffmpeg -i music.mp3 -i bg.jpg -filter_complex "[0:a]showwaves=s=1280x720:mode=line:colors=White,colorkey=0x000000:0.01:0.1,format=yuva420p[v];[1:v]scale=1280:720[bg];[bg][v]overlay[outv]" -map "[outv]" -map 0:a -c:v libx264 -pix_fmt yuv420p -b:a 360k -r:a 44100 video.mp4

# all
https://gist.github.com/tayvano/6e2d456a9897f55025e25035478a3a50


## volume reduce
https://trac.ffmpeg.org/wiki/AudioVolume
ffmpeg -i input.mp4 -filter:a "volume=0.007" output7.mp4


## Many useful commands
https://medium.com/hamza-solutions/ffmpeg-tool-with-flutter-ac1d68c2fddb


## Volume
https://www.maketecheasier.com/normalize-music-files-with-ffmpeg/



## Watermark (including animated)
https://gist.github.com/bennylope/d5d6029fb63648582fed2367ae23cfd6
