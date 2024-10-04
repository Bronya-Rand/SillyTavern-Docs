---
icon: git-branch
order: 100
---

## Branches

SillyTavern is being developed using a multi-branch system to ensure a smooth experience for all users.

* **release** - Recommended for most users. This is the most stable and recommended branch, updated only when major releases are pushed. It's suitable for the majority of users.
* **staging** - Not recommended for casual use. This branch has the latest features, but be cautious as it may break at any time. Only for power users and enthusiasts.
* **main** and **dev** - These branches are deprecated, will not receive updates, and will be deleted on *September 1, 2023*. You are encouraged to switch branches before the deadline.

## What happened to the main and dev?

The git commit history was squashed to the state of release 1.9.0.

Old branches were carrying the long legacy of bad git practices and large binary files once present in the repository.
Every git clone would download and store a lot of unnecessary files, creating a network and disk load.
Also, it makes it virtually impossible for us to properly update the default content such as settings.json without causing git conflicts.

Unfortunately, losing commit history also means losing the code contribution history.
If you contributed to the SillyTavern development and want to see yourself credited in the README file and Docs website, please get in touch with us!

## How to migrate to a new branch if I use main/dev?

_**It is recommended to do a fresh install.**_ However, if you wish to use an existing copy of SillyTavern, please follow the instructions below.

**IMPORTANT!** Before doing anything, make *a complete backup* of your installation. You may *lose your data* in the process, so don't ignore this warning.

Not sure of which files to back up? See the list here: [How to Update SillyTavern](https://docs.sillytavern.app/usage/update/#note-do-not-copy-the-entire-public-folder)

### git installs

1. Open a terminal prompt (cmd, PowerShell, Termux, etc) in your SillyTavern installation folder.
2. Type `git fetch` and then `git pull` to pull the updates.
3. You may lose your settings. Have you made a backup? `git switch release` or `git switch staging` will change your branch, respectively 
4. Skip to next item if you have no errors. You may have something like:
   ```
   error: Your local changes to the following files would be overwritten by checkout:
        config.conf
        public/css/bg_load.css
        public/settings.json
   ```
   You will see a list of files effected. If you do not care about those settings files being replaced `git switch -f release` or `git switch -f staging` will set your branch.
   If you do care to save those changes restore from backup.
7. Type `npm install` and then `npm run start` to test that everything behaves correctly.
8. Enjoy! Restore your data from a backup if needed.

### fatal: invalid reference: release

This may happen if you cloned just a single branch from an old remote (before migration to the organization repo). To fix this, you need to add and fetch a branch from a new remote:

```
git remote add st http://github.com/SillyTavern/SillyTavern
git fetch st
git checkout -t st/release
```

Then proceed from step 5.

### ZIP installs

Nothing changes for you. Just download the branch/release ZIP like usual.
