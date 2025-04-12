[TurboWarp](https://turbowarp.org/) で使用するために修正された Scratch-GUI を [PenguinMod](https://studio.penguinmod.com) で使用するために修正しました 😀
[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/PenguinMod/penguinmod.github.io/)←オリジナルのpenguinModへのGitpodリンク
## Setup

完全な TurboWarp 環境をセットアップするには、https://docs.turbowarp.org/development/getting-started を参照してください。

GUI を操作したいだけであれば、アップストリームの Scratch-gui と同じプロセスになります。

## ライセンス

TurboWarp による Scratch への改変は、GNU General Public License v3.0 に基づいてライセンスされています。詳細は LICENSE または https://www.gnu.org/licenses/ をご覧ください。

以下は、私たちが保持する必要がある scrap-gui のオリジナルのライセンスです。これは、このプロジェクトのライセンスではありません。

```
Copyright (c) 2016, Massachusetts Institute of Technology
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

src/lib/default-project/dango.svg は [Twemoji](https://twemoji.twitter.com/) に基づいており、CC BY 4.0 https://creativecommons.org/licenses/by/4.0/ ライセンスに基づいています。

<!--

# scrap-gui
#### Scratch GUI は、Scratch 3.0 プロジェクトの作成と実行のためのインターフェースを構成する React コンポーネントのセットです。

## インストール
このプロジェクトを実行するには、Git と Node.js がインストールされている必要があります。

ご自身の Node 環境/アプリケーションの場合:
```bash
npm install https://github.com/LLK/scratch-gui.git
```
ご自身で編集/操作する場合:
```bash
git clone https://github.com/LLK/scratch-gui.git
cd scrap-gui
npm install
```

**git リポジトリの履歴に大きなファイルがいくつかあるため、`git clone` コマンドに `--depth=1` を追加することをおすすめします。**

## はじめに
このプロジェクトを実行するには、Node.js がインストールされている必要があります。

## 実行
リポジトリでコマンドプロンプトまたはターミナルを開き、次のコマンドを実行します。
```bash
npm start
```
次に [http://localhost:8601/](http://localhost:8601/) にアクセスします。プレイグラウンドはデフォルトの GUI コンポーネントを出力します。

## 他の Scratch リポジトリと並行して開発する

### このコードを参照する別のリポジトリを取得する

`scratch-gui` を、それに依存する他の Scratch リポジトリと並行して開発する場合、他のリポジトリでは、`npm install` を使用してデフォルトで検出される最新の製品版の Scratch-gui を取得するのではなく、ローカルの `scratch-gui` ビルドを使用するように設定できます。

ローカルの `scratch-gui` コードを他のプロジェクトの `node_modules/scratch-gui` にリンクする方法は次のとおりです。

#### 設定

1. ローカルの `scratch-gui` リポジトリのトップレベルで、以下の操作を行います。
1. `npm install` が実行されていることを確認します。
2. `BUILD_MODE=dist npm run build` を実行して `dist` ディレクトリをビルドします。
3. `npm link` を実行して、このリポジトリへのリンクを確立します。

2. `scratch-gui` に依存する各リポジトリ（`scratch-www` など）のトップレベルで、以下の操作を行います。
1. `npm install` が実行されていることを確認します。
2. `npm link scrap-gui` を実行します。
3. リポジトリをビルドまたは実行します。

#### `npm run watch` の使用

`BUILD_MODE=dist npm run build` の代わりに、`BUILD_MODE=dist npm run watch` を使用できます。これにより、`scratch-gui` コードの変更が監視され、変更があった場合は自動的にリビルドされます。この方法は信頼できない場合があります。問題が発生した場合は、問題が解決するまで `BUILD_MODE=dist npm run build` に戻してみてください。

#### ああ、うまくいきませんでした！

リンクが正しく機能しない場合は、以下をお試しください。
* 上記の手順をステップごとに実行し、順序を変更しないでください。特に重要なのは、`npm install` を `npm link` の前に実行することです。リンク後にインストールすると、リンクがリセットされてしまうためです。
* リポジトリがマシンのファイルツリー上で兄弟関係にあることを確認してください。例: `.../.../MY_SCRATCH_DEV_DIRECTORY/scratch-gui/` と `.../.../MY_SCRATCH_DEV_DIRECTORY/scratch-www/`
* Node.js バージョンの一貫性: 複数の Scratch リポジトリ用に複数のターミナルタブまたはウィンドウを開いている場合は、すべて同じバージョンの Node.js を使用してください。
* 他に方法がない場合は、両方のリポジトリで `npm unlink` を実行してリンクを解除し、最初からやり直してください。

## テスト
### ドキュメント

テストを作成する際には、[Jest](https://facebook.github.io/jest/docs/en/api.html) と [Enzyme](http://airbnb.io/enzyme/docs/api/) のドキュメントを確認することをお勧めします。

その他のオプションについては、[jest cli ドキュメント](https://facebook.github.io/jest/docs/en/cli.html#content) を参照してください。

### テストの実行

*注: Windows をお使いの場合は、Git Bash/MINGW64 ではなく、Windows の `cmd.exe` でこれらのスクリプトを実行してください。*

テストを実行する前に、この (scratch-gui) リポジトリのトップレベルから `npm install` を実行してください。

#### メインテストコマンド

リンター、ユニットテスト、ビルド、統合テストをすべて一度に実行するには:
```bash
npm test
```

#### ユニットテストの実行

ユニットテストを個別に実行するには:
```bash
npm run test:unit
```

ウォッチモードでユニットテストを実行するには: (コードの変更を監視し、継続的にテストを実行します):
```bash
npm run test:unit -- --watch
```

統合テストのファイル (この例では `button` テスト) を 1 つだけ実行できます:

```bash
$(npm bin)/jest --runInBand test/unit/components/button.test.jsx
```

#### 統合テストの実行

統合テストでは、ヘッドレスブラウザを使用して、リポジトリが生成する実際の HTML と JavaScript を操作します。このアクティビティは表示されません (ただし、サウンドを再生すると聞こえます)。

統合テストを実行するには、まずブラウザで読み込めるビルドを作成する必要があります。

```bash
npm run build
```

その後、すべての統合テストを実行できます。

```bash
npm run test:integration
```

または、統合テストのファイル（この例では `backpack` テスト）を 1 つだけ実行することもできます。

```bash
$(npm bin)/jest --runInBand test/integration/backpack.test.js
```

ヘッドレス実行ではなく、ブラウザでテストを実行する様子を確認する場合は、以下を使用します。

```bash
USE_HEADLESS=no $(npm bin)/jest --runInBand test/integration/backpack.test.js
```

## トラブルシューティング

### オプションの依存関係を無視する

`npm install` を実行すると、オプションの依存関係に関する警告が表示される場合があります。依存関係:

```
npm WARN オプション 失敗したオプション依存関係 /chokidar/fsevents をスキップしています:
npm WARN notsu
