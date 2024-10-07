# Principles and Practices

## Assignment

- Set up a documentation website using GitLab.
- Plan and sketch a potential final project.

More information can be found at [Fab Academy Schedule](https://fabacademy.org/2025/schedule.html).

## Pre Fab

!!! Note "Info!"
    I followed these [instructions](https://www.fabisa.is/N%C3%A1msefni/Pre-Fab/1-heimasidugerd/) provided by [Svavar Konráðsson](https://fabacademy.org/2023/labs/isafjordur/students/svavar-konradsson/index.html) at Fab Lab Isafjörður, which were very helpful in setting up [MKDocs](https://www.mkdocs.org/). MKDocs is a simplified version of HTML that uses Markdown. There are numerous themes available, but I decided to use the [Material](https://squidfunk.github.io/mkdocs-material/) theme.

### Setting Up the Website on GitHub

To get started, I downloaded the following tools:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Python](https://www.python.org/)
- [Git](https://git-scm.com/)

!!! note
    In VS Code, I recommend you install [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python), [Markdown Extension Pack](https://marketplace.visualstudio.com/items?itemName=bat67.markdown-extension-pack), and [YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml). YAML requires a bit more setup to work with MKDocs, which you can find the instructions for [here](https://squidfunk.github.io/mkdocs-material/creating-your-site/#minimal-configuration) inside of the note: **_Recommended: configuration validation and auto-complete._**

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

Then I could open my browser and type [localhost:8000](localhost:8000). That was a local website that I could use to see how my website looks even when coding!

Once I had checked that everything was working, I needed to get the website to GitHub. That was a bit more complicated than I thought, but in the end, it worked. Let's go through how I did that!

To get started, I connected VS Code and Git to my GitHub account. To log in with Git, I needed to open up the terminal and type:

```bash
git config --global user.name "name"
git config --global user.email "email@example.com"
```

After connecting GitHub to VS Code and logging in with Git, I could finally send my page to my GitHub repository. This was done by pressing `Source Control (Ctrl + Shift + G)` on the sidebar, which for me looked a little something like this:

![Source Control](../images/VS-Code-Git-Panel.png){: style="width:20%"}

Then you just press initialize repository, choose your desired repository, and then press Commit and then Sync. Well done! Your website is now on GitHub. Afterwards, we want to get a functional website hosted, so we need to use GitHub Pages. First, open up GitHub, log in, and open up your repository. So you should be on this page:

![GitHub Repository Main Page](../images/Github-Repo.png){:style="width:100%"}

Then I needed to deploy my page using GitHub Pages. To configure Pages, I opened up `settings`:

![GitHub Repository Settings Page](../images/Github-Repo-Settings.png){:style="width:100%"}

In settings, I opened the `Pages` tab:

![GitHub Repository Pages Page](../images/Github-Settings-Pages.png){:style="width:100%"}

There I configured GitHub to use the main branch and told it to use the root folder which didn't work so afterwards I changed it to the docs folder which worked. That looked a little something like this:

![Github Page Settings](../images/Github-Page-Settings-Wrrong.png)

Then I pressed `save` and after around 20 seconds, I reloaded the page and at the top there was a pop-up that looked like this:

![Github Pages Pop-up](../images/Github%20-%20Pages.png)

Then I could press `Visit Site` but when I checked the site it looked like this:

![Not Correctly Setup up Page](../images/Wrong-Page-Setup.png)

Which is not correct so I googled why my page looked like that, I was told that I needed to tell GitHub that this is an MKDocs site. To do that, I followed these [instructions](https://squidfunk.github.io/mkdocs-material/publishing-your-site/), which told me I need to make a GitHub "Action". To make a GitHub Action, I went to the top bar and opened up Actions:

In the Actions tab, I pressed `New workflow` then I pressed:

![Set up a workflow yourself](../images/Github-Workflow.png)

Once that was done, I pasted in this code:

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

and named it `MK-Docs` and then to save it I pressed `commit`.

Then I went back into the `settings` tab, then `pages`, and selected gh-pages as my branch and root as my folder so it looked like this:

![Github Page Settings](../images/Github-Page-Settings.png)

and then my page looked like this:

![Correctly Setup up Page](../images/Correct-Page-Setup.png)

**Success**! I now had a page that anyone can access and a place to document my journey!

### Configuring and Personalizing my website

To begin, I opened the `mkdocs.yml` file and decided to use Svavar Konráðsson's configuration as a base, customizing it to fit my needs. One of the features I added was the ability to switch between light and dark modes using a light bulb icon next to the search bar. Here is the code for that:

```yaml
theme:
  palette:
    - media: "(prefers-color-scheme: light)"  # Toggle for light mode
      scheme: default
      toggle: 
        icon: material/lightbulb
        name: Switch to dark mode
      primary: black
      accent: red
    - media: "(prefers-color-scheme: dark)"   # Toggle for dark mode
      scheme: slate
      toggle:
        icon: material/lightbulb-outline
        name: Switch to light mode
      primary: black 
      accent: red 
```

Next, I changed the font to enhance the readability of the text and code:

```yaml
# This code should go inside the theme section
  font:
    text: Roboto 
    code: Roboto Mono  
```

I also added several useful Markdown extensions to improve the functionality of the site:

```yaml
markdown_extensions:
  - pymdownx.snippets
  - pymdownx.keys
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.inlinehilite
  - pymdownx.superfences
  - pymdownx.tabbed:
      alternate_style: true
  - pymdownx.details
  - admonition
  - attr_list
  - md_in_html
  - pymdownx.arithmatex:
      generic: true
  - pymdownx.tasklist:
      custom_checkbox: true
```

After making these and a few other minor adjustments like changing the icons, I was extremely pleased with the final result!

### Compressing Images

To conserve space and make sure the site loads fast, I needed to compress all of my images. To do that, I downloaded [FFmpeg](https://www.gyan.dev/ffmpeg/builds/?ref=winstall) which both Frosti and Svavar recommended. To download FFmpeg, I had to run this command in the terminal:

```bash
winget install ffmpeg
```
