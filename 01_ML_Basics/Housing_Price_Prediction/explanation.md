# Model Explanation – California Housing Price Prediction
This document summarizes the interpretability analysis for the **Random Forest Regression model** trained on the California Housing dataset.  
The goal is to understand **which features most strongly affect house prices**, and **how** they influence the model’s predictions.

---

# 1. Feature Importance (Random Forest)
Random Forest provides an impurity-based feature importance score.  
The top feature is:

- **MedInc（Median Income，中位数收入）**

This matches domain knowledge：**收入越高的区域，房价越高。**

Other features such as `HouseAge`、`AveRooms` 贡献度明显较低。

---

# 2. Partial Dependence Plot (PDP)
PDP 显示某个特征的整体趋势，即“该特征上升时，模型的平均预测如何变化”。

本项目绘制了：**PDP – MedInc**

### Interpretation
- PDP 曲线随 **MedInc 增加而明显上升**。
- 表明收入对房价呈 **强正相关**。
- 曲线光滑、单调，没有显著的拐点 → **模型对该特征的学习方式稳定一致**。

直观理解：
> 如果把所有样本的 MedInc 都提高 1 单位，模型预测的房价平均会上升。

---

# 3. Individual Conditional Expectation (ICE)
ICE 比 PDP 更细致，它为 **每一个样本单独画一条曲线**。

### Interpretation
- 大多数样本的 ICE 曲线与 PDP 趋势方向一致。
- 几乎所有样本在 MedInc 增长时，房价预测也上升。
- 无显著反向或曲折线，表明：
  - **模型在不同样本中对 MedInc 的影响方向一致**  
  - 没有强烈的样本异质性（heterogeneity）

ICE 结合 PDP 的结论非常稳定。

---

# 4. SHAP Values（Shapley Additive Explanations）
SHAP 能解释 **每个特征对每个样本的贡献**，是目前最主流的解释方法。

我们绘制了 SHAP summary plot。

### Interpretation
- **MedInc 的 SHAP 值呈最大范围** → 最重要特征
- 红点（高收入）在右侧 → 提高预测  
- 蓝点（低收入）在左侧 → 拉低预测  
- `HouseAge`、`AveRooms` 的 SHAP 分布窄且集中 → 影响较弱

**关键认识：**
- SHAP 显示了“每个特征在每一个预测里到底贡献了多少”
- 与特征重要性（整体）、PDP（平均效应）、ICE（样本行为）形成互补

---

# 5. Summary of All Interpretability Findings

### **结论 1：MedInc 是绝对核心特征**
模型、PDP、ICE、SHAP 均一致证明：

> 中位收入是影响房价的决定性因素。

这是极为稳定且可信的结果。

---

### **结论 2：部分其他特征影响弱**
`HouseAge`、`AveRooms` 等特征对预测影响有限。  
从 SHAP 和 Feature Importance 都能看出这一点。

---

### **结论 3：模型行为稳定且没有过拟合迹象**
- PDP 平滑
- ICE 曲线方向一致
- SHAP 分布有序

说明模型学到的是合理的经济规律，而不是噪声。

---

# 6. Future Work
后续模型解释可以进一步扩展：

- 计算 SHAP dependence plot（更细的双变量关系）
- 研究特征交互（SHAP interaction values）
- 尝试 LIME 用于单样本解释
- 使用更复杂模型（XGBoost / LightGBM）对比解释结果

---

# 7. Figures
所有图存储在：

v
explanation/
pdp_medinc.png
ice_medinc.png
shap_summary.png

