# playwright-hands-on

- [playwright-hands-on](#playwright-hands-on)
  - [はじめに](#はじめに)
  - [Playwrightとは？](#playwrightとは)
  - [準備](#準備)
  - [テストを眺めてみよう](#テストを眺めてみよう)
  - [テストをじっくり眺めてみよう](#テストをじっくり眺めてみよう)
  - [テストを生成してみよう](#テストを生成してみよう)
  - [テストをデバッグモードで動かしてみよう](#テストをデバッグモードで動かしてみよう)
  - [自動テストを試そう](#自動テストを試そう)

## はじめに

Playwrightを社内に布教を目的としたハンズオン資料です。
目標は自走できそうという感覚を持ってもらうことです。

## Playwrightとは？

Microsoftが提供するEnd to Endに特化したエンジニアフレンドリーなテストライブラリです。
主要な競争先としては[cypress](https://www.cypress.io/)があります。
特筆すべき特徴にChromium、WebKit、FireFox、つまりChrome、Edge、Safari、 FireFoxと主要なブラウザに対して自動テストが実行できることがあります。

https://playwright.dev/

## 準備

[ハンズオン用のレポジトリ](https://github.com/mymactive/playwright-hands-on)のクローンをし、以下を実行してください。

```
npm install
```

playwrightが初めての方は以下の実行もお願いします。
これはplaywright用に動かすブラウザのインストールも兼ねてます。
```
npx playwright install
```

## テストを眺めてみよう
playwright公式から提供されている`example.spec.ts`を動かしてみましょう！

```
npx playwright test --headed
```

チェックポイント
- ブラウザが立ち上がって実行されたこと
- Chromium, firefox, webkitの3種類のブラウザで実行されたこと
- 並列実行されたこと

## テストをじっくり眺めてみよう
高速でテストが実行されたため、何が何だかわからなかったかもしれません。
実際私ははじめて実行した時は何をしていたのかよく分かりませんでした。
次は何をしているのか、じっくり眺めてみましょう。

```
PWDEBUG=1 npx playwright test --project=chromium 
```

チェックポイント
- chromiumブラウザが立ち上がったこと
- page.gotoでブラウザの遷移ができたこと
- expect(XXX)で値の検証をしたこと
他は色々書いてありますが、現状理解しなくても大丈夫です

## テストを生成してみよう
次はテストコードを作ってみましょう。
playwrightには強力なテストコード生成コマンドが存在します。
それを使って弊社をぶっ壊してやりましょう。

```
npx playwright codegen https://www.team-lab.com/
```

結果はコピーをして、新しく`/tests/`ディレクトリ配下に`.spec.ts`形式のファイルを作成してください

チェックポイント
- コードがGUI操作で生成できたこと
- .spec.tsファイルをtestsディレクトリ配下に作ったこと

## テストをデバッグモードで動かしてみよう
早速作成したテストを試してみましょう。

```
PWDEBUG=1 npx playwright test --project=firefox tests/<your_test_file_name>.spec.ts
```

うまく実行できたでしょうか？
失敗することもあるかもしれませんが、気にせずなんとなく作れる感覚を大事にしてください！

チェックポイント
- GUI操作で作られたテストを実際に目で確認できたこと
- GUI操作に対応したテストメソッドが何かをなんとなく理解できたこと

## 自動テストを試そう

思ったよりも簡単に、しかしクロスブラウザテストができたかと思います。
ここから先はplaywright公式のドキュメントを読み込んでいけばどうにかなります！
興味を持った方は早速色々と遊んでみてはいかがでしょうか。

https://playwright.dev/
