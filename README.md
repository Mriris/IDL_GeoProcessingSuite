# IDL_GeoProcessingSuite

IDL_GeoProcessingSuite 是一个使用 IDL 编程语言开发的高分三号（GF3）数据处理脚本套件，包含从数据导入到多视处理、地理编码和导出等多个模块，支持完整的高分三号数据处理流程。

## 项目结构

该项目分为 **Unit** 和 **Integration** 两个部分：

### Unit 文件夹
单元模块，负责实现数据处理的核心功能，包括以下脚本（按执行顺序）：
1. **GF3_Import_Process.pro**  
   导入高分三号数据的脚本，用于加载并预处理数据。

2. **GF3_Filter_Process.pro**  
   数据过滤与增强脚本，用于对高分三号数据进行去噪和增强。

3. **Geocoding_Process.pro**  
   地理编码脚本，用于将数据映射到地理坐标系。

4. **Generate_Meta_From_DB_With_Dimensions.pro**  
   Meta 文件生成脚本，从数据文件中提取维度和其他元信息，生成 meta 文件。

5. **Generate_DEM.pro**  
   数字高程模型（DEM）生成脚本，从影像中提取高程信息。

6. **Export_Meta_To_TIFF.pro**  
   数据导出脚本，将处理后的数据和 meta 信息导出为 TIFF 格式文件。

7. **GF3_Multilooking_Process.pro**  
   多视处理脚本，用于提升图像质量或合成多个视角的数据。

### Integration 文件夹
集成模块，整合 Unit 中的单元模块，完成完整数据处理流程：
1. **GF3_Pipeline_Process.pro**  
   高分三号数据处理管道脚本，串联多个单元模块，实现完整的自动化数据处理流程。

2. **GF3_One_Process.pro**  
   单次处理脚本，用于调试或快速执行单个完整操作。

## 使用说明

### 环境要求
- IDL 环境（建议版本：8.8）
- ENVI 软件（建议版本：5.6）
- 高分三号数据文件

### 快速开始
1. 克隆本项目到本地：
   ```bash
   git clone git@github.com:Mriris/IDL_GeoProcessingSuite.git
   ```
2. 在 IDL 环境中加载并运行需要的脚本：
   - 单独测试某一功能时，可加载 Unit 文件夹中的脚本。
   - 执行完整流程时，可加载 Integration 文件夹中的脚本。

3. 执行完整流程示例：
   ```idl
   .compile 'GF3_Pipeline_Process.pro'
   GF3_Pipeline_Process
   ```

### 输出
- 所有处理结果将保存为 TIFF 文件或其他格式的文件，存储在指定的输出目录中。

## 贡献
如果您有改进建议或发现问题，请提交 Issue 或 Pull Request，我们欢迎所有贡献！