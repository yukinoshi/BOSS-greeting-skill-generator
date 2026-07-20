# AI Job Greeting Skills

一套用于 BOSS直聘等招聘平台的 AI 打招呼生成工具链，基于 QoderWork Skill 体系构建。

## 工作流程

```
简历/自我描述 → [resume-profile-extractor] → 结构化候选人画像
                                                    ↓
候选人画像   → [greeting-skill-generator] → 个性化打招呼 Skill
                                                    ↓
招聘 JD      → [ai-job-greeting]           → 高回复率打招呼话术
```

## Skills

### resume-profile-extractor

从简历文件（PDF/DOCX/纯文本）或口述描述中提取结构化候选人画像。

输出内容包括：目标岗位方向、核心标签（3~7 个差异化卖点）、技术栈分类、项目经历摘要、差异化优势、硬性约束。

画像默认保存为 `candidate-profile.md`，用户可手动修改后再生成下游 skill。

### greeting-skill-generator

根据结构化候选人画像，生成个性化的打招呼 skill 并写入本地技能目录。

支持自定义 skill 名称（默认 `ai-job-greeting`）。生成的 skill 包含完整的 JD 分析策略、打招呼结构、优先级规则和硬性约束。

### ai-job-greeting（生成产物）

最终使用的打招呼 skill。接收一份 JD，先分析企业真实招聘意图和痛点，再生成 100~170 字的个性化打招呼话术。

核心策略：痛点优先于技术栈、首句决定点击率、每份 JD 都像重新写的一样。

## 安装方式

将 skill 目录复制到任意ai的skill文件夹下即可：

```bash
cp -r skills/resume-profile-extractor ~/.qoderworkcn/skills/
cp -r skills/greeting-skill-generator ~/.qoderworkcn/skills/
```

或在 QoderWork 中通过 skill_manage 工具安装。

## 使用示例

1. 对 QoderWork 说："帮我提取简历画像"，附上简历文件或描述背景
2. 检查生成的 `candidate-profile.md`，按需修改
3. 对 QoderWork 说："用我的画像生成打招呼 skill"
4. 发送任意 JD，即可获得针对性的打招呼话术
