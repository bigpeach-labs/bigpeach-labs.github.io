# bigpeach-labs.github.io

BigPeach のアプリの法務ページと、ストアへの導線ページを公開する静的サイト。GitHub Pages で `main` ブランチのルートをそのまま配信している。

| ページ | URL |
| --- | --- |
| インデックス | https://bigpeach-labs.github.io/ |
| PinkyPromise ストア導線 | https://bigpeach-labs.github.io/pinkypromise/ |
| PinkyPromise プライバシーポリシー | https://bigpeach-labs.github.io/pinkypromise/privacy/ |
| PinkyPromise Privacy Policy (EN) | https://bigpeach-labs.github.io/pinkypromise/privacy/en/ |
| PinkyPromise 利用規約 | https://bigpeach-labs.github.io/pinkypromise/terms/ |
| PinkyPromise Terms of Use (EN) | https://bigpeach-labs.github.io/pinkypromise/terms/en/ |

ビルドは不要。素の HTML を直接編集して push すれば数十秒で反映される。`.nojekyll` を置いて Jekyll のビルドを止めている。法務ページのスタイルは `assets/legal.css` を共有し、インデックスとストア導線ページはそれぞれ個別のインラインスタイルを持つ。

アプリ本体のリポジトリは private のため、Free プランでは Pages を公開できない。公開が必要なページだけをこのリポジトリに置いている。

## PinkyPromise のストア導線ページ

`pinkypromise/index.html` は、UA を見て App Store / Google Play へ振り分ける 1 枚のページ。PinkyPromise が書き出す共有画像のフッターに、この URL の QR コードが載っている。

言語の扱いだけ法務ページと違う。QR は URL を 1 つしか運べず `/en/` を分ける方式では到達できないため、このページは 1 枚で日本語と英語を出し分ける。`?lang=ja` / `?lang=en` の明示指定が最優先で、無ければ `navigator.languages` を見て決め、どちらでもない言語と言語情報が取れない場合は英語にフォールバックする。

### 経路の目印 `?c=`

`?c=<経路>` を付けて開くと、ストアへのリンクにその経路を付けて渡す。どこから来た人がインストールしたかを、SDK を入れずに各ストアの管理画面で数えるため。

| ストア | 付けるもの | 数字が出る場所 |
| --- | --- | --- |
| App Store | `pt=<プロバイダトークン>&ct=<経路>&mt=8` | App Store Connect の App 分析 → 獲得 → キャンペーン |
| Google Play | `referrer=utm_source=<経路>&utm_campaign=<経路>`（エンコード済み） | Play Console のストア掲載情報の獲得レポート（UTM） |

- 経路に使えるのは英数字・`_`・`-` の 40 文字まで（App Store の `ct` の上限）。外れた値は無視して、目印なしでストアへ渡す。
- App Store 側は `index.html` の `APP_STORE_PROVIDER_TOKEN` が空のあいだは何も付けない。値は App Store Connect でキャンペーンリンクを生成すると出る `pt=` の数字。
- App Store Connect は、1 つの経路で初回ダウンロードが 5 件を超えるまで数字を出さない。

使っている経路:

| `c` | 経路 |
| --- | --- |
| `cert` | PinkyPromise が書き出した共有画像の QR |
| `formation` | PinkyPromise の成立画面に出る QR（署名を終えた相手が、その場で自分のスマホで読みとる） |

## 更新するときの注意

- **`/pinkypromise/` の URL は変更しない。** ストア掲載情報に登録済みなのに加えて、この URL は PinkyPromise が書き出した共有画像の QR コードに焼き込まれている。利用者が誰かに送った画像は後から差し替えられないので、パスを変えるとその画像の QR が永久に死ぬ。
- 同じ理由で、**公開済みページのパスは変更しない**。
- **`?c=` の読み取りを消さない。** 共有画像の QR は `?c=cert` 付きで焼き込まれている。消しても QR は死なないが、そこから来た人を数えられなくなる。
- 法務ページの本文を変更したら、ページ末尾の最終更新日も合わせて更新する。ストア導線ページに最終更新日は無い。
- 法務ページの日本語版と英語版は同じ内容を保つ。英語版は参考訳で、齟齬がある場合は日本語版が優先する旨を明記している。
