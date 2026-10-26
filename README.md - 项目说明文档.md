# 黄瓜温室环境时序监测与智能问答系统

基于 Python + Streamlit 搭建的智慧农业温室环境数据分析平台，支持多源CSV时序数据上传、多表JOIN关联、可视化展示、随机森林预测与自然语言智能问答。

## 技术栈

- **后端框架**：Python 3.9+ / Streamlit
- **数据处理**：Pandas / NumPy
- **可视化**：Plotly
- **机器学习**：Scikit-learn（随机森林回归）

## 项目功能

1. **多源数据上传与关联**
   - 支持上传温室气候（Greenhouse_climate）、灌溉（Irrigation）、产量（Production）、资源能耗（ResourceCalculations）4类CSV数据
   - 基于时间戳 GHtime 实现多表 Inner Join，整合为统一数据集
   - 自动清洗空值与异常时间戳

2. **时序可视化**
   - 温室温度 Tair 时序曲线
   - 灌溉水量 water 时序曲线
   - Plotly 交互式图表，支持缩放、悬浮查看数值

3. **机器学习预测**
   - 随机森林回归模型，以湿度 HumDef、CO₂浓度 CO2air 为特征预测温室温度 Tair
   - 输出 MAE（平均绝对误差）、MSE（均方误差）、R²（决定系数）三项评估指标

4. **智能问答模块**
   - 基于多表合并后的完整数据集，支持自然语言关键词解析查询
   - 支持查询：温度/灌溉水量/产量/CO₂/湿度的最大值、最小值、平均值
   - 支持计算灌溉水量与温度的相关性系数

5. **异常告警（扩展）**
   - 可设置高温阈值，自动识别超标数据并高亮展示

## 项目结构

```
├── app.py                          # 主程序入口
├── Greenhouse_climate.csv          # 温室气候数据（示例）
├── Irrigation.csv                 # 灌溉数据（示例）
├── Production.csv                 # 产量数据（示例）
├── ResourceCalculations.csv        # 资源能耗数据（示例）
├── requirements.txt                # 依赖清单
└── README.md                       # 项目说明
```

## 快速启动

### 1. 安装依赖

```bash
pip install -r requirements.txt
```

### 2. 运行项目

```bash
streamlit run app.py
```

浏览器自动打开 http://localhost:8501 即可访问。

### 3. 使用方式

1. 依次上传4份CSV文件（Greenhouse_climate.csv 为必需）
2. 系统自动完成多表关联、数据清洗与可视化
3. 在智能问答输入框中输入问题，如"平均温度是多少"、"灌溉和温度相关性"

## 数据集说明

| 文件名 | 说明 | 关键字段 |
|--------|------|----------|
| Greenhouse_climate.csv | 温室环境气候监测数据 | GHtime, Tair, HumDef, CO2air |
| Irrigation.csv | 灌溉用水量记录 | GHtime, water |
| Production.csv | 作物产量记录 | GHtime, yield |
| ResourceCalculations.csv | 资源能耗统计 | GHtime, Elec, Gas |

## 模型评估指标说明

- **MAE（Mean Absolute Error）**：平均绝对误差，值越小预测越准
- **MSE（Mean Squared Error）**：均方误差，对大误差惩罚更重
- **R²（R-Squared）**：决定系数，越接近1拟合效果越好

## 适用场景

- 智慧农业温室环境监测演示
- 计算机专业课程设计 / 毕业设计
- 数据分析、机器学习项目实践
- 软件测试岗项目经验展示

## 作者

吉林农业大学 计算机科学与技术专业
