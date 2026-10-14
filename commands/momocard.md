---
name: momocard
description: 生成符合墨墨记忆卡（Markji）官方语法的背诵卡片，挖空聚焦重点难点易错点
argument-hint: [知识点、笔记或文件路径]
---

读取并严格遵循技能 ${CLAUDE_PLUGIN_ROOT}/skills/momocard/SKILL.md 中的完整制卡流程；语法依据 ${CLAUDE_PLUGIN_ROOT}/skills/momocard/references/markji-syntax.md，挖空与美化策略依据 ${CLAUDE_PLUGIN_ROOT}/skills/momocard/references/card-design.md。

为以下内容生成墨墨记忆卡：

$ARGUMENTS

若 $ARGUMENTS 为空，先向用户询问要制卡的知识点、笔记内容或文件路径，再按流程生成。
