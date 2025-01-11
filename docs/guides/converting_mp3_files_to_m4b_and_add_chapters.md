# Converting MP3 Files to m4b and Add Chapters

By [Step-3-Profit](https://www.reddit.com/user/Step-3-Profit/) ([source](https://www.reddit.com/r/audiobooks/comments/zwnxc8/comment/j1w5aug/))

Required Software (Both are free)

- [Audacity](https://www.audacityteam.org/)
- [Audiobook Converter](https://www.recoupler.com/products/audiobookconverter) ([Free](https://github.com/yermak/AudioBookConverter), [Paid](https://store.steampowered.com/app/1529240/AudiobookConverter/))
 
The process is pretty simple. Use Audacity to break down the MP3 file into smaller chunks and export each chapter as it's own file. Then use Audiobook Converter to merge the multiple files into an M4B file containing your chapter data and cover artwork.

Steps to convert single file MP3 audiobook to multi-file MP3s with each chapter as a separate files.

1.  Open Audaci ty and load your audiobook
2.  Use the Magnify+ button to zoom in on the audio graph so you can easily identify breaks between dialog.
3.  Scroll to the start of the book and find the first chapter and measure the amount of silence before the chapter heading (if any). We'll use this as a baseline measurement for the chapter breaks.
4.  Press CTRL+A to select all and go to `Analyze` tool menu and select `Label Sounds`
5.  The default `Label Sounds` work pretty well though you will want to adjust the `Minimum Silence Duration` file based on your baseline measurement earlier. I've found 3-4 seconds works well for most books.
6.  After the tool does its work you'll need to go through each label and verify they are correct and make adjustments as necessary. This is a tedious process but unfortunately unavoidable. Note: if you need to add a new label you can use Edit >> Labels >> Add Label at Selection or CTRL+B. If you find a label you do not need, right-click inside the label and select delete.
7.  After you've made your adjustments and ready to export go to File >> Export >> Export Multiple. The default settings work well but make sure you select Split files based on `Tracks` and Name files `Using Label/Track Name`. Select export when ready. You may also adjust the Quality. I usually set this to 96kbps though because it's just voice data and not music, you can take this as low as 64kpbs to reduce your file sizes and still maintain decent sound.

Someone put together a pretty good walkthrough. Though it uses a slightly older version of Audacity in which the `Silence Finder` menu item has been replaced by `Label Sounds`, the process is essentially the same. [source](https://www.youtube.com/watch?v=FfHC12Xcjlk)

I use Audiobook Converter to combine the audio files into an M4B file containing chapters.

1.  Select the files you want to include in your audiobook and drag them into Audiobook Converter. I've found adding one file at a time works best to give you the most control over how the files will be ordered. The sorting options are fairly limited so this can save you a lot of headaches later on if you need to manually adjust the sorting.
2.  Make sure your files are sorted in the desired order and click `Chapters`
3.  A `Chapters` tab will open containing the list of chapters read from the files. If the list is empty click `Add` to add them. If for what ever reason the list is still empty click `Clear` and try importing again.
4.  Make sure your chapter titles are correct. Right-Click and select `Edit` to adjust. I believe the default is to auto name based on `Chapter` `Chapter No` and `Duration`. I typically uncheck all these options and select `Title` or in some cases `File_Name`. Other times I may need to select None and enter a chapter name manually. Select OK with done
5.  At the bottom of the screen you can set your meta data for the audiobook and attach your cover art. I generally leave the `Quality` settings at their default values.
6.  Click `Start` when your ready to merge the files.