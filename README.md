
# MARS - Maths Assessments Recommendation System

An online data catalogue for educational Maths material with a built-in Machine Learning topic recommendation system.

https://rickybassom.github.io/mars/

## Design
* The site is static and runs on [GitHub Pages](https://pages.github.com/).
* Pages are created with either markdown files or html pages which use [Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll) for rendering.
* The site is styled with [Bootstrap 4](https://getbootstrap.com/docs/4.0/getting-started/introduction/).
* The site lists and displays topics in the `catalogue/` directory using GitHub Actions for indexing.
* The site uses JavaScript to recommend topics based on a weighted directed dependency tree.
* [SCORM](https://scorm.com/) packages (as well as some other file formats) can be stored and viewed in the catalogue.

### Two Data Structures
#### Catalogue Directory Tree
* Located at `catalogue/`.
* Represents the tree structure of files and directories you see on the left of the site.
* A directory can contain:
  * One or more .md Markdown or .html files. An optional index.md or index.html file in a directory will appear when the directory is clicked on the Catalogue Directory Tree.
  * One or more .pdf files.
  * One or more video files (.mp4, .ogv, .webm, .wav).
  * Only unzipped SCORM package files. The `index.html` file is used to display the quiz on the site. A SCORM directory is identified by the `numbas-manifest.json` file. The SCORM directory will appear and act like a file in the Catalogue Directory Tree.
  * One or more child directories.

#### Topic Dependency Graph
* THIS MAY CHANGE IN THE NEAR FUTURE, DON'T POPULATE FILE
* Located at `catalogue/deps.csv`.
* Represents a weighted directed graph of files and directories to identify topic learning dependencies.
* A topic is a file or directory in the `catalogue/` directory. Note that a topic that is a SCORM package is identified by the directory, not any files in an unzipped SCORM directory.
* Files or directories are nodes, a connection is a topic dependency, and the connection weight is the degree of which a student needs to first know another topic 2 to learn topic 1.
* The file format is described at the top of the file as comments.
* Dependency data is not required, but more dependency data will improve recommendations on the site.

## Modifying the catalogue through github.com
1. Go to https://github.com/rickybassom/mars.
2. Press the dot key on your keyboard. An editor should pop up.
3. On the left-hand side of the editor click on the Explore button to view the repository's files.
4. Using the file tree you can add, modify, and delete file/folders inside the `catalogue/` folder. Files/folders can be uploaded by right-clicking on a folder and clicking on upload.
5. Once your happy with your changes, you can commit+push the changes to the repository by clicking on the Source Control button on the left and then clicking on the Commit and push tick button along with a name for your commit.
6. If you navigate back to https://github.com/rickybassom/mars you should see the commit added to repository.
7. After ~5 minutes the changes should appear on the site at https://rickybassom.github.io/mars/.
8. If the changes do not appear on the site double-check your last commit at https://github.com/rickybassom/mars/commits/master. Or try rerunning the latest GitHub Action page building job here https://github.com/rickybassom/mars/actions.

## Advanced Developer Documentation

### Running locally
Generate `assets/catalogue_index.txt`:
```sh
./generate_catalogue_index.sh
```

Start server:
```sh
docker run -it --rm -v "$PWD":/usr/src/app -p "4000:4000" starefossen/github-pages
```

For committing locally, run the following command to disable catalogue_index.txt tracking (GH Actions generates this file):
```sh
git update-index --assume-unchanged assets/catalogue_index.txt
```

Useful links:
- https://jekyllrb.com/
- https://getbootstrap.com/docs/5.0/getting-started/introduction/

## Contribution

[See the contribution guide.](./CONTRIBUTING.md)

## License

[See the license file.](./LICENSE.md)
