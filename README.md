# bigpeach-labs.github.io

BigPeach のアプリの法務ページを公開する静的サイト。GitHub Pages で `main` ブランチのルートをそのまま配信している。

| ページ | URL |
| --- | --- |
| インデックス | https://bigpeach-labs.github.io/ |
| PinkyPromise プライバシーポリシー | https://bigpeach-labs.github.io/pinkypromise/privacy/ |
| PinkyPromise Privacy Policy (EN) | https://bigpeach-labs.github.io/pinkypromise/privacy/en/ |
| PinkyPromise 利用規約 | https://bigpeach-labs.github.io/pinkypromise/terms/ |
| PinkyPromise Terms of Use (EN) | https://bigpeach-labs.github.io/pinkypromise/terms/en/ |

ビルドは不要。素の HTML を直接編集して push すれば数十秒で反映される。`.nojekyll` を置いて Jekyll のビルドを止めている。法務ページのスタイルは `assets/legal.css` を共有し、インデックスだけ個別のインラインスタイルを持つ。

アプリ本体のリポジトリは private のため、Free プランでは Pages を公開できない。公開が必要なページだけをこのリポジトリに置いている。

## 更新するときの注意

- 本文を変更したら、ページ末尾の最終更新日も合わせて更新する。
- 日本語版と英語版は同じ内容を保つ。英語版は参考訳で、齟齬がある場合は日本語版が優先する旨を明記している。
- ストア掲載情報に URL を登録済みのため、**公開済みページのパスは変更しない**。
