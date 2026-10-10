# AGENTS.md

这个仓库是《高性价比人生指南》的正文。

- **改这本书**（增删条目、改正文、动工具脚本）：规则全在 [CLAUDE.md](CLAUDE.md) 里，全部适用，先读完再动手。文件名叫 CLAUDE.md 只是历史原因，内容与工具无关。
- **用这本书回答问题**（有人问该不该做、值不值、怎么选、出事了先做什么、能领哪笔钱、犯不犯法）：按 [skills/life-decision-guide/SKILL.md](skills/life-decision-guide/SKILL.md) 执行，先查条目再答，答复里注明出自第几节第几条。装到别的目录去用的办法见 [skills/life-decision-guide/README.md](skills/life-decision-guide/README.md)。

## Cursor Cloud specific instructions

- 检索页是静态站点，没有后端。环境启动时会在 8000 端口执行 `python3 -m http.server`。`index.html` 必须用 http 打开，用文件协议直接打开会空白。
- 正文检查不装依赖：`node tools/check-refs.mjs --check`、`node tools/check-plain.mjs`、`node tools/sync-stats.mjs --check`。最后这条只查不改；去掉 `--check` 会改 README、index.html 并重截 `og.png`。
- EPUB 依赖在 `tools/epub`，用 `npm ci`。生成命令是 `node tools/epub/build.mjs`、`node tools/offline/build.mjs`、`node tools/pdf/build.mjs`。PDF 用已装好的 pandoc 3.11、typst 0.15.1 和 `fonts-noto-cjk`。EPUB 校验：`java -jar /opt/epubcheck/epubcheck.jar dist/HowToLiveBetter.epub`。产物在 `dist/`，不入库。
