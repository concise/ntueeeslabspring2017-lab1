# 嵌入式系統實驗實驗一

目的：以 web 應用程式開發作為練習，學習 JavaScript 程式語言。（實驗二要使用的 [Tessel 開發板](https://tessel.io/)有 JavaScript API）練習自學新的、陌生的軟體工程技術。熟悉 Linux 系統與 bash 指令列。認識 git 原始碼版本控制系統與 GitHub 平台。

每一組請開發一個功能類似 Messenger (https://www.messenger.com/) 的線上聊天室 web application。整個專案所使用程式語言必須以 JavaScript 為主，前端只需要考慮桌面版 Google Chrome 瀏覽器即可，除此之外，沒有什麼特別的限制。允許使用任何的函式庫、框架。線上聊天室，建議至少要做到基本的文字聊天功能。除此之外自由發揮。帳號註冊、帳號登入、好友管理、聊天室管理、更好用的 UI... 非常可以追加的功能，很多細節可以有不同的設計。如果真的行有餘力、你本來就擅長 JavaScript 與 webapp 開發了，想要做多媒體分享、語音傳訊、webRTC 即時語音聊天...  也可以。

在 03/31 (五) 14:20-17:20 需要將成果 live demo 給助教。請將整份專案的原始碼與一份 PDF 報告都放在 GitHub 平台上。 (i.e., everything you do is public) PDF 報告內容排版格式不拘，建議使用中文，原則上篇幅以 10 頁 A4 為上限。



# 參考資源

- [MDN A re-introduction to JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
- [Chrome DevTools](https://developer.chrome.com/devtools)
- [Node.js](https://nodejs.org/en/)
- ECMAScript Language Specification (本 repo 的 ecmascript-specs.zip 包含了 ES5.1、ES6、ES7 的離線網頁閱讀版了)
- [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [MDN HTML Reference](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [一個 JavaScript style guide 實例](https://github.com/airbnb/javascript)
- 以前上課為 JavaScript 準備的: [投影片](https://slides.com/concise/js/fullscreen#/)、[some example code snippets](https://gist.github.com/concise/ccdb62da35a07fc989e0)



# 其他

#### 安裝 Ubuntu 16.04 x64 desktop 系統

準備一支至少有 2 GB 容量的 USB flash drive。至 `http://debian.linux.org.tw/ubuntu-releases/xenial/` 或 `http://ftp.nchc.org.tw/ubuntu-cd/xenial/` 下載 `ubuntu-16.04.2-desktop-amd64.iso` 檔案。製作可開機隨身碟。

#### 關於用 apt 下載軟體套件

若在台大校內，下載軟體套件用的 archive mirror 建議使用台大計中的 `http://debian.linux.org.tw/ubuntu/`，速度較快；若在校外，則使用 `http://tw.archive.ubuntu.com/ubuntu/` 或 `http://free.nchc.org.tw/ubuntu/` 即可。

若要將你的 Ubuntu 16.04 系統的 archive mirror 設定為台大計中的，將 `/etc/apt/sources.list` 檔案內容修改如下：

```
deb http://debian.linux.org.tw/ubuntu/ xenial           main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ xenial-updates   main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ xenial-backports main restricted universe multiverse
deb http://debian.linux.org.tw/ubuntu/ xenial-security  main restricted universe multiverse
```

然後執行 `apt-get update`。

#### 安裝 Google Chrome 瀏覽器

```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
dpkg -i google-chrome-stable_current_amd64.deb
apt-get install -f
```

#### 安裝 Node.js LTS 版 (v6 系列)

到 https://nodejs.org/en/ 可以看到現在最新版本號。到 https://nodejs.org/dist/ 可以看到所有可以下載的版本號。

以 6.10.0 為例，Linux 或 macOS 使用者可以直接下載到 binary：

- https://nodejs.org/dist/v6.10.0/node-v6.10.0-linux-x64.tar.gz
- https://nodejs.org/dist/v6.10.0/node-v6.10.0-darwin-x64.tar.gz

免編譯、免安裝的安裝方式：將 tar archive 解開，放到你喜歡的目錄下，即可。不希望總是要輸入完整路徑才能執行 node、npm 等指令，以 bash 為例，改變 PATH 環境變數就行了。

而這個版本的 Node.js API 文件在此：

- https://nodejs.org/dist/v6.10.0/docs/api/
