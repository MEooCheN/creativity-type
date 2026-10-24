# 创造力剖面（creativity-type）

**这是什么**：一个可以放在微信里传播的小网页，22 道题输出"你的创造力是哪种形状"，8 个主型 + 2 个彩蛋。纯静态、无后端、无依赖、不采集数据。
**怎么跑**：双击 `index.html` 就能用（手机也直接打开文件即可，`file://` 下功能完整）。
**现在到哪一步**：v0.1 已上线 → 8 型 / 22 题 / 雷达 / 结果卡 / 复制文案全部跑通，用无头浏览器逐屏验过版式；文案是草稿，等你改名换词。

线上地址：**https://meoochen.github.io/creativity-type/**

## 文件

```
index.html              全部代码（HTML/CSS/JS 内联，单文件，零依赖）
docs/type-system.md     8+2 个型：代号、名字、判词、天赋、盲点、姿势，每条带"决定了什么"
docs/question-bank.md   22 道题：测哪个维度、为什么这么问、选项映射
docs/screenshots/       封面 / 答题页 / 结果页 / 分享卡（无头浏览器实拍）
```

## 改文案怎么改

`index.html` 里搜 `const TYPES` → 8 个主型 + `__COPY` / `__SELF` 两个彩蛋，改 `name`、`verdict`、`gift`、`blind`、`pose` 即可。
改题搜 `const Q` → 每题 `{axis, w, t, o:[{t,p}]}`，`axis` 决定计入哪个维度，`p` 是极点字母（F/P/N/R/W/B/I/C）。

改完刷新即可，不需要任何构建步骤。

## 部署

目标：GitHub Pages（公开仓库，免费、无需备案）
1. `git init && git add -A && git commit -m "v0.1"`
2. `gh repo create creativity-type --public --source=. --push`
3. `gh api -X POST repos/:owner/creativity-type/pages -f source.branch=main -f source.path=/`

线上地址：**https://meoochen.github.io/creativity-type/**

> 注意：本机 `github.com:443` 被网络层拦（`git push` 连不上，`api.github.com` 正常），所以首次推送是走 GitHub API 建的提交（`blobs → tree → commit → ref`）。换机器或挂代理后再 `git push` 即可正常同步；本地提交和远端提交内容一致、SHA 不同。

## 待办

- [ ] 8 个名字定稿（当前是我起的草稿）
- [ ] 判词调性定稿（冷幽默 / 温柔 / 阴阳，见 `docs/type-system.md` 的"调性旋钮"）
- [x] 部署到 GitHub Pages，拿到线上地址
- [ ] 微信内实测：iOS / 安卓各一台，检查长按保存结果卡
- [ ] 域名（可选）：微信内打开需要备案域名，先用 Pages 裸链测试

## 边界

娱乐性自评，不是心理测量工具。页面内已有声明，不要删。不做"分享解锁结果"——微信明令禁止诱导分享，那是封号点。
