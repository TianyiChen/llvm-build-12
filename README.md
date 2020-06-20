# LLVM-build

Make building LLVM and switching between commits painless.

## Usage
* Create an issue with the desired LLVM commit as its title
* When the build is ready, the issue should be closed and you will receive an email by default
* The build will appear in releases
* Download and extract it in `/tmp/llvm-project`
Example: `curl -L https://github.com/TianyiChen/llvm-build/releases/download/48a8c7dc/clang11-virtualroot.tar.gz| tar -xz`
*  Set environment variables
```
export LLVM_VIRT=/tmp/llvm-project/virtualroot
export PATH=$LLVM_VIRT/bin:$PATH
export LD_LIBRARY_PATH=$LLVM_VIRT/lib:$LD_LIBRARY_PATH
```

## Issues
Issues in this repository are meant to be handled by scripts, issues for humans can be submitted at https://github.com/TianyiChen/llvm-build-issues/issues

## Notes
* Instead of clone and checkout, there's another way `git fetch origin <commit>`, which does not differ much in benchmark.
* LLVM needs to be compiled with itself (currently clang-11) if you are making intensive use of it (for example, running it with a plugin). Otherwise you may encounter some mysterious issues.
* If you want to store the binaries somewhere else, you can create a link:
```
# run within the folder for actural storage
ln -s $PWD /tmp/llvm-project
```
* Getting commits by date: https://github.com/llvm/llvm-project/commits/master?until=2020-04-30
https://api.github.com/repos/llvm/llvm-project/commits?until=2020-04-30
