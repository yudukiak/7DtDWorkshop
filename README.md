7 Days To Die のMOD置き場
=====

## MODのインストール
1. ZIPを解凍する
2. <kbd>Windows</kbd>+<kbd>R</kbd> で `ファイル名を指定して実行` を起動させる
3. 「名前」に `%appdata%\7DaysToDie` を記入して「OK」ボタンをクリック
4. 7 Days To Die のフォルダが開くので `Mods` というフォルダを作成する（あるなら無視）
5. 作成したフォルダ内にZIPを解凍して出てきたフォルダをそのまま置くだけ

### フォルダの階層
- 7DaysToDie
  - Mods
    - 各種MODフォルダ
      - Config
      - ModInfo.xml
      - など

## MODの作成

### xmlの作成
1. `steamapps\common\7 Days To Die\Data\Config` から必要なXMLをパクって弄るだけ

#### 参考サイト
- [xml書き換え - 7 Days to Die Japan Wiki*](https://wikiwiki.jp/7daystodie/xml%E6%9B%B8%E3%81%8D%E6%8F%9B%E3%81%88)
- [Modlet - 7 Days to Die Japan Wiki*](https://wikiwiki.jp/7daystodie/xml%E6%9B%B8%E3%81%8D%E6%8F%9B%E3%81%88/Man/Modlet)

### unity3dの作成
1. 適当なバージョンのUnityをインストール（A21なら [2021.3.x](https://unity.com/releases/editor/archive#download-archive-2021) あたり）
2. 適当に3Dでプロジェクトを立ち上げる
3. [A21 NPCMod and Addons - Mods - 7 Days to Die](https://community.7daystodie.com/topic/26974-a21-npcmod-and-addons/page/1/#comments) に張ってある「 [A21_1bTutorialProject.zip - Google ドライブ](https://drive.google.com/file/d/1yPQ2yOj1Oe7pOml3ytfZcNggWWTAD4gq/view) 」からZIPをダウンロード
4. ZIPを解凍して `A21TutorialProject\Assets\MultiPlatformExportAssetBundles.cs` を探す
5. 立ち上げたプロジェクトの `Assets` へ `MultiPlatformExportAssetBundles.cs` を入れる
6. 適当にディレクトリ作ったりして音源を入れる
7. ディレクトリに対して `右クリック` > `Build Unity3D AssetBundle From Selection` > `LZ4 Chunk-Compressed (Recommended) - Medium Compression - Fast to Load` を実行
8. すると `*.unity3d` を抽出可能
9. XMLは `<AudioClip ClipName="#@modfolder:Resources/抽出したファイル名.unity3d?音声ファイル名（拡張子不要）" />`

#### 参考サイト
- [7 Days To Die SDX Tutorial and Help](https://7d2dsdx.github.io/Tutorials/index.html?HowtoaddCustomSounds.html)
- [A21 NPCMod and Addons - Mods - 7 Days to Die](https://community.7daystodie.com/topic/26974-a21-npcmod-and-addons/page/1/#comments) ※蜘蛛の画像注意
- [Adding a new sound to game. - Page 2 - Discussion and Requests - 7 Days to Die](https://community.7daystodie.com/topic/12288-adding-a-new-sound-to-game/page/2/)
- [Steam コミュニティ :: ガイド :: TextMesh Proを使用したUnity製ゲームのフォントの差し替え方法について](https://steamcommunity.com/sharedfiles/filedetails/?id=2869701209)

### 確認用ツール
- [Releases · SeriousCache/UABE](https://github.com/SeriousCache/UABE/releases)
- [Releases · nesrak1/UABEA](https://github.com/nesrak1/UABEA/releases)
  - UABEよりUABEAの方が新しいバージョンらしい
- [Releases · Perfare/AssetStudio](https://github.com/Perfare/AssetStudio/releases)
  - `*.unity3d` を確認できるけど、公式リソースはファイルが大きくエラーを吐くので閲覧不可

## 7DtDのデータを抽出
1. [Releases · nesrak1/UABEA](https://github.com/nesrak1/UABEA/releases) をダウンロードして起動
2. データを抽出したいファイルをドラッグ＆ドロップする
   1. `\7DaysToDie_Data\data.unity3d` : 基本はコレ
   2. `\Data\Addressables\Standalone\...` : 武器のテクスチャやメッシュはコレ
3. `This bundle is compressed. Decompress to file or memory?` と尋ねられるので `Memory` を選択（※もしメモリー容量が少ない場合は `File` を選択するといいかも？）
4. 読み込みを終えたらプルダウンから閲覧したいリソースを選択
   1. `Resources/unity_builtin_extra` : 不明
   2. `globalgamemanagers` : 音源、メッシュ、テクスチャが含まれている
   3. `globalgamemanagers.assets` : 不明
   4. `level0` : 不明
   5. `level1` : 音源、メッシュ、テクスチャが含まれている
   6. `resources.assets` : 音源、メッシュ、テクスチャが含まれている
   7. `resources.assets.resS` : 開けない
   8. `sharedassets0.assets` : 不明
   9. `sharedassets0.assets.resS` : 開けない
   10. `sharedassets1.assets` : 音源、メッシュ、テクスチャが含まれている
   11. `sharedassets1.assets.resS` : 開けない
5. リソースを選択したら「Info」をクリック
6. Asset Info が開くので `View` から `Filter` を選択
7. `Deselect all` をクリックして、欲しいデータだけチェックして、閉じると絞り込める
   1. 効果音やボイスなら `AudioClip`
   2. テクスチャなら `Texture2D`
8.  欲しいデータを見つけたら `Plugins` をクリックして `Export ** file` を選び、OKをクリック