# carbon-project

[中文](#中文) | [English](#english)

---

## 中文

基于 Java + SQLite 的林木生长模型与生物量模型数据库，附带简单的 JDBC 查询工具。

### 状态

早期项目，不再维护。

### 功能

- `src/GrowthModel.db`：生长模型库，包括树种（`TreeSpecies`）、研究地点（`ResearchLocation`）、文献来源（`Research`）以及生长模型（`GrowthModel`，含模型表达式、模型形式、自变量及范围、R²、P 值等）。
- `src/BiomassModel.db`：在上述表的基础上增加生物量模型表（`BiomassModel`，含属/种、器官、林分类型、模型形式、R²、适用范围、文献信息等）。
- `DatabaseHelperForGrowth`：按树种中文名或拉丁名查询树种 ID，并打印该树种的生长模型（因变量、模型表达式、模型形式）。
- `DatabaseHelperForBiomass`：按属名或拉丁名查询生物量模型记录，并打印属、拉丁名、树种。
- 仅为命令行查询示例，没有图形界面。

### 技术栈

- Java 17
- Maven
- SQLite + `org.xerial:sqlite-jdbc` 3.34.0
- IntelliJ IDEA 项目配置（`.idea/`）

### 本地运行

需要 JDK 17 和 Maven。

1. 修改 `src/main/java/DatabaseHelperForGrowth.java` 和 `DatabaseHelperForBiomass.java` 中硬编码的 JDBC 地址（`jdbc:sqlite:/home/dahuangggg/IdeaProjects/testdb/src/...`），使其指向本仓库 `src/` 下的 `.db` 文件，例如 `jdbc:sqlite:src/GrowthModel.db`。
2. 在仓库根目录编译并运行：

```bash
mvn compile exec:java -Dexec.mainClass=DatabaseHelperForGrowth
```

示例会查询“云杉”的生长模型并输出到控制台。也可以直接在 IntelliJ IDEA 中打开项目并运行对应类的 `main` 方法。

> 注意：`DatabaseHelperForBiomass` 的 `main` 方法目前实际调用的是 `DatabaseHelperForGrowth`。

### 目录结构

```text
.
├── pom.xml                              # Maven 配置
├── src/
│   ├── GrowthModel.db                   # 生长模型 SQLite 数据库
│   ├── BiomassModel.db                  # 生物量模型 SQLite 数据库
│   └── main/java/
│       ├── DatabaseHelperForGrowth.java # 生长模型查询
│       ├── DatabaseHelperForBiomass.java# 生物量模型查询
│       └── org/example/Main.java        # IDE 生成的示例入口
└── .idea/                               # IntelliJ IDEA 配置
```

---

## English

A Java + SQLite database of forest tree growth models and biomass models, with simple JDBC query helpers.

### Status

Early project, no longer actively maintained.

### Features

- `src/GrowthModel.db`: growth model catalog with tree species (`TreeSpecies`), study locations (`ResearchLocation`), literature sources (`Research`) and growth models (`GrowthModel`: model expression, model form, independent variables and ranges, R², p-value, etc.).
- `src/BiomassModel.db`: the same tables plus a biomass model table (`BiomassModel`: genus/species, organ, forest type, model form, R², applicable range, literature info, etc.).
- `DatabaseHelperForGrowth`: looks up a species ID by Chinese or Latin name and prints its growth models (dependent variable, model expression, model form).
- `DatabaseHelperForBiomass`: looks up biomass model records by genus or Latin name and prints genus, Latin name and species.
- Command-line query examples only; there is no GUI.

### Tech Stack

- Java 17
- Maven
- SQLite + `org.xerial:sqlite-jdbc` 3.34.0
- IntelliJ IDEA project settings (`.idea/`)

### Getting Started

Requires JDK 17 and Maven.

1. Edit the hardcoded JDBC URLs (`jdbc:sqlite:/home/dahuangggg/IdeaProjects/testdb/src/...`) in `src/main/java/DatabaseHelperForGrowth.java` and `DatabaseHelperForBiomass.java` so they point to the `.db` files in this repo's `src/`, e.g. `jdbc:sqlite:src/GrowthModel.db`.
2. Build and run from the repo root:

```bash
mvn compile exec:java -Dexec.mainClass=DatabaseHelperForGrowth
```

The example queries the growth models for 云杉 (spruce) and prints them to the console. You can also open the project in IntelliJ IDEA and run a class's `main` method.

> Note: `DatabaseHelperForBiomass.main` currently calls `DatabaseHelperForGrowth` instead of itself.

### Directory Structure

```text
.
├── pom.xml                              # Maven config
├── src/
│   ├── GrowthModel.db                   # growth model SQLite database
│   ├── BiomassModel.db                  # biomass model SQLite database
│   └── main/java/
│       ├── DatabaseHelperForGrowth.java # growth model queries
│       ├── DatabaseHelperForBiomass.java# biomass model queries
│       └── org/example/Main.java        # IDE-generated sample entry point
└── .idea/                               # IntelliJ IDEA settings
```
