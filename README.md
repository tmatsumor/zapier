ここでは zapier での API 連携について利用例を記録する[1]。  

zaipier ではアカウントを作成後、連携したいサービスを選択して  
ノーコードで API 連携を実現することが出来る。  
ただし、free プランでは 月に 100 タスクまでに制限されている（2023年4月現在）。  

特定の Zap がどの程度タスクを消費するかについては、  
Zap の History に表示される、使用タスクの量を見れば良い。

## やりたいこと
インスタまたはTwitterから、特定ハッシュタグを含む  
投稿のみを Slack に転送したい。  
特定ハッシュタグは、Slack への転送なので #2sl とする。
  
## Instagram ⇒ Slack 連携
１．Create Zap から Trigger で Instagram を選ぶ。  
  
２．一つ目の Action で contains「#2sl」を指定する。  
  
３．二つ目の Action で Slack へ投稿する。  
  
・Message Text を Caption と Permalink 指定。  
・Send as bot を No とする。  
・Include a link to this Zap? は No。  
・Attach Image by URL を Media Url。  
・Auto-Expand Links? を Yes。  


[1]: IFTTT でも構わなかったのだが、Twitter への Connect で  
エラーが発生したため、zapier を採用した。
