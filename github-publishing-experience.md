# Gitlab to Github migration - experiences 

### 1. Push repository to Github
Make sure you habe an up-to-date copy of your Gitlab repo (pull or make a fresh clone).
Create a new Github repo. Change origin and push to Github, e.g. with:
```` bash
git remote rm origin
git remote add origin git@link-to-your-github-repo.git
git push -u origin master
````

### 2. Сommunity standards
Tab **Insights > Community** in your new repository will guide you through making your project more compliant with "good open source style" (e.g. Readme, Code of conduct, Contributing).  

### 3. License 
Your project very likely has dependencies. 

If each of their licenses is **“permissive”** (gives the public permission to use, modify, and share, without any condition for downstream licensing), you can use any license you want. Common permissive licenses include **MIT, Apache 2.0, ISC, and BSD**.

On the other hand, if any of your dependencies’ licenses are **“strong copyleft”** (also gives public same permissions, subject to condition of using the same license downstream), then your project will have to use the same license. Common strong copyleft licenses include **GPLv2, GPLv3, and AGPLv3**.

### 4. Release
If you have a production package ready to use, you can create a release.
To do this click "Releases" on the panel below description and tags.

### 5. Import issues
Unfortunately, there is no good way to do this. If it is tolerable that 20% of issues won't be imported because of mistakes, here is a (pretty complicated) solution:

1. Download this perl script (and install Perl you don't have it)
https://gitlab.com/emobix/get-all-gitlab-issues-as-csv
Change variables at lines 12-14 to your Gitlab repository data and launch the script.
It will create file issues.csv in the same directory. 
If you have many issues you may need to launch script multiple times changing ``page`` variable.
2. Make sure fields Title, Description, Labels,  Milestone, Assignees and State in csv header are writen with capital letter (needed for next steps).
3. Install node module to import issues to Github:
```` bash
npm install -g github-csv-tools@0.3.0
````
4. Find installed module on your computer, open file `github-csv-tools\node_modules\csv-parse\lib\index.js` and remove lines 268 and 271-275.
5. Then run:
```` bash 
githubCsvTools file_with_issues.csv
````
