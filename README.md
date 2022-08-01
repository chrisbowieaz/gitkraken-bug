# gitkraken-bug

This repo is created to reproduce bug in GitKraken.

## Steps to reproduce

1. Fork this repo
1. Clone the fork via https https://github.com/<user>/gitkraken-bug.git
1. Regenerate big files
   ```sh
   ./generate-big-files.sh
   ```
1. Commit
1. Push from GitKraken UI

**Result:** spinner is displayed for ~46 seconds and after that following error appears.
```
[01:45:21] Push main: Secure Transport Error for origin: this might indicate you're attempting to push too many files at once.
```

## Notes

- Originally issue was discovered in a private repo (without git LFS)
- Issue doens't relate to file size (commit in private repo has 5MB patch, but there were more files in total)
- The same error appears if try to clone that private repo via https - can't reproduce on this repo
- Everything works well via ssh
- Everything works well from terminal via https
- Each big file is 40MB size to avoid warnings from github (started from 50MB)
- Just an idea: maybe there is some timeout in http client


## System

- MacBook Pro (15-inch, 2018)
- Processor 2.6 GHz 6-Core Intel Core i7
- Memory 16 GB 2400 MHz DDR4
- macOS Monterey 12.3.1 (21E258)
- GitKraken 8.7.0
