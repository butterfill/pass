---
title: Passwords with Pass (CLI utility) and gpg
created: 2023-01-07
tags:
  - personal
---

# Use

    pass -h

Can also recover passwords using

    gpg2 -d PASSWORD_FILE_NAME


passwords are encrypted with key stephen@butterfill.com

passwords are all in `syncthing/personal/_password-store`

# Install

\ref{url:https://www.passwordstore.org/}

    brew install pass

    pass init

    pass git init

add to `.zshrc`:

    export PASSWORD_STORE_DIR=/Users/*USERNAME*/syncthing/personal/_password-store


*I ran `pass init` on both eleven and monstress*.  The password store is synced using syncthing. Seems to work.


# Older passwords

are in files like `_pw.txt` and `_pw_bnk.txt`

Current way to access these:

```
gpg -d _pw.txt| pbcopy
```

Current way to update these

```
mv <filename.txt> <filename-YY-MM-DD.backup.txt>

pbpaste | gpg --encrypt --sign --armor -r stephen@butterfill.com > <filename>.txt
```

Check differences:

```
difft <(gpg -d _pw.txt) <(gpg -d _pwtest.txt)
```