# Notes about using traveling-ruby


Traveling-Ruby now supports aarch64 builds of Ruby `2.6.10` which is the required version for Homebrew.

Homebrew although it supports Linux, does not support `aarch64` as Portable ruby does not provide bottles.

- https://github.com/Homebrew/homebrew-portable-ruby/blob/master/Formula/portable-ruby.rb

## TODO

1. `./install.sh`
   1. [x] Update to allow `aarch64` linux installs
2. Homebrew ruby lookup fails on linux. both resolved in https://github.com/you54f/brew
   1. [X] `aarch64` fails to find ruby `2.6.10` on path, and errors on `brew update`
   2. [X] `x86_64` pours portable-ruby despite ruby being first on path.
3. [ ] Homebrew Binary support for aarch64
   1. [ ] No aarch64 builds for following binaries
      1. [ ] https://github.com/sorbet/sorbet/issues/4119
      2. [ ] https://gist.github.com/ethankhall/516ddcefd22297a6cb9f736648386292
4. Portable Ruby
   1. Update bottles to include `aarch64` build from traveling ruby.


Workflows shown tested in

`.github/workflows/install.yml`

`.cirrus.yml`

Steps to use your own Ruby with HomeBrew

1. Download Traveling-Ruby (or your own version of ruby)
   1. Install via Releases Page
   2. Install via CLI script
      1. https://gist.github.com/YOU54F/2e47eb0b653b6810dd6a0be9fc6820ea
2. Make it first in `PATH`
3. Set remote on install
   1.`HOMEBREW_BREW_GIT_REMOTE="https://github.com/you54f/brew"`
4. Install Homebrew as usual
   1. - Linux `x86_64`
      `NONINTERACTIVE=1 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/HomeBrew/install/HEAD/install.sh)"`
   2. - Linux `aarch64`
      `NONINTERACTIVE=1 /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/YOU54F/install/HEAD/install.sh)"`
5. Run `brew doctor` - 
   1. Note now using user provided Ruby
   2. Warn about suspicious remote, set at install time, lets reset it back to HomeBrews official
      1. `git -C "/home/linuxbrew/.linuxbrew/Homebrew" remote set-url origin https://github.com/Homebrew/brew`
6. Run `brew doctor` - 
   1. Note now using user provided Ruby
   2. No longer warning about suspicious remote
   3. Linux `aarch64` users will get message about unsupported CPU architecture.


### Notes

#### Running locally

- Act
  - Runner home path is different in GHA compared to Act
    - Act `export PATH=/root/.travelling-ruby/bin:${PATH}`
    - GHA `export PATH=/home/runner/.travelling-ruby/bin:${PATH}`
