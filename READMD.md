# secondaryMarket

## 配置
- node: v18
- hexo-deployer-git // 部署
## 指令
- hexo server

## 安裝方式
```
npm install
hexo s  // 架設本地端伺服器，也可以輸入 hexo server
hexo g  // 靜態文件

```
### 開發環境

```sh
hexo cl  //清除之前建立的靜態檔案，也可以輸入 hexo clean
hexo g  //建立靜態檔案，也可以輸入 hexo generate
hexo d  //部署至 Github Pages，也可以輸入 hexo deploy
(http://localhost:4000/admin )就能進入後台 (npm install hexo-admin --save)
```
https://ed521.github.io/2019/07/hexo-install/

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)

.  // 根目錄
├─ .deploy_git
├─ node_modules
├─ public　    // 使用 hexo g 指令生成的內容
├─ scaffolds   // 模板
├─ source　    // 存放原始檔案
　　├─ _discarded　// 已刪除文章
　　├─ _drafts　 // 未發布文章
　　├─ _posts　　// 已發布文章（會被 push）
　　├─ about　　 // 關於我
　　├─ categories   // 分類
　　└─ _data // 自訂樣式 
├─ themes　      // 存放主題
　　└─ landscape　// 預設主題
　　　　├─ layout, scripts, source
　　　　└─ _config.yml　// 修改主題設定
└─ _config.yml　// 修改部落格的通用設定，例如：網站標題、網址、使用主題等

https://guiblogs.com/hexo30-12/