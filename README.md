# eighty-seven DR-1101

ブラウザで動くドラムマシン・シーケンサー。インストール不要・単一HTMLファイル。

![DR-1101](https://img.shields.io/badge/Web%20Audio-API-orange) ![License](https://img.shields.io/badge/license-MIT-blue)

## デモ

`DR1101.html` をブラウザで開くだけで動作します。サーバー不要。

## 機能

| カテゴリ | 内容 |
|---|---|
| **シーケンサー** | 8パート × 最大16ステップ、4バンク × 16パターン（計64パターン） |
| **ベロシティ** | 弱 / 中 / 強の3段階 |
| **スウィング** | 0〜100%のグルーブ調整 |
| **MIX** | VOL / TUNE / DECAY / TONE / SAT / REV をパートごとに調整 |
| **REVERB** | Schroeder / IR モード切替（Plate / Room / Hall） |
| **FX1** | コンプレッサー + 3バンドEQ |
| **FX2** | Isolator / LPF / HPF / Distortion / Bit Crush / Lo-fi |
| **FX3** | Phaser / Delay / Ring Mod / Lo-fi |
| **SONG MODE** | 最大16スロット × 16ソング、ループ・BPM変化対応 |
| **サンプル** | WAVファイルをパートごとにロード可能 |
| **エクスポート** | JSON（全データ）/ WAV（2ループレンダリング） |
| **Sound Set** | A〜D の4スロットにサンプル＋MIX/FX設定を保存・共有 |
| **CLOCK OUT** | オーディオパルス + MIDI クロックマスター出力 |
| **自動保存** | localStorage に編集内容を自動バックアップ |

## 使い方

### 基本

1. `DR1101.html` をブラウザで開く（Chrome / Edge 推奨）
2. **START** ボタン（またはスペースキー）で再生開始
3. LCD のマス目をタップ / クリックでステップ ON/OFF
4. **WRITE** で現在パターンを保存

### ステップ入力

- タップでON/OFF
- **VEL** ボタンONにすると 弱→中→強→OFF のサイクル入力
- ドラッグで連続入力

### パターン管理

- フッター PAT 1〜16 でパターン切替（再生中は1小節末に反映）
- **BANK A〜D** で64パターン管理
- **COPY → PASTE** でパターンコピー
- **UNDO** で直前操作を取り消し

### Sound Set の共有

1. SETTING タブ → 各パートに WAV をロード
2. MIX / FX を調整
3. **SAVE SOUND SET A〜D** で保存
4. **EXPORT SET** で JSON ファイルを書き出し → 受け取った人は **IMPORT SET** で読み込み

## バグ修正履歴

| # | 修正内容 |
|---|---|
| 1 | `stopSong()` 内の `songNoSel.textContent` 読み捨てを削除 |
| 2 | `runSongStep()` 内の `songNoSel.value` 読み捨てを、現在スロットへの反映に修正 |
| 3 | `saveHist()` がコミット済みパターンではなく作業中パターンを保存するよう修正 |
| 4 | SONG MODE のタイマーが `state.timer` と `songState.timer` で混在していた問題を統一 |
| 5 | `createScriptProcessor`（非推奨API）に注釈を追加 |

## ブラウザ対応

| ブラウザ | 対応状況 |
|---|---|
| Chrome 90+ | ✅ 完全対応 |
| Edge 90+ | ✅ 完全対応 |
| Firefox 90+ | ✅ 対応（一部FXで差異あり） |
| Safari 15+ | ⚠️ AudioContext の制限あり |

## ライセンス

MIT License
