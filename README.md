# spkg

A simple, minimal package manager for BaseRoot Linux, written in POSIX shell.  
Uses a JSON-based repository and is fully compatible with toybox sh.

## commands

```sh
spkg sync              # download the package repository
spkg list              # list installed packages
spkg add <pkg> [...]   # install one or more packages
spkg del <pkg> [...]   # remove one or more packages
spkg up [pkg ...]      # update all packages, or specific ones
```

## repository format

The repository is a JSON file fetched from `REPO_URL`. Each entry looks like:

```json
[
  { "pkg": "curl", "ver": "8.11.0", "link": "https://example.com/packages/curl-8.11.0.tar.gz" },
  { "pkg": "nano", "ver": "8.2",    "link": "https://example.com/packages/nano-8.2.tar.gz" }
]
```

## file structure

```
/usr/share/spkg/packages.json    # cached repository
/usr/share/spkg/installed.info   # installed packages and versions
/usr/share/spkg/files/<pkg>.files  # file list per package
```

## configuration

Edit `REPO_URL` at the top of the script to point to your repository.

## notes

- Package tarballs must extract directly to `/`
- Root is required for all commands except `list`