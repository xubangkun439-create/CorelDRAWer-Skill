# 地层柱状图绘制练习 — Nature 风格

基于 Nature 系列期刊论文数据，使用 `--style nature` 生成的练习图件。

## 练习成果

| 文件 | 主题 | 数据来源 | 图件类型 |
|:-----|:-----|:---------|:---------|
| `practice_ediacaran_cambrian.svg` | 埃迪卡拉-寒武纪界线 | 秭归地区 + 参考 Nature 论文 | 柱状图 + δ¹³C 曲线 |
| `practice_ptb.svg` | 二叠纪-三叠纪界线 (Meishan GSSP) | 参考 s41561-020-00646-4 | 柱状图 + δ¹³C 曲线 |
| `practice_oae2.svg` | 白垩纪 OAE 2 | 参考 s43247-024-01214-z | 柱状图 + δ¹³C 曲线 |
| `practice_snowball_earth.svg` | 雪球地球 (Cryogenian) | 参考 Adelaide 数据 | 柱状图 + δ¹³C |
| `practice_toarcian_oae.svg` | 侏罗纪 Toarcian OAE | 参考 s41561-022-01115-w | 柱状图 + δ¹³C + δ¹¹B |
| `practice_phanerozoic.svg` | 显生宙综合柱状图 | 14 个主要事件综合 | 柱状图 |

## 练习覆盖的地质时期

```
显生宙综合 ───────────────────────────────────── practice_phanerozoic.svg
├── 寒武纪  ← 埃迪卡拉-寒武纪 ───────────────── practice_ediacaran_cambrian.svg
├── 奥陶-志留-泥盆
├── 石炭-二叠  ← 二叠纪-三叠纪 ──────────────── practice_ptb.svg
├── 三叠-侏罗  ← Toarcian OAE ──────────────── practice_toarcian_oae.svg
├── 白垩纪    ← 白垩纪 OAE2 ────────────────── practice_oae2.svg
└── 古近-新近-第四纪
雪球地球 (前寒武) ────────────────────────────── practice_snowball_earth.svg
埃迪卡拉剖面 ────────────────────────────────── practice_xsection.svg
```

## 使用方法

```bash
# 柱状图 (Nature 风格)
python3 generate_column.py ediacaran_cambrian_practice.json output.svg --style nature

# 剖面图 (Nature 风格)
python3 generate_cross_section.py adelaide_xsection.json output.svg --style nature
```

## 学习成果

- 熟悉了 Nature 风格的 Arial 字体、细线系统、柔和配色
- 掌握了 δ¹³C 曲线通道的配置方法
- 验证了化石/构造列的自动显隐功能
- 确认了跨期刊风格的一致性（Comms Earth & Env ≈ Nature Comms）
