# 嵌入式系統實驗實驗一：JavaScript and web programming basics

目的：以 web 應用程式開發作為練習，學習 JavaScript 程式語言。（實驗二要使用的 [Tessel 開發板](https://tessel.io/)有 JavaScript API）練習自學新的、陌生的軟體工程技術。熟悉 Linux 系統與 bash 指令列。認識 git 原始碼版本控制系統與 GitHub 平台。

每一組請開發一個功能類似 Messenger (https://www.messenger.com/) 的線上聊天室 web application。整個專案所使用程式語言必須以 JavaScript 為主，前端只需要考慮桌面版 Google Chrome 瀏覽器即可，除此之外，沒有什麼特別的限制。允許使用任何的函式庫、框架。線上聊天室，建議至少要做到基本的文字聊天功能。除此之外自由發揮。帳號註冊、帳號登入、好友管理、聊天室管理、單帳號多 clients 同步、更好用的 UI... 許多可以追加精進的功能，很多細節可以有不同的設計、取捨。如果真的行有餘力、你本來就擅長 JavaScript 與 webapp 開發了，想要做多媒體分享、語音傳訊、webRTC 即時語音聊天...  也可以。Web server 與 client 都在本地端是可以的，在區域網路內的多台電腦也行，實際上把 web server 部署到一個具有 public IP address 的主機也很好。

在 03/31 (五) 14:20-17:20 需要將成果 live demo 給助教，如果這個時段不克出席，請另外約時間提早 demo。請將整份專案的原始碼與一份 PDF 報告都放在 GitHub 平台上。 (i.e., everything you do is public) PDF 報告內容排版格式不拘，建議使用中文，原則上篇幅以 10 頁 A4 為上限。

EDIT: 關於報告的補充說明：在 PDF 報告裡，請描述你們設計、實作的 web app 具備哪些功能以及系統架構。系統架構方面，描述得愈清楚愈好，系統太過複雜時，畫圖做說明可能會更好。整個系統包含哪些子元件？每個元件擔任什麼角色？元件與元件之間的界面是什麼、會發生怎樣的互動？



# 參考資源

- [ECMAScript Language Specification](https://www.ecma-international.org/publications/standards/Ecma-262-arch.htm) (此 repo 的 ecmascript-specs.zip 包含 5.1、6、7 三個版本的離線網頁閱讀版)
- [MDN A re-introduction to JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript)
- [MDN JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Node.js](https://nodejs.org/en/) and [Node.js API docs](https://nodejs.org/dist/latest-v6.x/docs/api/)
- [MDN HTML Reference](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [MDN Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [Chrome DevTools](https://developer.chrome.com/devtools)
- [一個 JavaScript style guide 實例](https://github.com/airbnb/javascript)
- 以前上課為 JavaScript 準備的: [投影片](https://slides.com/concise/js/fullscreen#/)、[some example code snippets](https://gist.github.com/concise/ccdb62da35a07fc989e0)
- [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [localStorage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)
- [Events](https://developer.mozilla.org/en-US/docs/Web/Events)
- [Pro Git book 第一章與第二章](https://git-scm.com/book/zh-tw/v2)（[原英文版](https://git-scm.com/book/en/v2)）



# 工作環境建置

#### 安裝 Ubuntu 16.04 x64 desktop 系統

準備一支至少有 2 GB 容量的 USB flash drive。至 `http://debian.linux.org.tw/ubuntu-releases/xenial/` 或 `http://ftp.nchc.org.tw/ubuntu-cd/xenial/` 下載 `ubuntu-16.04.2-desktop-amd64.iso` 檔案。製作可開機隨身碟，用隨身碟開機，安裝系統。

#### 用 apt 下載、安裝軟體套件，可以選用較快的 mirror

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

以 6.10.0 為例，Linux 或 macOS 使用者可以直接下載相對應的 prebuilt binary：

- https://nodejs.org/dist/v6.10.0/node-v6.10.0-linux-x64.tar.gz
- https://nodejs.org/dist/v6.10.0/node-v6.10.0-darwin-x64.tar.gz

免編譯、免安裝的安裝方式：將 tar archive 解開，放到你喜歡的目錄下，即可。不希望總是要輸入完整路徑才能執行 node、npm 等指令，以 bash 為例，改變 PATH 環境變數就行了。
