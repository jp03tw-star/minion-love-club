# Minion Love Club 💛

這是一個簡易的 Firebase 即時集點網站。目標獎品：EPT 全白鞋子；15 點兌換。

## 1. 先修改管理員 Email
在 `index.html` 搜尋 `YOUR_ADMIN_EMAIL@example.com`，換成你的 Email。
在 `firestore.rules` 也把同一段換成完全相同的 Email。

## 2. Firebase Console 設定
在 Firebase 專案 `minion-love-club-6350a`：
1. Authentication → Get started → Sign-in method → 啟用 Email/Password。
2. Firestore Database → Create database → 選 Production mode。
3. Firestore → Rules，貼上本資料夾的 `firestore.rules` 內容並 Publish。
4. Authentication → Settings → Authorized domains，確認部署網站網域已加入（Firebase Hosting 通常會自動加入）。

## 3. 建立兩個帳號
1. 先用管理員 Email 在網站註冊，登入後會初始化集點卡。
2. 女朋友用她自己的 Email 在同一網站註冊。
3. 管理員可新增任務加點、手動扣點、集滿 15 點後確認兌換。
4. 女朋友登入後可查看進度與紀錄。

## 4. 部署到 Firebase Hosting
需要在電腦安裝 Node.js，再執行：
```bash
npm install -g firebase-tools
firebase login
cd minion-love-club
firebase use minion-love-club-6350a
firebase deploy
```
部署完成後，終端機會顯示 Hosting 網址，分享該網址給女朋友即可。

## 安全提醒
- `index.html` 的 Firebase Web 設定是前端設定，不是私密金鑰。
- 不要把 Service Account 私鑰、服務帳號 JSON 或帳號密碼貼到聊天。
- Firestore Rules 的管理員 Email 必須與 `index.html` 相同。不要把資料庫規則改成任何人都能寫入。
- 這是入門版：點數與歷史紀錄存放在同一份文件；適合小型私人集點卡，不適合高流量或需要防止管理員以外的複雜稽核場景。
