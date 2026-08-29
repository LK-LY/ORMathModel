# ORMathModel

Operations Research Mathematical Modeling Agent - 运筹学数学建模智能体

## 项目简介

基于Claude AI的数学建模竞赛辅助系统，集成运筹学知识库和完整建模工作流，适用于CUMCM、MCM/ICM等数学建模竞赛。

## 核心特性

- **智能化工作流**: 6阶段建模流程（数据探索→分析建模→代码实现→论文撰写→结果验证→质量审查）
- **运筹学知识库**: 17种经典方法（线性规划、整数规划、动态规划、图算法、遗传算法等）
- **方法快速检索**: 根据问题类型自动推荐合适的运筹学方法
- **LaTeX论文生成**: 自动生成符合CUMCM格式的完整论文
- **代码实现**: Python数值计算和优化算法实现

## 目录结构

```
MathModelAgent/
├── skills/                          # 建模技能库
│   ├── 1data-explore/              # 数据探索与清洗
│   ├── 2analysis-modeling/         # 分析与建模设计
│   ├── 3code-implement/            # 代码实现
│   ├── 4paper-write/               # 论文撰写
│   ├── 5result-verify/             # 结果验证
│   ├── 6verity/                    # 质量审查
│   └── _references/                # 参考知识库
│       ├── math_modeling_norms.md  # 数学建模规范
│       └── operations_research_methods.md  # 运筹学方法库
└── 运筹学specialist/                # 运筹学专家资料
    ├── 运筹优化算法知识提纯.txt     # 知识提炼（591行）
    └── [30个PDF讲义章节]

```

## 运筹学方法覆盖

### 数学规划类
- 线性规划（LP）- 运输配送、资源分配
- 整数规划（IP/MILP）- 设施选址、项目选择
- 非线性规划（NLP）- 价格优化、参数标定
- 目标规划 - 多目标权衡

### 网络与动态决策
- 图与网络优化 - 最短路、最大流、匈牙利算法
- 动态规划（DP）- 背包、设备更新、多阶段决策
- 排队论 - 服务系统设计
- 库存论 - EOQ模型、报童模型

### 智能优化
- 遗传算法（GA）
- 模拟退火（SA）
- 蚁群算法（ACO）

### 统计与预测
- 回归分析
- 时间序列（ARIMA）
- 神经网络
- 灰色系统（GM）

### 决策评价
- 层次分析法（AHP）
- 模糊综合评价

## 快速开始

### 1. 安装Skills

```bash
# 安装所有建模skills到本地
npx skills add ./MathModelAgent/skills/1data-explore
npx skills add ./MathModelAgent/skills/2analysis-modeling
npx skills add ./MathModelAgent/skills/3code-implement
npx skills add ./MathModelAgent/skills/4paper-write
npx skills add ./MathModelAgent/skills/5result-verify
npx skills add ./MathModelAgent/skills/6verity

# 安装参考知识库
cp -r ./MathModelAgent/skills/_references ~/.claude/skills/
```

### 2. 使用工作流

在Claude Code中调用skills：

```bash
# 第一阶段：数据探索
/1data-explore

# 第二阶段：分析建模（会自动引用运筹学知识库）
/2analysis-modeling

# 第三阶段：代码实现
/3code-implement

# 第四阶段：论文撰写
/4paper-write

# 第五阶段：结果验证
/5result-verify

# 第六阶段：质量审查
/6verity
```

### 3. 运筹学方法选择

在建模阶段，系统会根据问题类型自动推荐方法：

| 问题类型 | 推荐方法 |
|---------|---------|
| 运输配送、资源分配 | 线性规划、网络流 |
| 设施选址、项目选择 | 整数规划 |
| 定价与补货 | 非线性规划、动态规划 |
| 路径规划、车辆调度 | 图算法、遗传算法 |
| 排班排程 | 整数规划、约束规划 |
| 库存管理 | 存贮论、动态规划 |
| 需求预测 | 回归、时间序列、神经网络 |
| 方案评价 | AHP、模糊评价 |

## 使用示例

### 案例：2023 CUMCM Problem C - 蔬菜定价与补货

**问题类型**: 定价优化 + 库存管理

**推荐方法**: 
- 价格弹性分析（回归分析）
- 联合优化（非线性规划 - SLSQP算法）
- 多产品多周期决策（动态规划思想）

**实现效果**:
- 问题1: R²=0.45, 价格弹性系数-0.8到-1.5
- 问题2: 7天利润¥8,624.77（+13.1%），定价-3.8%，补货+12.5%
- 问题3: 27产品组合，利润¥312.45，空间利用率98.7%

## 技术栈

- **AI**: Claude Opus 5（推理与代码生成）
- **编程**: Python 3.x（NumPy, Pandas, SciPy, Matplotlib）
- **优化器**: scipy.optimize（SLSQP, minimize）
- **文档**: LaTeX（ctex, CUMCM模板）
- **流程管理**: Claude Skills架构

## 参考资料

- 运筹学specialist目录包含30章PDF讲义
- 知识提纯文件涵盖34种方法分类
- 2004-2025 CUMCM优秀论文方法映射

## 团队协作

本项目设计用于团队协作：

1. **Founder**: 维护skills库和运筹学知识库
2. **队友**: 克隆仓库后安装skills到本地Claude Code
3. **共享**: 统一的建模规范和方法选择标准

## 许可

本项目仅供学习和数学建模竞赛使用。

## 联系方式

- GitHub: [LK-LY/ORMathModel](https://github.com/LK-LY/ORMathModel)
