---
layout: post
title: Git Global post-checkout hook
---

A global git post checkout hook allows you to set per repo settings while cloning them.
While commiting to work repo i needed to configure my work email and
for public repo i was using gmail.
A global post-checkout hook does this automatically for you while cloning the repo itself.

To setup a global post-checkout hook:
```
git config --global init.templatedir '~/.git_template'
mkdir ~/.git_template/hooks
```

Create a file post-checkout and give it executable permissions.
```
touch ~/.git_template/hooks/post-checkout
chmod +x ~/.git_template/hooks/post-checkout
```

`post-checkout`:
```
#!/bin/bash
if [[ $(git config --get remote.origin.url) =~ "github.workplace.com" ]]; then
  git config --local  user.email "xxxxxxxxxxxxx@workplace.com"
else
  git config --local  user.email "xxxxxxxx@gmail.com"
fi
```

