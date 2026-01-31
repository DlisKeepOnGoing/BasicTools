---

# 🐍 Conda 完整使用教程

Conda 是一个开源的 **包管理 + 环境管理** 工具，广泛用于 Python、数据科学、机器学习和科研开发环境管理。

它最大的优势：**环境隔离 + 依赖自动解决**。

---

## 📌 一、Conda 是什么？

Conda 可以帮你解决两个核心问题：

| 功能      | 作用                            |
| ------- | ----------------------------- |
| 📦 包管理  | 安装、升级、删除 Python 包（不仅限 Python） |
| 🧪 环境管理 | 为不同项目创建独立的运行环境，互不干扰           |

例如：

* 项目 A 用 Python 3.8 + TensorFlow 2.3
* 项目 B 用 Python 3.11 + PyTorch 2.x
  👉 用 Conda 可以完美隔离

---

## 💾 二、安装 Conda

推荐安装 **Miniconda**（轻量版）：

### 1️⃣ 下载地址

[https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)

### 2️⃣ 安装后验证

```bash
conda --version
```

如果输出版本号，例如：

```bash
conda 24.1.2
```

说明安装成功 ✅

---

## 🧱 三、环境管理（最重要的功能）

### 📍 1. 创建环境

```bash
conda create -n myenv python=3.10
```

| 参数            | 说明           |
| ------------- | ------------ |
| `-n`          | 环境名称         |
| `python=3.10` | 指定 Python 版本 |

---

### ▶️ 2. 激活环境

```bash
conda activate myenv
```

激活后，终端前面会出现：

```bash
(myenv) $
```

---

### ⛔ 3. 退出环境

```bash
conda deactivate
```

---

### 📃 4. 查看已有环境

```bash
conda env list
```

或

```bash
conda info --envs
```

---

### ❌ 5. 删除环境

```bash
conda remove -n myenv --all
```

---

## 📦 四、包管理

### 📥 1. 安装包

```bash
conda install numpy
```

指定版本：

```bash
conda install numpy=1.24
```

---

### 📤 2. 卸载包

```bash
conda remove numpy
```

---

### 🔄 3. 更新包

```bash
conda update numpy
```

更新 conda 自身：

```bash
conda update conda
```

---

### 🔍 4. 搜索包

```bash
conda search pandas
```

---

## 🌍 五、使用 Conda 仓库（channels）

Conda 从不同的“软件源”下载包，常用的有：

| Channel     | 说明           |
| ----------- | ------------ |
| defaults    | 官方源          |
| conda-forge | 社区维护，包更多更新更快 |

### 添加 conda-forge

```bash
conda config --add channels conda-forge
conda config --set channel_priority strict
```

---

## 📁 六、环境导出与共享（非常实用）

### 📤 导出当前环境

```bash
conda env export > environment.yml
```

生成的文件可以分享给别人。

---

### 📥 根据文件创建环境

```bash
conda env create -f environment.yml
```

---

## 🚀 七、一次性创建带依赖的环境

```bash
conda create -n dataenv python=3.10 numpy pandas matplotlib scikit-learn
```

---

## 🧠 八、Conda vs Pip

| 对比         | Conda   | Pip             |
| ---------- | ------- | --------------- |
| 环境管理       | ✅ 支持    | ❌ 需要 virtualenv |
| 依赖解决能力     | 强       | 一般              |
| 非 Python 包 | ✅ 支持    | ❌ 不支持           |
| 适合场景       | 数据科学、AI | 纯 Python 项目     |

📌 实战建议：

> **Conda 管环境 + Pip 装少数特殊包**

---

## ⚙️ 九、清理缓存（释放磁盘空间）

```bash
conda clean -a
```

---

## 🔥 十、常见问题

### ❓1. Conda 很慢怎么办？

使用国内镜像（清华源）：

```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --set show_channel_urls yes
```

---

### ❓2. pip 和 conda 混用会冲突吗？

👉 建议顺序：

1. 先用 `conda install`
2. 再用 `pip install`
3. 不要反过来

---

## 🧩 总结常用命令速查表

| 操作   | 命令                                |
| ---- | --------------------------------- |
| 创建环境 | `conda create -n env python=3.10` |
| 激活环境 | `conda activate env`              |
| 退出环境 | `conda deactivate`                |
| 删除环境 | `conda remove -n env --all`       |
| 安装包  | `conda install pkg`               |
| 更新包  | `conda update pkg`                |
| 导出环境 | `conda env export > env.yml`      |
| 还原环境 | `conda env create -f env.yml`     |

---
