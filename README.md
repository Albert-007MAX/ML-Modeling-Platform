# ML建模平台

可解释性机器学习建模平台，面向地学单目标回归任务，支持自动建模、SHAP 可解释性分析、GeoShapley 空间解释、SHAP-PDP 特征效应图和技术报告导出。

## 当前发行版

- 版本：`26.0529.15`
- 发布日期：`2026-05-29`
- 下载文件：`ML-Modeling-Platform_26.0529.15.zip`
- 解压后目录：`ML建模平台`
- 适用系统：Windows 10 / 11 64 位
- 授权邮箱：`1778140731@qq.com`

## 效果图

### 启动与授权

| 平台首页 | 首次授权页面 |
|---|---|
| ![平台首页](docs/images/platform_home.png) | ![授权页面](docs/images/platform_authorization.png) |

### 建模结果与诊断

| 模型对比 | 预测散点图 |
|---|---|
| ![模型对比](docs/images/output_model_comparison.png) | ![预测散点图](docs/images/output_prediction_scatter.png) |

| 残差诊断 | 特征重要性 |
|---|---|
| ![残差诊断](docs/images/output_residual_plot.png) | ![特征重要性](docs/images/output_feature_importance.png) |

### 可解释性输出

| SHAP Summary | Mean Absolute SHAP |
|---|---|
| ![SHAP Summary](docs/images/output_shap_summary.png) | ![SHAP Bar](docs/images/output_shap_bar.png) |

| GeoShapley Summary | GeoShapley 交互效应 |
|---|---|
| ![GeoShapley Summary](docs/images/output_geoshapley_summary.png) | ![GeoShapley Interactions](docs/images/output_geoshapley_interactions.png) |

### SHAP-PDP 特征效应

![SHAP-PDP Grid](docs/images/output_shap_pdp_grid.png)

### 2D SHAP-PDP 交互热力图

| x1 × x3 | x7 × x8 |
|---|---|
| ![2D SHAP-PDP x1 vs x3](docs/images/output_2d_shap_pdp_x1_x3.png) | ![2D SHAP-PDP x7 vs x8](docs/images/output_2d_shap_pdp_x7_x8.png) |

### SHP 空间映射与主导因子

| GEO 空间效应 | x1 空间 SHAP |
|---|---|
| ![GEO 空间效应](docs/images/output_spatial_geo_effect.png) | ![x1 空间 SHAP](docs/images/output_spatial_x1_effect.png) |

| x7 空间 SHAP | 主导因子空间分布 |
|---|---|
| ![x7 空间 SHAP](docs/images/output_spatial_x7_effect.png) | ![主导因子空间分布](docs/images/output_spatial_dominant_factor.png) |

### SHAP 聚类分析与空间映射

| 聚类特征画像 | 聚类空间分布 |
|---|---|
| ![聚类雷达图](docs/images/output_cluster_radar.png) | ![聚类空间分布](docs/images/output_cluster_map.png) |

## 设计逻辑

```mermaid
flowchart LR
    A["授权激活<br/>复制机器码并发送邮箱"] --> B["数据导入<br/>Excel / CSV / 内置示例"]
    B --> C["变量配置<br/>目标列、特征列、空间坐标"]
    C --> D["一键建模<br/>预处理、调参、训练"]
    D --> E["模型评估<br/>Train / Test 指标、散点、残差"]
    E --> F["可解释性分析<br/>SHAP / GeoShapley"]
    F --> G["SHAP-PDP<br/>特征效应曲线"]
    G --> H["空间可视化与报告<br/>图表、记录、完整结果包"]
```

## 下载与使用

1. 打开 [v26.0529.15 Release](https://github.com/Albert-007MAX/ML-Modeling-Platform/releases/tag/v26.0529.15)。
2. 下载 `ML-Modeling-Platform_26.0529.15.zip`。
3. 解压完整 `ML建模平台` 文件夹。
4. 双击 `双击启动_平台.bat`。
5. 首次打开时，授权页面会显示本机机器码。
6. 将机器码发送至 `1778140731@qq.com`，收到授权码后粘贴激活。

## 授权说明

- 平台采用离线机器码授权，不需要联网验证。
- 用户首次打开平台时，会先看到“软件授权”页面，页面上直接显示本机机器码。
- 机器码由当前电脑的系统信息、硬件标识、主机名等信息在本机摘要生成，不会自动上传。
- 授权码与机器码绑定，同一台电脑激活后会自动保存。
- 授权文件保存在 `.license\activation.lic`。
- 更换电脑、重装系统或关键硬件变化后，需要重新生成授权码。
- 授权码生成器仅保留在发行人本地，不包含在公开发行包中。

## 发行说明

完整更新内容见 [`RELEASE_NOTES_26.0529.15.md`](RELEASE_NOTES_26.0529.15.md)。
