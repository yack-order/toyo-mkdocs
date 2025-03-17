# Building with MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.


## Fixing the GitHub Pages Deployment

When mkdocs build the website it starts by deleting the `/site` directory which includes the `CNAME` file required for GitHub Pages to know where to serve the deployed site. We can fix that by overriding the `mkdocs build` command with a powershell alias.


1. Create a PowerShell script file. You can name it `mkbuild.ps1`. Open your favorite text editor and add the following lines to the file:
```
mkdocs build
cd site
"yackorder.org" > CNAME
cd ..
```
2. Save this file in a convenient location.
3. Open your PowerShell session and run the following command:
```
New-Alias mkbuild "Path\To\Your\Script\mkbuild.ps1"
```
4. Replace `Path\To\Your\Script` with the actual path to your `mkbuild.ps1` file. This will create an alias called `mkbuild` that you can use to run the script.
5. To make this alias persistent across PowerShell sessions, you can add it to your PowerShell profile script. 
6. You can create the profile script by running the following command in PowerShell if the profile doesn't already exist:
```
New-Item -Path $PROFILE -ItemType File 
```
7. Open your profile script with:
```
notepad $PROFILE
```
8. Add the alias command to the profile script:
```
New-Alias mkbuild "Path\To\Your\Script\mkbuild.ps1"
```
9. Save and close the profile script.

Now, whenever you type `mkbuild` in PowerShell, it will run your script, execute mkdocs build, and write "yackorder.org" to the CNAME file. 