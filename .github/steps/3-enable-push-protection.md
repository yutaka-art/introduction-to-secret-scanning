## ステップ3: プッシュ保護を有効にする

このセクションでは、新しいシークレットが公開されるのを防ぐためにリポジトリを設定します。

### プッシュ保護とは？

誰かがGitHubにコード変更（プッシュ）を送信しようとすると、シークレットスキャンが高い確度でシークレットを検出します。検出されたシークレットはリスト化され、作成者が内容を確認して削除したり、必要に応じてそのままプッシュを許可したりできます。

### :keyboard: アクティビティ: プッシュ保護を設定する

> [!IMPORTANT]
> 学習のため、最初のステップでプッシュ保護を無効にしました。通常はすべてのパブリックリポジトリでデフォルトで有効になっています。

1. リポジトリのヘッダーで **Settings（設定）** タブをクリックします。
1. 左側のナビゲーションで **Security（セキュリティ）** セクションの下にある **Advanced Security** を選択します。
1. **Code Scanning** と **Dependabot** セクションを下にスクロールし、**Secret Protection** セクションを見つけます。
1. デフォルト設定を以下のように調整します。

   - **Secret Protection:** `enabled`（有効）
   - **Push Protection:** `enabled`（有効）

   <img width="400" alt="Secret protection configuration settings" src="https://github.com/user-attachments/assets/4ecbc9a5-f1b2-4b68-8a1e-667dee7a7661" />

### :keyboard: アクティビティ: シークレットのプッシュを試す

シークレットのプッシュ保護が有効になったので、実際に試してみましょう！

1. リポジトリのヘッダーで **Code** タブをクリックします。

1. ファイル一覧から `credentials.yml` ファイルをクリックしてプレビューします。

1. 内容プレビューの上にある **Edit** ボタンをクリックします。

   <img width="200" alt="pencil-light" src="https://github.com/user-attachments/assets/3dfb1b2e-6fee-4b69-8b38-fc7bfedc8772"/>

1. 下記の無効なシークレットをファイルにコピーし、`<REMOVE_ME>` の部分を削除してください。下記のスクリーンショットのようになります。

   ```txt
     github-token: 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
   ```

   ![Screenshot of credentials.yml being edited in the GitHub web interface. A newly added github-token is highlighted.](https://github.com/user-attachments/assets/d5e16dc7-ffa9-422a-bc37-89f5cbb26a2e)

1. 右上の **Commit changes...** ボタンを使って `main` ブランチに直接コミットしようとします。ファイルの更新をコミットする代わりに、プッシュ保護のアラートが表示されます。素晴らしい！🥰

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/19099848-4191-4fd7-b52b-be521d7f356c" />

> [!IMPORTANT]
> シークレットプッシュ保護は _**プッシュ時**_ のみスキャンします。ローカルコミットはチェックできません。ローカルコミット内にシークレットがあり、それが複数コミット前の場合は、ブランチのコミット履歴からシークレットを削除する必要があります。[コマンドラインでブロックされたプッシュを解決する方法](https://docs.github.com/ja/code-security/secret-scanning/pushing-a-branch-blocked-by-push-protection#resolving-a-blocked-push-on-the-command-line) を参照してください。

### :keyboard: アクティビティ: プッシュ保護をバイパスする

場合によっては、シークレットに似たコードを書いたためにコミットが誤ってブロックされることがあります（例：認証プロセスのテストコードなど）。そのような場合は、プッシュ保護をバイパスできます。練習してみましょう。

1. `It's used in tests` のラジオボタンを選択します。説明文が現在の学習ケースに合っていることを確認してください。

   <img width="400" alt="image" src="https://github.com/user-attachments/assets/04b51b50-c93b-4bce-ab2a-988ab42e8db2" />

1. **Allow secret** をクリックします。通知バナーが表示され、再度コミットを試せるようになります。

1. 右上の **Commit changes...** ボタンを使って `main` ブランチに直接コミットします。

1. ファイルが更新されると、Monaが作業内容をチェックします。チェック後、フィードバックと最終レビューが届きます。お疲れさまでした！これですべて完了です！🎉
