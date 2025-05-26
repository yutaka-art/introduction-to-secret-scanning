## ステップ1: シークレット保護を有効にする

メールを確認すると、GitHubから「有効なシークレットが見つかった可能性があります」という件名のアラートが届いているかもしれません。あら、大変！😮

心配しないでください！この演習では、意図的に期限切れの認証情報を入れています。パブリックリポジトリではシークレット保護が無料で利用できるからです。素晴らしいですね！🕵️

このステップでは、リポジトリでシークレット保護を有効にします。有効化した後、新しい認証情報を追加し、シークレット保護がどのように認証情報を検出してアラートを出すかを確認します。

> [!WARNING]
> リポジトリがプライベートの場合は、続行するために [GitHub Advanced Security](https://docs.github.com/ja/enterprise-cloud@latest/get-started/learning-about-github/about-github-advanced-security) が必要です。有効にするには、[この演習リポジトリをパブリックに変更すること](https://docs.github.com/ja/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility) をおすすめします。

### シークレットとは？

この文脈でのシークレット（または認証情報）とは、サービスへのアクセスを許可する平文の文字列、または文字列のペアのことです。例としては、AWSのシークレットアクセスキー/ID、Google APIキー、GitHubのパーソナルアクセストークン（PAT）などがあります。

GitHub Docsには[サポートされているすべてのパターン](https://docs.github.com/ja/code-security/secret-scanning/secret-scanning-patterns#supported-secrets)の一覧があります。

### シークレット保護とは？

シークレット保護は、チームがこれらの平文認証情報を特定・削除し、GitHubに書き込まれるのを防ぐルールを作成できる強力なツールです。

シークレット保護は**すべてのプランのパブリックリポジトリで無料**で利用できます。プライベートリポジトリでシークレット保護機能が必要な企業は [GitHub Advanced Security](https://github.com/security/advanced-security) をご検討ください。シークレット保護だけでなく、高度な静的解析、ソフトウェア構成解析（SCA）、エンタープライズ向けAppSec管理ツールも提供され、リスクプロファイルの低減に役立ちます。

### :keyboard: アクティビティ: シークレット保護を設定する

1. リポジトリのヘッダーから **Settings（設定）** を新しいタブで開きます。

1. 左側のナビゲーションで、**Security（セキュリティ）** セクションの下にある **Advanced Security** を選択します。

1. **Code Scanning** と **Dependabot** セクションを下にスクロールし、**Secret Protection** セクションを見つけます。

   > 💡 **ヒント:** [コードスキャン](https://github.com/skills/introduction-to-codeql) や [サプライチェーン保護](https://github.com/skills/secure-repository-supply-chain) の演習もあります！

1. デフォルトの設定を以下のように調整します。

   - **Secret Protection:** `enabled`（有効）
   - **Push Protection:** `disabled`（無効）

   <img width="400" alt="Secret protection configuration settings" src="https://github.com/user-attachments/assets/7b999e54-dbf4-400d-8730-17b96bc06de1" />

### :keyboard: アクティビティ: 機密ファイルをコミットする

それでは、（うっかり）機密ファイルをコミットして、どのように動作するか見てみましょう。ご安心ください、これらは無効な認証情報です。

1. リポジトリのヘッダーで **Code** タブをクリックします。

1. ファイル一覧の上にある **Add file** ドロップダウンから **Create new file** を選択します。

   <img width="350" alt="New file button" src="https://github.com/user-attachments/assets/8f3f8da8-1471-485a-9df5-8c03ecba2d8e"/>

1. ファイル名に `credentials.yml` と入力し、以下の**無効な**サンプル認証情報をコピーします。

   <img width="400" alt="New file button" src="https://github.com/user-attachments/assets/40f5ce62-936c-4d71-8c51-02c724d5aac0"/>

   ```yaml
   default:
     aws_access_key_id: AKIAQYLPMN5HNM4OZ56B
     aws_secret_access_key: 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
     mongodb: mongodb+srv://svc-admin:kLeioeBne5lsopPf@mergington-high.avocado.mongodb.net
     output: json
     region: us-east-2
   ```

1. 右上の **Commit changes...** ボタンを使って、`main` ブランチに直接コミットします。

   > ❗️ **重要:** デフォルトブランチへの直接コミットは通常おすすめしませんが、この演習を簡単にするために行っています。

1. 認証情報ファイルを（うっかり）共有したことで、Monaがすぐに気づき、次のステップを準備してくれるはずです。
