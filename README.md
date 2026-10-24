# AI4Health-Agent

**医疗 AI 每日简报（个人定制版）** · 网站：**https://siyuanyan1.github.io/AI4Health-Agent/**

每天北京时间 07:30 自动抓取约 40 个信源（Nature 系与高影响力期刊 RSS、arXiv / medRxiv / PubMed、Hugging Face、Google / DeepMind / Microsoft 等实验室博客、FDA / EMA 等监管机构），由 LLM（`anthropic/claude-sonnet-5.5`，经 OpenRouter）生成中文摘要、分类与重要性评分，构建静态网站发布到 GitHub Pages。另有顶会论文库（`/papers/`，CVPR / ICCV / NeurIPS / ICML / ICLR / ACL / AAAI / MICCAI / ISBI / MIDL / CHIL / ML4H）、每周汇总和 RSS 输出。

内容由程序自动生成，仅供科研参考，不构成医疗建议；预印本未经同行评审。

## 覆盖方向

影像与病理 · 大模型与智能体 · 临床预测与决策 · 生命科学与药物 · 数字健康 · 落地与监管；每个方向内可按形式筛选（研究论文 / 综述与观点 / 开源模型与代码 / 新闻与监管）。

## 相对上游的定制

按个人研究方向（医学影像与医学基础模型）做了小幅修改：

- **信源**：新增 Nature 正刊、Nature Communications、Nature Biotechnology、Nature Cancer、npj Precision Oncology；扩展 arXiv 检索（病理 / 皮肤 / 眼科 / scientific & drug discovery）；移除融资并购与行业新闻类信源及「产业动态」板块。
- **评分**：`prompts/score_rubric.md` 增加读者偏好——医学基础模型（longitudinal、patient-level）、多模态 LLM、影像专科、领域专用 LM、world model in medical、AI for scientific discovery、human-AI collaboration 等加分；产业宣传减分。
- **权重**：Nature 家族信源上调，新闻监管类下调。

## 运行

GitHub Actions 全自动（`.github/workflows/update.yml`）。需配置 Secrets：`LLM_API_KEY`、`LLM_BASE_URL`；变量 `LLM_MODEL`；可选 `SPRINGER_API_KEY`、`NCBI_API_KEY`。本地构建：`pip install feedparser && python hub.py build`。实现细节、评分评测流程见[上游 README](https://github.com/ChunXiaostudy/AI4Health-Hub#readme)。

## Attribution

本仓库 **heavily based on [ChunXiaostudy/AI4Health-Hub](https://github.com/ChunXiaostudy/AI4Health-Hub)**（直接 fork，核心代码与架构均来自该项目，MIT 许可），仅按个人阅读偏好做了信源与评分定制。上游项目的思路参考了 [wuyoscar/AISafetyHot-Hub](https://github.com/wuyoscar/AISafetyHot-Hub)（内容 CC BY-NC 4.0）与 [KKKKhazix/AIHOT](https://github.com/KKKKhazix/AIHOT)（MIT），一并致谢。

所有条目内容版权归原始来源（期刊、预印本平台、媒体等）所有；本仓库代码以 MIT 许可发布。
