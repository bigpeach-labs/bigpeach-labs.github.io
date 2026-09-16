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

## 更新するときの注意

- **`/pinkypromise/` の URL は変更しない。** ストア掲載情報に登録済みなのに加えて、この URL は PinkyPromise が書き出した共有画像の QR コードに焼き込まれている。利用者が誰かに送った画像は後から差し替えられないので、パスを変えるとその画像の QR が永久に死ぬ。
- 同じ理由で、**公開済みページのパスは変更しない**。
- 法務ページの本文を変更したら、ページ末尾の最終更新日も合わせて更新する。ストア導線ページに最終更新日は無い。
- 法務ページの日本語版と英語版は同じ内容を保つ。英語版は参考訳で、齟齬がある場合は日本語版が優先する旨を明記している。
