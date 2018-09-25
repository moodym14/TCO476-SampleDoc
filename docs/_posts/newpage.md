---
latout: default
---

# How to create a new page!
by Marlon Moody

This post describes how to configure your github repo to use the /docs folder as the source code for the repo’s documentation that will be automatically published in github.io.

Configuring the documentation folder
In the repo’s Settings, in the GitHub Pages section, set (or ensure that) the doc source to none.

Set the current branch to master.
Create (or confirm the existence of) a /docs folder in repo. To create a folder, if necessary, create a /docs/index.md file and enter some simple content in markdown.
In the repo’s Settings, in the GitHub Pages section, set (or ensure that) the doc source to master branch /docs folder.
Wait about a minute and make sure that no errors are reported in the GitHub Pages section of the repo’s Settings page.
If no errors are reported, check to see if your documentation is visible at https://<account>.github.io/<repo name>. For example, this content will be visible at http://rbwatson.moodym14/TCO476-SampleDoc
Create a new Jekyll documentation project
If the preceding steps produce a valid documentation topic entry in github.io, you can proceed to create a new Jekyll project from a system that has git and Jekyll installed (e.g. you AWS EC2 server).

From the root folder of your user account on your AWS EC2 server, do one of these:
If you have not cloned the repo, clone the documentation repo created above and go to the /docs folder of the repo.
If you have already cloned the repo, then refresh the content of the repo on the server by going to the folder with the repo and entering the following at the command line:
git pull origin master
and go to the /docs folder of the repo.
Create a new Jekyll documentation template in the /docs folder, by entering this at the command line: 
jekyll new . --force 
Rename index.html to index.md and add any additional markdown to the page (carefully so as to not create any errors when the documentation is built).
Add all the new files to git:
git add *.*
git add _posts/*.*
git add css/*.*
git commit -a -m "creating new Jekyll doc project"
git push origin master
This should push the documentation files to the github server, which should cause it to build automatically (within a few seconds, if not immediately)
Wait about a minute, refresh the Settings page of the repo, and make sure that no errors are reported in the GitHub Pages section of the repo’s Settings page.
If no errors are reported, check to see if your updated documentation is visible at https://<account>.github.io/<repo name>. For example, this content will be visible at http://moodym14.github.io/TCO476-SampleDoc
Documentation updates
After the preceding is successful, new topics and documentation can be added and updated using normal git protocol. That is, a dev branch can be created from the master branch and then edited and tested.

When the updated content in the dev branch is ready to publish, a pull request can be created to update the master branch. Once the master branch documentation content has been merged and updated, the content at https://<account>.github.io/<repo name> will be updated automatically (within a minute or so, normally).

Additional documentation
Check out the Jekyll docs for more info on how to get the most out of Jekyll. File all bugs/feature requests at Jekyll’s GitHub repo. If you have questions, you can ask them on Jekyll Talk.
