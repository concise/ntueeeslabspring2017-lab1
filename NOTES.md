### 安裝 Ubuntu 16.04 x64 desktop 系統

準備一支至少有 2 GB 容量的 USB flash drive。至 `http://debian.linux.org.tw/ubuntu-releases/xenial/` 或 `http://ftp.nchc.org.tw/ubuntu-cd/xenial/` 下載 `ubuntu-16.04.2-desktop-amd64.iso` 檔案。製作可開機隨身碟。

### 關於用 apt 下載軟體套件

若在台大校內，下載軟體套件用的 archive mirror 建議使用台大計中的 `http://debian.linux.org.tw/ubuntu/`，速度較快；若在校外，則使用 `http://tw.archive.ubuntu.com/ubuntu/` 或 `http://free.nchc.org.tw/ubuntu/` 即可。

若要將你的 Ubuntu 16.04 系統的 archive mirror 設定為台大計中的，將 `/etc/apt/sources.list` 檔案內容修改如下：

```
deb http://debian.linux.org.tw/ubuntu/ xenial           main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ xenial-updates   main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ xenial-backports main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ xenial-security  main restricted universe multiverse
```

然後執行 `apt-get update`。
