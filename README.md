# 守一工坊官网（单文件版）

一个 `index.html`，零依赖、零外部请求、无统计无 Cookie——官网本身践行三律。

## 本地预览

```bash
cd website
python -m http.server 8765
# 浏览器打开 http://127.0.0.1:8765
```

## 部署到 GitHub Pages（免费，5 分钟）

1. GitHub 新建仓库（公开），名字随意，如 `shouyi-site`。
2. 把 `index.html` 推上去：
   ```bash
   git init && git add index.html && git commit -m "init"
   git branch -M main
   git remote add origin https://github.com/<你的用户名>/shouyi-site.git
   git push -u origin main
   ```
3. 仓库 **Settings → Pages** → Source 选 `main` 分支 `/ (root)` → Save。
4. 约 1 分钟后可访问 `https://<用户名>.github.io/shouyi-site/`。

## 绑定自己的域名（域名定稿后）

1. 仓库根目录加一个 `CNAME` 文件，内容为你的域名（如 `shouyigongfang.cn`）。
2. 域名 DNS 添加解析（在华为云解析控制台）：
   - `CNAME` www → `<用户名>.github.io`
   - `A` @ → `185.199.108.153`（GitHub Pages 官方 IP，共 4 条可全加）
3. GitHub Pages 设置里填 Custom domain，勾选 **Enforce HTTPS**。

> 备选部署：Cloudflare Pages（免费额度更大）——导入同一仓库即可，DNS 改指向 Cloudflare。两条路零成本，任选。

## 需要你自己替换的占位符

| 位置 | 占位内容 | 替换时机 |
|---|---|---|
| 全文 | 守一工坊 / 守一 | 若最终定名利其器，全局搜索替换 |
| 页脚 + 邮箱链接 | `hi@shouyigongfang.cn` | 域名定稿后 |
| 页脚 | ICP 备案号（**已改为 HTML 注释隐藏**） | 完成网站 ICP 备案后取消注释填入真实号并链接 beian.miit.gov.cn；境外托管期间不得显示任何备案号 |
| 维护面板表格 | 订阅管家状态行 | 每次发版更新 |
| 应用区卡片 | 开发中状态 | 上架后改为「已上架」+ 商店链接 |

## 设计规范速记（改版时保持一致）

- 墨色底 + 朱砂印章 + 暖纸浅色双主题（默认暗色，右上角切换）
- 中文标题用楷体系（Kaiti SC / STKaiti / KaiTi），正文系统无衬线，技术元素等宽字体
- 强调色仅两种语义：朱砂红 = 品牌/警示（未申请），绿 = 验证通过
- 交互：滚动入场动画（IntersectionObserver），`prefers-reduced-motion` 时全部关闭
- 任何改版不得引入：外部字体、CDN 脚本、统计代码——这是三律的一部分
