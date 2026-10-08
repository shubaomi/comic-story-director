# Comic Story Director

在 Codex 内创作完整漫画的 Skill：原创、经典改编或续写，支持分阶段确认，也支持明确委托后一次性完成整部并自审。

可以说：“请一次性完成这部故事的创作和插画，沿已确认喜好，自审后只把最终结果交我审阅。”此时助手自行完成中间决策与质量门；也可以说“分阶段让我确认”或“只写文字，不出图”。详见[协作模式](references/collaboration-modes.md)。下文逐阶段确认说明仅适用于staged，最终用户审阅始终保留。

## 使用

在可以访问本目录的 Codex 聊天中输入：

> 请读取当前目录的 SKILL.md，使用漫画故事导演技能，先和我讨论一个原创故事。暂不生成图片。

如果已通过你的 Codex 技能安装方式将此目录作为 `comic-story-director` 安装，可使用：

> 请使用 $comic-story-director，和我打磨《丑小鸭》的续写。先确认原作版本与续写方向。

本次交付只创建当前目录内的包；未进行全局安装。直接读取 SKILL.md 可在当前聊天使用，不等于已注册到所有聊天的技能列表。安装时应只复制技能包，不包含个人 works/、照片和生成结果。

不需要项目后台或本包专用依赖。文字阶段不调用图像服务；绘图阶段需要所在 Codex 会话提供内置图像工具。优先使用该工具，不要求用户另交 API 密钥；可选的外部 API 路径不在本版实现中。

## 从想法到漫画

**W1创作定位 → W2故事定案 → W3完整剧本 → W4视觉方案 → W5设定图 → W6试画 → W7全篇制作 → W8验收交付。**

[标准流程](references/workflow.md) 定义每阶段的交付物、助手/用户分工、通过条件和返回修改的方式。作品的project-state记录当前进度，助手先做全量检查；用户默认看一张[简版审阅卡](assets/templates/decision-card.md)：含结局摘要、推荐意见、代表片段或实际图片，以及最多3项决定。全文保留供备查，不要求逐格阅读。

可以直接说“按我的取向代审”“给我当前进度”“只展示本轮需要决定的事”。对话用于作决定，版本和批准落在文件中；这是文档执行流程，尚无自动程序强制推进或拦截能力。代审不等于替用户批准，图像身份与效果仍需展示实际图片。

“确认制作这个 Skill”和“确认故事大纲”均不自动授权绘图。可以一次批准明确列出的多个已展示产物；无需背诵特定确认口令。

继续既有作品时：

> 读取 works/我的故事/project-state.md，核对有效批准和输出，从上次停下的位置继续。

修订时：

> 把第 2 页第二格对白改成“我想先坐一会儿”。列出受影响的版本和页面，保留旧图。

## 可选用途：经典启蒙

明确说“用途选择经典启蒙，创作类型选原创生活故事（或改编）”即可启用[专用参考](references/classic-introduction.md)。例如：“面向亲子共读，用一个原创生活故事解释我选的经典句段；先讨论版本和一个理解目标，不出图。”年级、识字能力、选文及长度按本作品确认。

用途与原创／改编／续写分别记录，共用W1–W8。普通原创、经典续写和没有新字段的旧作品保持原流程；不会因为读者是儿童就自动启用。新增的是来源、释义、目标到页格的追溯及适龄审阅，不承诺读懂整部经典或教学效果，也不包含销售运营功能。

## 文件组织

| 路径 | 用途 |
|---|---|
| [SKILL.md](SKILL.md) | 技能入口和阶段路由 |
| [DESIGN.md](DESIGN.md) | 本版已确认范围、边界和需求编号 |
| [references/workflow.md](references/workflow.md) | 八阶段流程、分工和简版审阅 |
| [references/approval-and-state.md](references/approval-and-state.md) | 批准、变更失效和恢复 |
| [references/story-development.md](references/story-development.md) | 原创与续写故事编辑 |
| [references/visual-generation.md](references/visual-generation.md) | 视觉方案、参考图、工具与生成流程 |
| [references/quality-review.md](references/quality-review.md) | 故事与图像验收 |
| [assets/templates/project-state.md](assets/templates/project-state.md) | 按需复制的作品模板索引 |
| [examples/original-short.md](examples/original-short.md) | 4 页 12 格原创文字示例 |
| [examples/sequel-short.md](examples/sequel-short.md) | 4 页 12 格续写方向示例，原作核对待办明确保留 |
| [validation/scenarios.md](validation/scenarios.md) | 不出图的情境检查 |
| [validation/report.md](validation/report.md) | 实际执行过的验证与局限 |

作品建议保存在 `works/<作品名>/`，文档使用相对路径引用各自作品内的文件；向用户提供文件链接时解析为当前环境的绝对路径。每部作品分别保存批准记录、参考图、页图和问题清单。

可在技能根目录的 `.local/editor-profile.md` 保存个人主编创作取向；Skill 在新建和继续作品时读取，作品简报记录引用版本。档案应区分用户自述、来源资料和编辑推导，并写成可落实到剧情的取舍。`.local/` 已被 Git 忽略；安装、复制或分享技能包时也应排除它，Git 忽略规则不会自动替手工复制脱敏。复制到另一处的技能包不会自动取得原来的私人档案，也不等于所有聊天已全局加载该取向。

## 能力与发布状态

本版交付文档流程、模板和示例，不含生成后端、自动工具拦截、中文排版引擎或 PDF/CBZ 导出器。页内文字默认随图生成并逐字检查；错误可通过内置图像编辑修复，超出约定修复额度则暂停商议，不用错图冒充成品。

角色一致性依靠批准设定、实际参考输入、试画和审核；无法承诺无限篇幅或百分之百无漂移。温柔叙事与情绪支持是创作目标，不声称临床疗效。

本包尚未进行真实绘图和用户视觉验收。示例不是已获批准的作品，也不是历史聊天附件的恢复副本。

仓库地址：[shubaomi/comic-story-director](https://github.com/shubaomi/comic-story-director)。作品、照片与生成结果通过 `.gitignore` 排除，仓库仅保存技能包及其文字示例。

目标是可复用的开源 Skill 包，但许可证与署名尚待所有者选择；目前不宣称已授予开源许可，不复制第三方项目代码。首次 Git 提交不等于发布 Release、全局安装或作品发布。对外授予开源许可前需补齐许可证，并分别核对选用素材的来源。
