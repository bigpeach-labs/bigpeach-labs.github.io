# bigpeach-labs.github.io

BigPeach のアプリ一覧ページと、PinkyPromise の旧 URL の転送元。GitHub Pages で `main` ブランチのルートをそのまま配信している。

PinkyPromise のストア導線と法務ページは [pinkypromise-site](https://github.com/bigpeach-labs/pinkypromise-site) に移り、`https://pinkypromise.pink/` で配信している。このリポジトリの `pinkypromise/` 配下は、新しい URL へ飛ばすだけのページになっている。

| 旧 URL | 転送先 |
| --- | --- |
| https://bigpeach-labs.github.io/pinkypromise/ | https://pinkypromise.pink/get |
| https://bigpeach-labs.github.io/pinkypromise/privacy/ | https://pinkypromise.pink/privacy/ |
| https://bigpeach-labs.github.io/pinkypromise/privacy/en/ | https://pinkypromise.pink/privacy/en/ |
| https://bigpeach-labs.github.io/pinkypromise/terms/ | https://pinkypromise.pink/terms/ |
| https://bigpeach-labs.github.io/pinkypromise/terms/en/ | https://pinkypromise.pink/terms/en/ |

GitHub Pages はサーバー側の 301 を返せないので、JS の `location.replace` で転送し、JS が動かない環境向けに meta refresh を置いている。JS はクエリとハッシュを引き継ぐ。共有画像の QR は `?c=cert` 付きの旧 URL を指しているので、クエリが落ちるとその経路を数えられなくなる。

ビルドは不要。素の HTML を直接編集して push すれば数十秒で反映される。`.nojekyll` を置いて Jekyll のビルドを止めている。

アプリ本体のリポジトリは private のため、Free プランでは Pages を公開できない。このリポジトリは Pages のために public にしている。

## 更新するときの注意

- **このリポジトリと転送ページは消さない。** 旧 URL は、PinkyPromise が書き出した共有画像の QR と古いバージョンのアプリに焼き込まれている。利用者が送った画像は後から差し替えられないので、消すとその QR が永久に死ぬ。
- **転送ページからクエリの引き継ぎを消さない。**
- PinkyPromise のページの中身を変えるときは pinkypromise-site 側を編集する。
