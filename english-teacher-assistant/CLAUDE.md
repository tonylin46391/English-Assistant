# 英語教師助手 — CLAUDE.md

## 專案目標
用 AI Agent 幫我整理教學素材。

## 角色設定
- 我是一位專業的英文老師
- 教學對象:國小學生

## 語言規則
- 所有單字與句子,一律以「英文 + 繁體中文」對照呈現
- 說明文字使用繁體中文
- 用詞與例句難度需符合國小學生程度,句子簡短、生活化

## 專案結構
```
english-teacher-assistant/
├── CLAUDE.md      # 專案說明與 Agent 規則(本檔)
├── .gitignore     # 排除帳號密碼、API KEY 等敏感檔案
├── README.md      # 專案簡介
└── .claude/skills/
    ├── startup/   # 開工:唯讀,回顧上次進度
    └── shutdown/  # 收工:寫入,commit/push + 更新駕駛艙
```

## 三處同步對照表
| 位置 | 路徑 / 名稱 | 說明 |
|---|---|---|
| 本機專案 | `english-teacher-assistant/` | 工作目錄(git 版本控制) |
| GitHub | `tonylin46391/English-Assistant`(私有 repo)<br>https://github.com/tonylin46391/English-Assistant.git | 遠端備份 |
| Obsidian | `003_AI/英語教師助手/` | 筆記與教學素材(總覽:`00_專案總覽.md`) |

## 開工 / 收工(對偶設計)
| Skill | 觸發詞 | 性質 | 做什麼 |
|---|---|---|---|
| `startup` 開工 | 開工、我來了、上次做到哪、我們繼續 | 唯讀(講) | 讀 Obsidian 駕駛艙 → git status + fetch(不 pull)→ 結構化簡報 → 等我選方向 |
| `shutdown` 收工 | 收工、下班、同步、換電腦繼續做 | 寫入(寫) | 盤點今日 → commit + push → 更新 Obsidian 駕駛艙 |

駕駛艙:`003_AI/英語教師助手/00_專案總覽.md`(開工讀、收工寫,格式由 shutdown 定義)。

## 工作規則
- 不要把 API KEY、密碼、`.env` 提交到 Git
- 重大修改前先 commit
