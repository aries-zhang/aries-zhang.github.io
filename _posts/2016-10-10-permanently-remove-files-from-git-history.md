---
layout: post
title: How to permanently remove files from git history
---

If you try to search on Google about how to permanently remove a large file that was accidentally committed to your git repository, you may find the following solution.

```
git filter-branch --prune-empty --index-filter 'git rm -rf --cached --ignore-unmatch extremely-large.file' --tag-name-filter cat -- --all
```

Unfortunately, this can not help you. The reason is that while all commit history related to the file is completely removed, the git objects are still there. So, if you compare the ```.git``` folder's size before and after, you will find that there is no difference at all, and if you ```git push -f``` to your remote repository, these objects are still going with other objects.

A good way to avoid this is to clone a clean repository, change its remote to your remote repository, and push forcibly.

```
git clone --no-hardlinks file:////path/to/repo repo2
cd repo2
git remote set-url origin https://your-host.com/your-repo.git
git push -f
```

Now, enjoy your smaller git repo.