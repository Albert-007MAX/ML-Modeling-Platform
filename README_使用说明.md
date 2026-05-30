# 可解释性机器学习建模平台

发行版本：26.0530.22

面向地学单目标回归任务的可解释性机器学习建模平台。支持 11 个模型自动调优、SHAP 可解释性分析、SHAP-PDP 风格特征效应图，一键导出论文级图表与技术报告。

## 效果预览

### 1. 启动与授权

| 平台首页 | 首次授权页面 |
|---|---|
| ![平台首页](docs/images/platform_home.png) | ![授权页面](docs/images/platform_authorization.png) |

### 2. 建模结果与诊断

| 模型对比 | 预测散点图 |
|---|---|
| ![模型对比](docs/images/output_model_comparison.png) | ![预测散点图](docs/images/output_prediction_scatter.png) |

| 残差诊断 | 特征重要性 |
|---|---|
| ![残差诊断](docs/images/output_residual_plot.png) | ![特征重要性](docs/images/output_feature_importance.png) |

### 3. 可解释性输出

| SHAP Summary | Mean Absolute SHAP |
|---|---|
| ![SHAP Summary](docs/images/output_shap_summary.png) | ![SHAP Bar](docs/images/output_shap_bar.png) |

| GeoShapley Summary | GeoShapley 交互效应 |
|---|---|
| ![GeoShapley Summary](docs/images/output_geoshapley_summary.png) | ![GeoShapley Interactions](docs/images/output_geoshapley_interactions.png) |

### 4. SHAP-PDP 特征效应

![SHAP-PDP Grid](docs/images/output_shap_pdp_grid.png)

### 5. 2D SHAP-PDP 交互热力图

| x1 × x3 | x7 × x8 |
|---|---|
| ![2D SHAP-PDP x1 vs x3](docs/images/output_2d_shap_pdp_x1_x3.png) | ![2D SHAP-PDP x7 vs x8](docs/images/output_2d_shap_pdp_x7_x8.png) |

### 6. SHP 空间映射与主导因子

| GEO 空间效应 | x1 空间 SHAP |
|---|---|
| ![GEO 空间效应](docs/images/output_spatial_geo_effect.png) | ![x1 空间 SHAP](docs/images/output_spatial_x1_effect.png) |

| x7 空间 SHAP | 主导因子空间分布 |
|---|---|
| ![x7 空间 SHAP](docs/images/output_spatial_x7_effect.png) | ![主导因子空间分布](docs/images/output_spatial_dominant_factor.png) |

### 7. SHAP 聚类分析与空间映射

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
    G --> H["空间可视化<br/>SHP 映射、主导因子"]
    H --> I["SHAP 聚类<br/>聚类画像、空间映射"]
    I --> J["报告导出<br/>图表、记录、完整结果包"]
```

## 快速开始

1. 解压整个文件夹到任意位置，保持 `.python`、`.venv`、`assets`、`src` 等目录完整
2. 双击 **`双击启动_平台.bat`**
3. 浏览器自动打开 `http://localhost:8501`
4. 首次使用时，授权页面会显示本机机器码；将机器码发送至 `1778140731@qq.com`，获取授权码后粘贴激活
5. 关闭平台时，点击网页右上角 **关闭平台**，或双击 **`关闭平台.bat`**

**无需安装 Python，无需联网；首次使用需要授权码。** 当前便携包内置 Windows 64 位 Python 3.11 运行时；启动脚本会根据当前解压路径自动修复虚拟环境配置，因此移动目录或复制到其他 Windows 电脑后仍可直接双击启动。

## 授权激活

- 平台采用离线机器码授权，不需要联网验证。
- 首次打开平台时，授权页面会直接显示 **本机机器码**；用户只需要复制页面上显示的机器码。
- 机器码由当前电脑的系统信息、硬件标识、主机名等摘要生成，不上传服务器，也不需要联网。
- 将机器码发送至 `1778140731@qq.com`，邮件中建议写明使用人或单位名称、授权期限需求。
- 收到授权码后，粘贴到授权页面并点击 **激活并进入平台**。
- 激活成功后，授权信息会保存在 `.license\activation.lic`，同一台电脑后续启动无需重复输入。
- 授权码与机器码绑定；更换电脑、重装系统或硬件信息变化后，需要使用新机器码重新生成授权码。
- 平台激活后，侧边栏 **授权信息** 中仍可查看本机机器码和授权邮箱。

