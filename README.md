# シークレット保護の紹介

_シークレット保護を設定してシークレットを特定し、新しいシークレットがリポジトリにコミットされるのを防ぐ方法を学びましょう。_

## ようこそ

GitHubのリポジトリに誤って保存された平文の認証情報は、攻撃者の一般的な標的です。実際、GitHubプラットフォーム上では毎年100万件を超えるトークンが保存されていることが判明しています。これを防ぐ方法を学びましょう！

- **対象者**: 開発者、DevOpsエンジニア、セキュリティチーム
- **学べること**: リポジトリ内の平文認証情報を特定し、今後GitHubに公開されるのを防ぐ方法
- **前提条件**: gitとGitHubの基本的な機能。 [GitHub入門](https://github.com/skills/introduction-to-github) の受講をおすすめします。
- **所要時間**: このコースは15分以内で完了します。

このコースで学ぶこと:

1. シークレット保護を有効化する
2. リポジトリに保存されているシークレットを特定する
3. プッシュ保護を有効化する
4. シークレットがリポジトリに書き込まれるのを防ぐ

### 演習の始め方

演習を自分のアカウントにコピーし、お気に入りのOctocat（Mona）に**約20秒**待ってもらい、最初のレッスンの準備ができたら**ページをリフレッシュ**してください。

[![start-exercise](https://img.shields.io/badge/Copy%20Exercise-%E2%86%92-1f883d?style=for-the-badge&logo=github&labelColor=197935)](https://github.com/new?template_owner=yutaka-art&template_name=introduction-to-secret-scanning&owner=%40me&name=skills-introduction-to-secret-scanning&description=GitHub+Skills:+Introduction+to+Secret+Scanning&visibility=public)

<details>
<summary>問題が発生した場合 🤷</summary><br/>

演習をコピーする際は、以下の設定をおすすめします:

- オーナーには、ご自身の個人アカウントまたはリポジトリをホストする組織を選択してください。

- プライベートリポジトリではActionsの分数が消費されるため、パブリックリポジトリの作成をおすすめします。

20秒経っても演習が準備できない場合は、[Actions](../../actions) タブを確認してください。

- ジョブが実行中か確認してください。少し時間がかかる場合もあります。

- ページに失敗したジョブが表示された場合は、Issueを提出してください。バグを見つけてくれてありがとう！🐛

</details>

---

&copy; 2025 GitHub &bull; [行動規範](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MITライセンス](https://gh.io/mit)