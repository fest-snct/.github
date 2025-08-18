## 高専祭HP用

2025以降の担当になった方は2025のリポジトリを参照して作ってください。

## 自動デプロイ

mainブランチにmerge(push)したら、レンタルサーバーに自動デプロイできるようになる

以下の`.yml`ファイルをプロジェクト直下の`.github/workflow`に新しく作成してください。

```yml
name: Deploy to Sakura

on:
  push:
    branches:
      - main   # mainブランチにpushしたら実行

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Deploy via SSH
        uses: appleboy/ssh-action@v1.2.0
        with:
          host: fest-snct.sakura.ne.jp
          username: fest-snct
          key: ${{ secrets.SAKURA_SSH_KEY }}
          script: |
            cd /home/fest-snct/www/2025    # 2025は変更して適切な年に直してください
            git fetch origin
            git merge origin/main

```

<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->