## 局域网共享

如果想让同一网络下的同事也能使用：

1. 启动平台后，记下本机 IP（命令行输入 `ipconfig` 查看）
2. 同事在浏览器访问 `http://你的IP:8501`
3. 如无法访问，需在 Windows 防火墙中放行 8501 端口

## 内置模型

| 类别 | 模型 |
|------|------|
| 集成学习 | Random Forest, XGBoost, LightGBM, CatBoost, Extra Trees, HistGradientBoosting, AdaBoost |
| 线性模型 | OLS |
| 其他 | SVR, KNN, Decision Tree |

可调模型均支持 Optuna 自动超参数调优（TPE + 训练集内部验证，小样本会自动降低验证折数）。

## 功能流程

1. **项目信息** — 填写项目名称与项目分类，便于后续查找
2. **数据导入** — 上传 Excel/CSV 或使用内置示例数据
3. **变量配置** — 选择目标列与特征列
4. **一键建模** — 自动预处理、调参、训练
5. **解释模型选择** — 训练完成后，从已训练模型中选择用于 SHAP / SHAP-PDP 的模型
6. **结果评估** — 模型排行榜、散点图、残差诊断
7. **SHAP 分析** — 蜂群图、特征重要性
8. **SHAP-PDP 分析** — 基于样本级 SHAP 值构建特征效应曲线，左上角仅显示 R2 和 p 值
9. **空间可视化** — 生成 SHP 空间映射和主导特征图
10. **SHAP 聚类** — 生成聚类画像、空间分布和样本表
11. **技术报告** — 自动生成 Markdown 报告，一键下载完整结果包
12. **历史记录** — 每次解释分析生成后自动保存项目记录、原始数据和完整结果包

## 系统要求

- Windows 10/11 64 位
- 建议内存 8 GB 以上
- 不需要安装 Python（已内置 `.python` 便携运行时）
- 不需要联网（依赖已内置在 `.venv`）

## 分析记录

- 历史记录保存在 `records` 目录，复制整个项目文件夹时会一起带走。
- 每条记录包含项目名称、项目分类、数据文件名、目标列、解释分析所选模型、核心指标、原始数据和完整结果包。
- 在网页顶部的 **历史分析记录** 中可以按项目名称、分类、数据文件或模型搜索，也可以按分类筛选。
- `.runtime` 是临时运行目录，可以自动清理；`records` 是长期记录目录，不会被启动脚本清理。

## 常见问题

**Q: 双击 bat 后闪退？**
A: 确认解压后的 `.python` 和 `.venv` 目录没有被删除；也可以在命令行中手动执行 `双击启动_平台.bat` 查看报错信息。一般不需要管理员权限。

**Q: 复制到另一台电脑后还能运行吗？**
A: 程序可以启动。请复制整个文件夹，不要只复制 `app.py` 或只复制启动脚本。启动脚本会自动按新路径修复 `.venv\pyvenv.cfg`。首次使用时需要按新电脑显示的机器码重新获取授权码。

**Q: 用户怎么知道自己的机器码？**
A: 首次打开平台时会先进入“软件授权”页面，页面上会直接显示 **本机机器码**。用户复制该机器码，发送至 `1778140731@qq.com`，收到回复的授权码后粘贴激活即可。激活后也可在侧边栏 **授权信息** 中查看本机机器码。

**Q: 机器码是怎么来的，会联网吗？**
A: 机器码由当前电脑的系统信息、硬件标识、主机名等信息在本机摘要生成，不需要联网，也不会自动上传。授权码与该机器码绑定。

**Q: 浏览器没有自动打开？**
A: 手动访问 `http://localhost:8501`

**Q: 怎么关闭平台？**
A: 最简单的方法是点击网页右上角“关闭平台”。也可以双击项目目录里的 `关闭平台.bat`。只关闭浏览器标签页不会停止后台服务。

**Q: 局域网其他人访问不了？**
A: 检查防火墙是否放行 8501 端口，确认双方在同一网络。

**Q: 想更新到新版本？**
A: 重新解压新版压缩包覆盖即可，`.runtime` 下的临时数据会自动清理。
