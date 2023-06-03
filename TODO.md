# Notes about using traveling-ruby


Traveling-Ruby now supports aarch64 builds of Ruby `2.6.10` which is the required version for Homebrew.

Homebrew although it supports Linux, does not support `aarch64` as Portable ruby does not provide bottles.

- https://github.com/Homebrew/homebrew-portable-ruby/blob/master/Formula/portable-ruby.rb

## TODO

1. `./install.sh`
   1. [x] Update to allow `aarch64` linux installs
2. Homebrew ruby lookup fails on linux.
   1. [ ] `aarch64` fails to find ruby `2.6.10` on path, and errors on `brew update`
   2. [ ] `x86_64` pours portable-ruby despite ruby being first on path.
3. Portable Ruby
   1. Update bottles to include `aarch64` build from traveling ruby.