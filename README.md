# ANmap Wrapper
Nmap wrapper for Android

## History
In 2016 I applied for a GSoC at Nmap with a bid for an Android port of Nmap. I built an ugly prototype with a cross-compiled Nmap shared library,
a C wrapper and a simple Android activity to interact with it. The bid was not successful, and probably for good reasons.

In 2022, I thought it would still be nice to be able to run Nmap from time to time from my smartphone. I took the original prototype, polished
it a bit and packaged it. It's still ugly, but it does its job. And maybe angry user feedbacks will motivate me to spend some time on it.

## How to cross-compile Nmap

```
cd app/src/main/cpp
./make_nmap.sh
```

The script will do the following:

1) Download latest stable Nmap source (7.93 at the time of writing).
2) Configure and compile Nmap as a shared library for `armeabi-v7a` and `arm64-v8a`.
3) Import Nmap resource files (like `nmap-services`) to Android assets directory.

This operation needs to be performed only once. The C++ wrapper is compiled separately with Android CMake, so you don't need to rebuild the libraries
if you change the wrapper.

## TODO

1) ~~Migrate from deprecated AsyncTask to Runnable.~~
2) Explore options for IPC other than pipes and output redirection and remove ugly `fork()` in wrapper.
3) Add root support.
4) Add x86 and x86_64 support.
