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

### 安裝 Google Chrome 瀏覽器

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
dpkg -i google-chrome-stable_current_amd64.deb
apt-get install -f
```

### 安裝 Node.js LTS 版 (v6 系列)

到 https://nodejs.org/en/ 可以看到現在最新版本號。到 https://nodejs.org/dist/ 可以看到所有可以下載的版本號。

以 6.10.0 為例，Linux 或 macOS 使用者可以直接下載到 binary：

- https://nodejs.org/dist/v6.10.0/node-v6.10.0-linux-x64.tar.gz
- https://nodejs.org/dist/v6.10.0/node-v6.10.0-darwin-x64.tar.gz

免編譯、免安裝的安裝方式：將 tar archive 解開，放到你喜歡的目錄下，即可。不希望總是要輸入完整路徑才能執行 node、npm 等指令，以 bash 為例，改變 PATH 環境變數就行了。

而這個版本的 Node.js API 文件在此：

- https://nodejs.org/dist/v6.10.0/docs/api/
