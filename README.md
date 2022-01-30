
# yocto-ci-build

I've wanted to be able to build and test Yocto images for the [meta-mono](https://github.com/DynamicDevices/meta-mono) layer for many years.

Problems have been that hosted cloud builders tend not to have the performance that is needed to build Yocto and they tend to cut off builds after an hour or two.

Even on a relatively powerful system I find Yocto builds take 3 hours or so.

Recently I found I can use GitHub self-hosted runners to run GitHub build and test workflows on my own hardware, so this is something I am looking at now.

A problem I am seeing is that the build environment I set up on my own hardware is relatively new so works for recent Yocto releases, but there are issue building for older Yocto releases such as sumo, e.g. gcc 9/10 and new libc causes problems.

So it seemed that what I wanted was to run the GitHub build action inside a docker container, and then this could be tweaked to be an appropriate build host for building specific Yocto releases.

The last hurdle was that I host my build environment inside an LXC container running under ProxMox on my physical hardware so I needed to be able to set this up to nest Docker inside that container to be able to run up the GitHub action.

This all seems to be working now!

