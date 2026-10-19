# 学习目录约定

默认在用户选定的 personal-growth 下组织；已有生活日记不移动、不覆盖。普通 Markdown 相对链接，从当前文件计算路径，使用 /；空格编码为 %20。兼容普通编辑器，Obsidian 可选，无需插件或云同步。

```text
personal-growth/
  life-journal/YYYY-MM.md
  ielts/
    profile.md
    materials/M001/source.md
    materials/M001/attachments/     用户提供的 PDF、图片、音频等
    sessions/YYYY-MM/YYYY-MM-DD-reading-01/
      session.md
      response-v1.md               原始答题，可为其他实际格式
      response-v2.md               修改稿，不覆盖原稿
      feedback.md
      attachments/                用户录音、答题截图等
    progress/session-index.csv
    progress/weekly/YYYY-MM-DD.md
    templates/                    可复用模板
```

ID：资料 M001 递增，创建前检查避免冲突；session_id 使用目录名，同日同技能序号递增。同一资料复用 ID，不反复复制。source.md 保存来源、版次、页码/时间范围、访问状态、附件相对链接；材料多于一份时全部关联。不要下载或复制用户未提供的整本教材，仅记录书名/版次/页码和合法链接也可。

session.md 关联 material_id、实际练习范围、原始回答、反馈及复测记录。可以先只有 session.md，其余文件在实际有内容时创建，不能生成假证据。保存附件时保留原文件名映射，重名使用新序号，不覆盖；复制或导入后核实文件存在再声明成功。

session-index.csv 是可重建索引，session.md 为事实记录。每次真正保存练习后追加索引；按 session_id 查重，同一练习更新一行，修订注明时间，缺失字段留空。用 CSV 库处理引号，不用字符串拼接。量化只读真实条目，空索引不是零分。每行包括：
session_id,date,skill,test_type,material_ids,attempt_type,timed,duration_minutes,correct,total,band_low,band_high,score_source,assistance,evidence_status,record_path
skill=listening/reading/writing/speaking；attempt_type=first/repeat/revision/retest；timed=true/false/unknown；evidence_status=self-reported/inspected/partial/unavailable。分数与反馈细节留在 session.md。

示例路径（仅示意，需有文件才建立实际链接）：
- life-journal/YYYY-MM.md 到练习：../ielts/sessions/YYYY-MM/SESSION-ID/session.md
- session.md 到资料：../../../materials/M001/source.md
- 索引 record_path 以 ielts/ 为基准：sessions/YYYY-MM/SESSION-ID/session.md

复测创建新 session_id，记录原练习 ID。每周汇总链接回样本，不伪造未读取记录。需要长期交接时更新 profile.md 的当前目标与最近复盘链接，不把私人数据写回插件资源。

文档设计参考：通过 Context7 查询的 [Obsidian links](https://obsidian.md/help/links) 和 [attachments](https://obsidian.md/help/attachments)；仅用于 Markdown 与附件组织，不作为雅思评分依据。
