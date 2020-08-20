# Git fork workflow ([Reference](https://blog.scottlowe.org/2015/01/27/using-fork-branch-git-workflow/))

- Fork the repository, then clone the fork

```bash
$ git clone https://github.com/waynee95/<fork>.git
```

- Add original repository as `upstream` to be able to fetch latest updates

```bash
$ git remote add upstream https://github.com/<org>/<original-repo>.git
```

### Adding a new feature

1. Create and checkout a _feature_ branch
2. Make changes to the files
3. Commit changes to the branch/fork

```bash
$ git checkout -b <new branch>
$ git push origin <new branch>
```

Then create a PR in the original repository.

### Cleaning up

- After the feature was merged, update the fork

```bash
$ git pull upstream master
```

- Delete the feature branch, as not needed anymore

```bash
$ git branch -d <branch name>
```

- Update the master branch of the fork

```bash
$ git push origin master
```

- And also delete the feature branch in the remote repository

```bash
$ git push --delete origin <branch name>
```

### Keeping fork in sync

- Make sure to always have the most recent version in the fork, since forks do not 
update automatically!

```bash
git pull upstream master
git push origin master
```