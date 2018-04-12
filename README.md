To use the npm packages access github API you need to first generate a token. You can generate a personal token follow [this guide](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/).

Once a token is generated add the following lines to the `.bashrc`

`export GITHUB_USER="<USERNAME>"`

`export GITHUB_TOKEN="<TOKEN>"`

you need to first install `npm` package manager

`sudo apt-get install npm`

Then you need the install the following three packages
* [github-labels](https://github.com/popomore/github-labels)
* [copy-github-labels](https://github.com/jvandemo/copy-github-labels)
* [github-label-manager](https://www.npmjs.com/package/github-label-manager)

The package [github-labels](https://github.com/popomore/github-labels) lets you to add labels to your github repository from `.json` file directly using

`labels -c <file> -f <github_user>/<repo_name> -t <token>`

e.g. `labels -c github-labels.json -f yeshasvitvs/github-labels -t ${GITHUB_TOKEN}`

**NOTE**: The option `-f` is force option which will delete all existing labels.

The package [github-label-manager](https://www.npmjs.com/package/github-label-manager) lets you to copy the labels from one repository to another repository.

To remove the existing labels in a repository use 

`glm -u <github_user> -t <token> clear <origin-repo-name>`

e.g.`glm -u ${GITHUB_USER} -t ${GITHUB_TOKEN} clear github-labels`

**NOTE**: This only removes the labels in one page. If you have more the one page of labels you need to run the above command multiple times to delete all the labels.

To copy the labels from one repository to another repository use

`glm -u <github_user> -t <token> copy <origin-repo-name> <destination-repo-name>`

e.g. `glm -u ${GITHUB_USER} -t ${GITHUB_TOKEN} copy github-labels my-awesome-new-repo`
