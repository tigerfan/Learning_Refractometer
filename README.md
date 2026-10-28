# 分析仪器笔记 · 十页可视化推导

> 从分子极化率到质谱扫描：十篇可交互的可视化推导，全部零依赖单文件。

## 🔗 在线访问

### **<https://tigerfan.github.io/Learning_Refractometer/>**

直接打开上面这个地址即可，无需安装任何东西。

| # | 页面 | 主题 | 直达链接 |
|---|---|---|---|
| 01 | 单一溶质液体的折射率测量 | 三维原理总览 | [principles.html](https://tigerfan.github.io/Learning_Refractometer/principles.html) |
| 02 | 蔗糖溶液 | 从 45 个原子推导，零拟合 | [sucrose.html](https://tigerfan.github.io/Learning_Refractometer/sucrose.html) |
| 03 | 盐水 | 当离子加和失效 | [saltwater.html](https://tigerfan.github.io/Learning_Refractometer/saltwater.html) |
| 04 | 糖盐水三元体系 | 一个读数，两个未知数 | [ternary.html](https://tigerfan.github.io/Learning_Refractometer/ternary.html) |
| 05 | 三色光 | 色散是另一条通道 | [dispersion.html](https://tigerfan.github.io/Learning_Refractometer/dispersion.html) |
| 06 | 便携折光计 | 光路设计与误差预算 | [optics.html](https://tigerfan.github.io/Learning_Refractometer/optics.html) |
| 07 | 多组分落地方案 | 三种加维度的路 | [solutions.html](https://tigerfan.github.io/Learning_Refractometer/solutions.html) |
| 08 | 色谱仪 | 混合物进去，成分表出来 | [chromatograph.html](https://tigerfan.github.io/Learning_Refractometer/chromatograph.html) |
| 09 | NIR 与拉曼 | 同一根化学键的两种问法 | [nir-raman.html](https://tigerfan.github.io/Learning_Refractometer/nir-raman.html) |
| 10 | 在线质谱 | 不用等它跑完 | [online-ms.html](https://tigerfan.github.io/Learning_Refractometer/online-ms.html) |

## 📖 PART I / II · 同一条折光链

前七页是一条完整的推导，七个环环相扣的环节：

```
分子极化率  →  摩尔折射度 R_m  →  混合规则  →  折射率 n
     →  临界角 θc  →  CCD 像素  →  糖度读数
```

| 环节 | 对应页面 | 关键数字 |
|---|---|---|
| 原子加和 → R_m | 02 蔗糖 | R_m = 70.345 cm³/mol，n = 1.5659 |
| 加和性失效 | 03 盐水 | 算得 0.0780，实测 0.1570，差 2.01 倍 |
| 多组分欠定 | 04 三元 | 两族等值线夹角 9.9° |
| 第二个信息通道 | 05 色散 | V 的区分能力是 n 的 57 倍 |
| 变成仪器 | 06 光路 | 全量程只对应 9.41° |
| 落地实施 | 07 方案 | 条件数 47.8（双波长）vs 7.3（密度） |

## 🔬 PART III · 另外三条分析路线

后三页跳出折射率，看同样的问题——「把混合物变成数字」——还能怎么解。

| 路线 | 靠什么分开 | 强项 | 死角 |
|---|---|---|---|
| **08 色谱**（分离科学） | 时间差（保留时间） | 异构体也能分，分离度最好 | 慢，分钟级；必须等 |
| **09 NIR / 拉曼**（分子光谱） | 能级差（振动模式） | 非破坏、有官能团指纹 | 谱带重叠，靠建模；稀水溶液难 |
| **10 在线质谱**（质量分析） | 质荷比（m/z） | 秒级 + 多组分 + ppb | 必须取样进真空；同质量分不开 |

三个关键数字，正好说明各自的尺度：

| 页面 | 数字 | 含义 |
|---|---|---|
| 08 色谱 | **11.46 μm** | 最优板高 H（2.29 d_p）；柱压算得 85 bar，对实测 83 bar |
| 09 NIR/拉曼 | **10⁻³⁰ cm²** | 拉曼散射截面，比荧光弱 14 个数量级 |
| 10 质谱 | **37.5 ms** | 全谱扫描；比色谱的 780 s 快 20800 倍 |

## 阅读路线

- **入门**：01 → 02 → 05
- **物理**：01 → 02 → 03 → 04 → 05
- **工程**：02 → 06 → 07
- **扩展**：01 → 08 → 09 → 10

## 🛠 技术说明

- **零外部依赖**：没有 CDN、没有框架、没有网络请求。下载后双击即可打开，断网可用。
- **图表全部现画**：Canvas 2D 与内联 SVG 逐帧绘制。光路按 Snell 定律逐条求交、折射、判全反射；四极杆离子轨迹按 Mathieu 稳定区求包络；色谱峰按 van Deemter 与高斯卷积。不是示意插图。
- **体积**：10 个页面合计约 1.9 MB（最大的是三维总览页 724 KB）。

## ⚠️ 可信度说明

页面里对模型边界做了明确标注，没有隐藏偏差：

| 级别 | 含义 | 出现在 |
|---|---|---|
| 零拟合 | 从文献原子折射度加和，实测只用于校验 | 02 蔗糖 |
| 一参数反标定 | 结构算不动，用一个常数统一全浓度数据 | 03 盐水 |
| 近似加和 | 两端锚定，中间区域靠插值，缺实测 | 04 三元密度 |
| 经验项 | 从实测反推，只能解释不能预测 | 05 的 λ₀、结构通道占比 |
| 文献典型值 | 系数取自文献，只有宏观量有实测锚定 | 08 的 van Deemter 三系数 |

具体差异举例：

- 纯蔗糖算得 **1.5659**，晶体文献值 **1.5376**，差 1.8%（各向异性 + 固体中 Lorentz 空腔失效）
- 盐水色散曲线是**模型推算**，没有实测验证
- 三元体系密度使用二元收缩加和，**中间区域无实测校验**
- 08 色谱的五个 k 值是为教学选的同系物，不是实测；柱压是唯一有实测对照的量
- 09 的拉曼散射截面只能当**数量级**用，具体分子差异可达 3 个量级
- 10 的软电离模型（降低电子能量）是**定性示意**，不是真实截面计算

## 本地运行

```bash
git clone https://github.com/tigerfan/Learning_Refractometer.git
cd Learning_Refractometer
# 直接双击 index.html，或起一个本地服务：
python -m http.server 8000
```

## 仓库结构

```
Learning_Refractometer/
├── index.html          系列索引（入口）
├── principles.html     01 三维原理总览
├── sucrose.html        02 蔗糖溶液
├── saltwater.html      03 盐水
├── ternary.html        04 三元体系
├── dispersion.html     05 三色光色散
├── optics.html         06 光路设计
├── solutions.html      07 多组分方案
├── chromatograph.html  08 色谱仪
├── nir-raman.html      09 NIR 与拉曼
├── online-ms.html      10 在线质谱
├── favicon.ico         站点图标
├── .nojekyll           跳过 Jekyll 处理
└── README.md
```

## 部署

GitHub Pages，源为 `main` 分支根目录。推送后 1–2 分钟自动构建。
