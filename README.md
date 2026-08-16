# molkkymania_app

Mölkky Mania の大会運営アプリ（新基盤）。

## 置き場所

| パス | 中身 |
|---|---|
| `/` | 仮の入口。あとで紹介ページに差し替える |
| `/app/` | **アプリ本体** |

## 8-4 との違い

大会データ（対戦表・設定・スケジュール・予選結果・トーナメント表・会場・開催中の大会）の
**読み取り先を GitHub の JSON から Supabase に変更**した。GitHub 上の JSON は読まない。

### 移行期の約束ごと（2026年8月〜9月）

- **書き込み（管理者の「配信」）は当面 GitHub のまま**
- GitHub → Supabase のコピーは `~/.molkkymania/sync_github_to_supabase.py` で行う
- つまり「配信してもすぐには新アプリに出ない。コピーを走らせると出る」
- 8月・9月の大会は **旧アプリ（longbeachknit/molkkymania-score）** で運営する
- 9月の大会が終わったら、書き込み側も Supabase へ切り替える

## 反映のしかた

```
python3 ~/.molkkymania/publish_app.py <HTMLファイル> "変更メモ"
```

バージョン番号はファイル名から自動で読み取る（`molkkymania_app_1_1.html` → `1_1`）。
