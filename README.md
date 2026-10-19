# Growth Coach

个人成长与 IELTS 备考工作区，用于家中个人电脑及私有 Git 仓库。保存插件源码、个人背景、生活记录、学习资料和练习反馈，通过 Git 累积历史。

## 目录

```text
artifacts/
  growth-coach/                 初始插件源码
  growth-coach-update/          0.1.1 更新文件
  growth-coach-life-update/     0.1.2 更新文件
  growth-coach-ielts-update/    0.2.0 更新文件
personal-growth/
  life-journal-template.md      生活记录模板
  life-journal/YYYY-MM.md       按月追加生活记录
  ielts/
    profile.md                 备考目标与基线
    directory-guide.md         雅思目录、编号和链接约定
    materials/                 学习资料及附件，使用时创建条目
    sessions/                  每次练习、原作、修改稿与反馈
    progress/
      session-index.csv        练习索引
      weekly/                  每周复盘
    templates/                 练习、资料与周复盘模板
```

空目录不由 Git 保存，首次归档时可按需创建。

## 日常使用

1. 在 `personal-growth/life-journal/` 当月文件中按日期追加记录。每天三行也可以，不要求补齐漏记。
2. 雅思目标与已有成绩填写在 `personal-growth/ielts/profile.md`，未知信息保留为 unknown。
3. 学习资料按 `materials/M001/source.md` 建档，记录书名、版次、页码或时间范围；用户提供的附件放在对应 `attachments/` 中。同一资料复用编号。
4. 使用练习模板创建 `sessions/YYYY-MM/YYYY-MM-DD-reading-01/session.md`，技能可为 listening、reading、writing 或 speaking。关联资料、原始答题和反馈；修改稿另存，保留原作。
5. 生活日记只链接练习，不重复粘贴全部内容。完成归档后更新练习索引，每周使用周复盘模板回顾。

Markdown 链接以当前文件为基准计算相对路径，使用 `/`。详细规则见 [雅思目录说明](personal-growth/ielts/directory-guide.md)。普通编辑器即可使用，Obsidian 可选。

与 Growth Coach 对话时可以说：“记录今天”“归档这次雅思练习”或“根据已有记录做周复盘”。本地记录需在有文件访问能力的会话中读取和保存；插件没有自动采集生活、自动同步或自动提醒功能。

## 成长量化

分别记录学习投入、独立表现及延迟复测结果。学习资料说明接触过什么，不能单独证明掌握程度。听读保留正确数、题数和条件；写口反馈保留评分依据与原文证据。区分首次、重复、修订与复测，以及独立完成和使用辅助的情况。

AI 估分与正式成绩分开；数据不足时不推断趋势。只有文字稿时不评价发音。心理背景中的自我判断保留未确诊的限定，日记不用于自动诊断。

## 插件维护

当前私有插件：[Growth Coach](https://chatgpt.com/plugins/plugins_6ad5bf683b748191bc18aa2cbd93d915)，本次工程中最新保存版本为 `0.2.0`。

`artifacts/` 中的更新目录是历史更新包源码，可能只包含变更文件，不能单独视为完整安装包。完整源码需要从当前插件获取，或依次合并初始目录、0.1.1、0.1.2、0.2.0 更新文件；后续同路径文件覆盖较早版本。生成的兼容 manifest 与根 manifest 应保持版本和展示信息一致。

更新前读取线上当前源码及 release ID，修改必要文件，检查 JSON、技能 YAML 和文件引用，打包到源码目录之外。通过 Plugin Creator 更新原插件，并读取保存结果核对。日常生活记录和学习附件只保存在用户数据目录，不打包到插件。

## Git 与备份

插件源码、个人背景、生活记录、雅思练习、模板和进度均可提交到此私有仓库。`.gitignore` 排除构建压缩包、缓存、临时文件、机器专用配置和常见凭据文件；不会忽略整个 `artifacts/` 或 `personal-growth/`。

本机 `.mcp.json` 含连接配置及凭据，保持本地使用，不纳入 Git。可复用且不含凭据的配置可单独整理成示例文件。大型音视频和 PDF 不默认忽略，可按实际大小决定使用 Git LFS 或单独备份，并在记录中保留可定位的引用。

每次提交前检查 `git status --short` 和暂存差异，确认没有访问令牌或不需要备份的文件。推送到私有远程仓库后才有异机副本；本地提交本身不等于远程备份。
