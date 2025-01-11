Docs:
- Write new files and put them in the `/docs` folder, preferably in some sub folder.
- file a PR to merge into the `main` branch

Images:
- screenshots should use a short-hand for the name of the page that they are meant to be displayed on
- logos, headers, etc should have identifying labels

To build after new changes:
1. I need to download the repo after merging PRs
2. unzip to my working directory
3. `python -m mkdocs serve` to launch locally
4. check for errors on the terminal and resolve in the files
5. `python -m mkdocs build` to compile the static site files
6. uplaod the `/docs` and `mkdocs.yml` file to [this repo](https://github.com/humor4fun/toyo-mkdocs) and merge any changes
7. upload the `/site` folder to the [main site repo](https://github.com/humor4fun/The-Optimistic-Yack-Order) into the `dev` branch
8. File a PR to merge `dev` into `main`
9. Wait 5 minutes for the website to update
