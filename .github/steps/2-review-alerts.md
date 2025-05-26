## ステップ2: シークレットスキャンのアラートを確認し、クローズする

前のステップで、シークレット保護を有効にし、機密ファイルをリポジトリにコミットしました。今回は、オープンなシークレットスキャンのアラートを確認し、1つクローズしてみましょう。

### :keyboard: アクティビティ: シークレットスキャンのアラートを整理する

1. リポジトリのヘッダーで **Security（セキュリティ）** タブをクリックします。

1. 左側のナビゲーションで **Secret scanning（シークレットスキャン）** オプションを選択します。

1. ヘッダーバーにさまざまなオプションがあるので、アラートの整理に役立ててください。

   <img width="400" alt="list of filtered open alerts" src="https://github.com/user-attachments/assets/2926c12f-2d39-4ea1-a8dd-816442f332b4" />

1. **Provider** ドロップダウンをクリックし、`Amazon AWS` を選択して表示を絞り込みます。3件中2件だけが表示されることに注目してください。

   <img width="400" alt="list of filtered open alerts" src="https://github.com/user-attachments/assets/8623dec7-5199-4c5b-8c5e-1b812106a510" />

### :keyboard: アクティビティ: シークレットスキャンのアラートを確認する

1. オープンなアラート一覧から `Amazon AWS Access Key ID` のアラートを選択します。詳細ページが開き、より多くの情報が表示されます。

1. ページ上部で、アラートのステータス、発生日時、漏洩したシークレット、対応手順などをすぐに確認できます。

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/61700b67-234c-47ae-a4de-552be25cc2bf" />

1. 少し下にスクロールすると **Detected in X locations（X箇所で検出）** というエリアがあり、`credentials.yml` ファイルなど、このシークレットが検出されたすべての場所が表示されます。同じシークレットが複数箇所で見つかっても、重複したアラートは作成されないことに注目してください（例：学習課題内など）。

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/0a40db10-0461-4732-8e5d-674082020c96" />

### :keyboard: アクティビティ: アラートをクローズする

シークレット保護がリポジトリ内でシークレットを検出した場合、最初に行うべきことは**プロバイダー側でそのシークレットを無効化すること**です。漏洩したものと考えて対応しましょう。

> [!TIP]
> 一部の[サポートされているシークレット](https://docs.github.com/ja/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#default-patterns)は、漏洩時に自動的にプロバイダーへ通知されます。

1. 対応が完了したら、アラートのステータスを更新できます。右上の **Close as（次の理由でクローズ）** ドロップダウンを選択します。

   > 🚨 **注意:** 対応せずにアラートをクローズしないでください。問題を隠すだけで、誤った安心感を与えてしまいます。場合によってはサイバーセキュリティ部門で追加アラートが発生することもあります。🤦

1. `Revoked（無効化済み）` オプションを選択し、コメント欄に対応内容を記載します（例は下記）。その後、**Close alert（アラートをクローズ）** を選択します。

   ```txt
   シークレットの所有者に連絡し、漏洩したシークレットが置き換えられた証拠を提供してもらいました。
   ```

   > 💡 **ヒント:** 監査ログで後から調査が必要になった場合に備え、詳細な記録が重要です。

   <img width="250" alt="Screenshot of an alert being closed as revoked with a useful comment" src="https://github.com/user-attachments/assets/a65bf6be-2be3-4096-9afa-db7a3fb02ecd" />


1. アラートのステータスが `Closed（クローズ済み）` となり、監査証跡に説明が記録されます。

   <img width="250" alt="image" src="https://github.com/user-attachments/assets/fdff5ad5-40ab-4f35-9f37-284dfe129ebd" />

   <img width="450" alt="image" src="https://github.com/user-attachments/assets/29bde02e-88d8-4fe2-b39c-a85a7b705908" />

1. 少なくとも1件のアラートが解決できたら、Monaにこのステップが完了したことをコメントで伝え、次のステップを案内してもらいましょう。

   ```txt
   こんにちは @professortocat、セキュリティアラートを解決しました。次は何をすればいいですか？
   ```
