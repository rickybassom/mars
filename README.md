
# MARS - Maths Assessments Recommendation System

About...

https://rickybassom.github.io/mars/

## Design
* The site is static and runs on [GitHub Pages](https://pages.github.com/).
* Pages are created with either markdown files or html pages which use [Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll) for rendering.
* The site is styled with [Bootstrap 4](https://getbootstrap.com/docs/4.0/getting-started/introduction/).
* The site uses the [GitHub API](https://docs.github.com/en/rest) to list topics in the repository's `catalogue/` directory.
* The site uses JavaScript to recommend topics based on a weighted directed dependency tree.
* [SCORM](https://scorm.com/) packages (as well as some other file formats) can be stored and viewed in the catalogue.

### Two Data Structures
#### Catalogue Directory Tree
* Located at `catalogue/`.
* Represents the tree structure of files and directories you see on the left of the site.
* A directory can contain:
  * One or more .md Markdown files (will be rendered as HTML to the user)
  * One or more .pdf files
  * One or more video files (.mp4, .ogv, .webm, .wav)
  * Only unzipped SCORM package files. The index.html file is used to display the quiz. A SCORM directory is identified by the source.exam file. Only unzipped SCORM package files. The index.html file is used to display the quiz on the site. A SCORM directory is identified by the source.exam file. The SCORM directory will appear and act like a file in the site tree view.
  * One or more child directories

#### Topic Dependency Graph
* Located at `catalogue/deps.csv`.
* Represents a weighted directed graph of files and directories to identify topic learning dependencies.
* A topic is a file or directory in the `catalogue/` directory. Note that a topic that is a SCORM package is identified by the directory, not any files in an unzipped SCORM directory.
* Files or directories are nodes, a connection is a topic dependency, and the connection weight is the degree of which a student needs to first know another topic 2 to learn topic 1.
* The file format is described at the top of the file as comments.
* Dependency data is not required, but more dependency data will improve recommendations on the site.

## Dependencies
- `ruby 2.X.X`
- `jekyll` For templating look at: https://jekyllrb.com/docs/liquid/

## Running locally
```sh
bundle exec jekyll serve
``` 
For reference: https://help.github.com/en/enterprise/2.14/user/articles/setting-up-your-github-pages-site-locally-with-jekyll


## Contribution

[See the contribution guide.](./CONTRIBUTING.md)

## License

[See the license file.](./LICENSE.md)
