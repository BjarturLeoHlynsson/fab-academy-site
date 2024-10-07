# Principles and Practices

## Assignment

- Set up a documentation website using GitLab.
- Plan and sketch a potential final project.

More information can be found at [Fab Academy Schedule](https://fabacademy.org/2025/schedule.html).

## Pre Fab

I began by following these [instructions](https://www.fabisa.is/N%C3%A1msefni/Pre-Fab/1-heimasidugerd/) provided by [Svavar Konradsson](https://fabacademy.org/2023/labs/isafjordur/students/svavar-konradsson/index.html), which were very helpful in setting up [MKDocs](https://www.mkdocs.org/). MKDocs is a simplified version of HTML that uses Markdown. There are numerous themes available, but I decided to use the [Material](https://squidfunk.github.io/mkdocs-material/) theme.

### Setting Up the Website on GitHub

To get started, I downloaded the following:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Python](https://www.python.org/)
- [Git](https://git-scm.com/)

After installing these tools, I created a repository on [GitHub](https://github.com/) to store my project and host the website using GitHub Pages. On my machine, I created a folder named 'Code' on my C: drive. Within the 'Code' folder, I created a subfolder to store the website files during development.

After completing the setup, I opened VS Code, navigated to the 'Code' folder, and selected my project folder. Next, I needed to install MkDocs, so I opened the terminal and typed:

```bash
pip install mkdocs-material
```

This command installed all the necessary dependencies. Afterwards, I typed:

```bash
mkdocs new .
```

This command created a folder containing all the required resources for MKDocs, which looked like this:

```plaintext
├─ docs/
│  └─ index.md
└─ mkdocs.yml
```

When all that was done, I went into the `mkdocs.yml` file and typed:

```yaml
site_name: Bjartur's Fab Academy Journey

theme:
  name: material
```

This told MKDocs I wanted to use the Material theme. To check everything was successful, I went into the terminal and typed:

```bash
mkdocs serve
```

That opened a local website that I could use to see how my website looks even when coding!

Once I had checked that everything was working, I needed to get the website to GitHub. That was a bit more complicated than I thought, but in the end, it worked. Let's go through how I did that!

To get started, I connected VS Code and Git to my GitHub account. To log in with Git, I needed to open up the terminal and type:

```bash
git config --global user.name "name"
git config --global user.email "email@example.com"
```

After connecting GitHub to VS Code and logging in with Git, I could finally send my page to my GitHub repository. This was done by pressing Source Control (Ctrl + Shift + G) on the sidebar, which for me looked a little something like this:

![Source Control](../images/VS-Code-Git-Panel.png){: style="width:20%"}

Then you just press sync, choose your desired repository on the top, and then press Commit. Well done! Your website is now on GitHub. Afterwards, we want to get a functional website hosted, so we need to use GitHub Pages. First, open up GitHub, log in, and open up your repository. So you should be on this page:

![GitHub Repository Main Page](../images/Github-Repo.png){:style="width:100%"}

Before i set up GitHub Pages, i needed to tell GitHub that this is an MKDocs site. To do that i followed these [these instructions](https://squidfunk.github.io/mkdocs-material/publishing-your-site/), I told me i need to make a GitHub `"Action"`. To make a GitHub Action, went to the top bar and opened up Actions:

(INSERT HERE ACTIONS TUTORIAL IMAGES!!)

```yaml
name: MK-Docs 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configure Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v4
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```

After setting up Actions, i needed to deploy my page using GitHub Pages. To configure Pages, i opened up `settings`:

![GitHub Repository Settings Page](../images/Github-Repo-Settings.png){:style="width:100%"}

In settings, i opened the `Pages` tab:

![GitHub Repository Pages Page](../images/Github-Settings-Pages.png){:style="width:100%"}

There i configured GitHub to use the gh-pages branch and told it to use the root folder so afterwards it looked a little something like this:

![Github Page Settings](../images/Github-Page-Settings.png)

After around 20 seconds, i reloaded the page and at the top there was a pop-up that looked like this:

![Github Pages Pop-up](../images/Github%20-%20Pages.png)

Then i could press `Visit Site` and one the second try everything went correctly, i now had a working website that anyone can access!

### Compressing Images
