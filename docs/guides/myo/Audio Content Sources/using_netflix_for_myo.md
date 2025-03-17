# Netflix Audio for MYO

1.  Open **Netflix** in Web Browser    
2.  Press `F12` to open `Developer Tools`
3.  Go to `Network`
    ![unafm_01.png](/img/unafm_01.png)
4.  Let the episode/movie play for a minute, you can stop the recording to make it easier to filter.
    ![unafm_10.png](/img/unafm_10.png)
5.  Filter results with this string: `?o=`
    ![unafm_02](/img/unafm_02.png)
6.  Sort by size (smallest to largest) by clicking on the size column
    ![unafm_03.png](/img/unafm_03.png)
7.  Guess and check, middle size files (about 100-150kB usually contain the audio, movies tend to be a bit larger)
    ![unafm_04.png](/img/unafm_04.png)
8.  Click on the line you want, copy the url
    ![unafm_05.png](/img/unafm_05.png)
9.  Paste the URL into a separate browser tab and delete the section from `range` until `?` 
    ![unafm_06.png](/img/unafm_06.png)
10. AFTER REMOVING it should look like `net/?o=`
    ![unafm_07.png](/img/unafm_07.png)
11.  Press enter
12.  That will download an unencrypted aac file of bitrate between ~128kpbs - ~192kpbs. The file should be about 20-80mb, this is the size you should expect for audio of an episode/movie. (If the size is wrong, cancel download and repeat steps 7-11)
    ![unafm_08.png](/img/unafm_08.png)
13.  Rename and change file to `.mp4` extension
    ![unafm_09.png](/img/unafm_09.png)
14.  Open and verify it plays the audio
15.  Use [ffmpeg](https://github.com/FFmpeg/FFmpeg) to convert from `.mp4` to `.m4a`
    ```terminal
    ffmpeg -c:a aac_at -i ~/Downloads/[filename].mp4 [filename].m4a
    ```
You may have to specify where your downloads folder is:
    ```terminal
    ffmpeg -c:a aac_at -i /Users/[username]/Downloads/[filename].mp4 [filename].m4a
    ```