# Principles and Practices

## Assignment

- Set up a documentation website using GitLab.
- Plan and sketch a potential final project.

More information can be found at [Fab Academy Schedule](https://fabacademy.org/2025/schedule.html).

### More Info

I began by following these [instructions](https://www.fabisa.is/N%C3%A1msefni/Pre-Fab/1-heimasidugerd/) provided by [Svavar Konradsson](https://fabacademy.org/2023/labs/isafjordur/students/svavar-konradsson/index.html), which were very helpful in setting up [MKDocs](https://www.mkdocs.org/). MKDocs is a simplified version of HTML that uses Markdown. There are numerous themes available, but I decided to use the [Material](https://squidfunk.github.io/mkdocs-material/) theme.

### Setting Up the Website on GitHub

To get started, I downloaded the following:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Python](https://www.python.org/)
- [Git](https://git-scm.com/)

After installing these tools, I created a repository on [GitHub](https://github.com/) to store my project and host the website using GitHub Pages. On my machine, I created a folder named 'Code' on my C: drive. Within the 'Code' folder, I created a subfolder to store the website files during development.

After completing the setup, I opened VS Code, navigated to the 'Code' folder, and selected my project folder. Next, I needed to install MkDocs, so I opened the terminal and typed:
``` 
pip install mkdocs-material 
```
This command installed all the necessary dependencies. Afterwards, I typed:
```
mkdocs new .
```
This command created a folder containing all the required resources for MKDocs, which looked like this:

```
├─ docs/
│  └─ index.md
└─ mkdocs.yml
```
When all that was done, I went into the mkdocs.yml and typed:
```yaml
site_name: Bjartur's Fab Academy Journey 

theme:
    name: material
```
This told MKDocs I wanted to use the Material theme. To check everything was successful, I went into the terminal and typed:

```
mkdocs serve
```
That opened a local website that I can use to see how my website looks even when coding!

Once I had checked that everything was working, I needed to get the website to GitHub. That was a bit more complicated than I thought, but in the end, it worked. Lets go through how i did that!

To get started i connected VS Code to my Github account. 