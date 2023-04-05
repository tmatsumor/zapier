ここでは zapier での API 連携について利用例を記録する[1]。  

zaipier ではアカウントを作成後、連携したいサービスを選択して  
ノーコードで API 連携を実現することが出来る。  
ただし、free プランでは 月に 100 タスクまでに制限されている（2023年4月現在）。  

特定の Zap がどの程度タスクを消費するかについては、  
Zap の History に表示される、使用タスクの量を見れば良い。

## やりたいこと
インスタまたはTwitterから、特定ハッシュタグを含む  
投稿のみを Slack に転送したい。  
特定ハッシュタグは、Slack への転送なので `#2sl` とする。  

  
## （Ａ）Instagram ⇒ Slack 連携
１．Create Zap から Trigger で Instagram を選ぶ。  
  
２．一つ目の Action で App に Filter by Zapier を選ぶ。  
`Text` にて contains `#2sl` を指定する。  
  
３．二つ目の Action で Slack へ投稿する。  
  
・Message Text を `Caption` と `Permalink` 指定。  
・Send as bot を No とする。  
・Include a link to this Zap? は No。  
・Attach Image by URL を Media Url。  
・Auto-Expand Links? を Yes。  
  
  
## （Ｂ）Twitter ⇒ Slack 連携
１．Create Zap から Trigger で Twitter を選ぶ。  
  
２．一つ目の Action で App に Filter by Zapier を選ぶ。  
`Text` にて contains `#2sl` を指定する。  
さらに And 条件を追加し、  
`Entities Urls Expanded Url` にて  
Does not contain `https://www.instagram.com` を指定する。  
  
３．二つ目の Action で Slack へ投稿する。  
  
・Message Text を Text 設定。  
・Send as bot を No とする。  
・Include a link to this Zap? は No。  
・Attach Image by URL に `Entities Attached Media Media Url https` を指定。  
・Auto-Expand Links? に No を指定。  
  

## 留意事項
なお、インスタ から Twitter は自動転送が入っているので、  
Twitter からの #2sl 投稿は インスタの URL入り投稿 を除外する。  
以下のようなケースを除外するためである。  
  
・インスタから #2sl タグを付けて投稿  
⇒ #2sl の インスタ Zapier が起動し Slack に転送。  
⇒ 並行して、インスタから Twitter に自動転送。  
⇒ #2sl の Twitter Zapier が起動し Slack に転送。  
⇒ #2sl が二重起動し、Slack への転送がダブる。  
  
---

[1]: IFTTT でも構わなかったのだが、Twitter への Connect で  
エラーが発生したため、zapier を採用した。
