# Overdrive ODM and odmpy

## Requirements:

- Install python and odmpy (python is required for odmpy to run)

---

## Part 1: Get the ODM File using Bookmarklet

1. Open up these two pages:
    1. [**bookmarklet.js**](https://gist.github.com/ping/b58ae66359691db1d08f929a9e57a03d)
    2. [**Mr Coles Bookmarklet Creator**](https://mrcoles.com/bookmarklet/)
2. Copy/paste the .js into the Bookmarklet Creator
    ![uslibodm_01.PNG](/img/uslibodm_01.png)
3. Give it a Name, and Click on Convert to bookmarklet
    ![uslibodm_02.PNG](/img/uslibodm_02.png)
4. Drag the button into your bookmark bar
    ![uslibodm_03.PNG](/img/uslibodm_03.png)
5. Navigate to your library’s Overdrive Loans page, then click on your new Bookmark button
    - The ODM download button will appear:
    ![uslibodm_04.PNG](/img/uslibodm_04.png)

6. Download the ODM file

---

## Part 2: Extract ODM file use odmpy

1. Install python (if needed) and odmpy.
    - Follow the installation instructions at: [https://github.com/ping/odmpy](https://github.com/ping/odmpy)
    - If you want to use the merge command (and merge all parts into a single file) you will also need to install [ffmpeg](https://ffmpeg.org/download.html).
2. Run the following script in Command Prompt (change your title to the actual title of your file):
    ```python
    odmpy --retry 3 dl "someBook.odm" --keepcover --chapters  --merge
    ```