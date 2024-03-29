﻿---
实验室：
    标题：“实验室：使用 Azure 中的服务创建多层解决方案”
    类型：“答案”
    模块：“模块 6：连接并使用 Azure 和第三方服务
---

# 实验室：使用 Azure 中的服务创建多层解决方案
# 学生实验室答案

## Microsoft Azure 用户界面

鉴于 Microsoft 云工具的动态特性，Azure 用户界面 (UI) 在此培训内容开发后可能会发生更改。这些更改可能会导致实验室说明和步骤不匹配。

一旦 Microsoft 世界各地的学习团队通过社区注意到必要更改，将会立即更新此培训课程。但由于云更新频繁，你可能会在此培训内容更新前遇到 UI 更改。**如果发生这种情况，请根据需要适更改并在实验室中完成这些更改。**

## 说明

### 开始前

#### 登录实验室虚拟机

  - 使用以下凭据登录到 **Windows 10** 虚拟机：
    
      - **用户名**：Admin
    
      - **密码**：Pa55w.rd

> > **注**：讲师将为你提供实验室虚拟机登录说明。

#### 查看已安装的应用

  - 观察位于 **Windows 10** 桌面底部的任务栏。任务栏包含将在本实验室中使用的应用程序图标：
    
      - Microsoft Edge
    
      - 文件资源管理器
    
      - Microsoft Azure 存储资源管理器

#### 下载实验室文件

1.  在任务栏上，选择 **Windows PowerShell** 图标。

2.  在 PowerShell 命令提示符中，将当前工作目录更改为 **Allfiles (F):\\** 路径：

    ```
    cd F:
    ```

3.  在命令提示符中，输入以下命令并按 Enter 键以将 GitHub 上托管的 **microsoftlearning/AZ-203-DevelopingSolutionsForAzure** 项目克隆到 **Labfiles** 目录：

    ```
    git clone --depth 1 --no-checkout https://github.com/microsoftlearning/AZ-203-DevelopingSolutionsForMicrosoftAzure .
    ```

4.  在命令提示符中，输入以下命令并按 **Enter** 键以签出完成 **AZ-203.02** 实验室所必需的实验室文件：

    ```
    git checkout master -- Allfiles/*
    ```

5.  关闭当前正在运行的 **Windows PowerShell** 命令提示应用程序。

### 练习 1：在门户中创建 Azure 搜索服务

#### 任务 1：打开 Azure 门户

1.  在任务栏上，选择 **Microsoft Edge** 图标。

2.  在打开的浏览器窗口中，导航到 [**Azure 门户**](https://portal.azure.com) (portal.azure.com)。

3.  在登录页面，输入 Microsoft 帐户的 **电子邮件地址**。

4.  选择“**下一步**”。

5.  输入 Microsoft 帐户的 **密码**。

6.  选择“**登录**”。

> **注**：如果这是你第一次登录 **Azure 门户**，则会显示一个对话框，提供门户教程。选择“**开始使用**”以跳过教程并开始使用门户。

#### 任务 2：创建 Azure 搜索帐户

1.  在门户的左侧导航窗格，单击“**+ 创建资源**”。

> **注**：如果你找不到该链接，“创建资源”图标是位于门户左侧的加号字符。

2.  在“**新建**”边栏选项卡顶部，找到“**搜索市场**”字段。

3.  在搜索字段中，输入文本 **Search**，然后按 Enter 键。

4.  在“**全部内容**”搜索结果边栏选项卡中，选择“**Azure 搜索**”结果。

5.  在“**Azure 搜索**”边栏选项卡中，选择“**创建**”。

6.  在“**新建搜索服务**”边栏选项卡中，执行以下操作：
    
    1.  在“**URL**”字段中，输入 **prodsearch\[*your name in lowercase*\]**。
    
    2.  将“**订阅**”字段保留设置为默认值。
    
    3.  在“**资源组**”部分，选择“**新建**”，在弹出字段中输入 **MultiTierService**，然后选择“**确定**”。
    
    4.  在“**位置**”拉列表中，选择“**美国东部**”。
    
    5.  选择“**定价层**”链接。在“**定价层**”边栏选项卡中，选择“**基本**”，然后选择“**选择**”。
    
    6.  选择“**创建**”。

7.  等待创建任务完成后，再继续本实验室。

8.  在门户左侧的导航窗格中，选择“**资源组**”。

9.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

10. 在“**MultiTierService**”边栏选项卡中，选择你之前在此实验室中创建的 **prodsearch\*** 搜索服务。

11. 在“**搜索服务**”边栏选项卡的“**设置**”部分，选择“**密钥**”链接。

12. 在“**密钥**”部分，选择任意一个密钥并记录该值。你将稍后在实验室中使用此值。

> > **注**：选择使用哪个连接字符串无关紧要。它们可以互换。

#### 任务 3：创建索引

1.  在门户左侧的导航窗格中，选择“**资源组**”。

2.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

3.  在“**MultiTierService**”边栏选项卡中，选择你之前在此实验室中创建的 **prodsearch\*** 搜索服务。

4.  在“**搜索服务**”边栏选项卡中，选择“**添加索引**”。

5.  在“**添加索引**”边栏选项卡中，执行以下操作：
    
    1.  在“**索引名称**”字段中，输入 **retail**.。
    
    2.  在“**密钥**”列表中，选择“**id**”。
    
    3.  将“**建议器名称**”字段保留空白。
    
    4.  将“**搜索模式**”列表保留空白。

6.  在“**添加索引**”边栏选项卡中，将显示字段列表。执行以下操作以配置“**id**”字段：
    
    5.  在“**字段名称**”字段中，观察 **id** 的硬编码值。
    
    6.  在“**类型**”列表中，观察 **Edm.String** 的硬编码选项。
    
    7.  在“**可检索**”选项中，观察其硬编码为 **true**。
    
    8.  将“**可筛选**”保留为不选定。
    
    9.  选择“**可排序**”。
    
    10. 将“**可查找**”保留为不选定。
    
    11. 将“**可搜索**”保留为不选定。

7.  在“**添加索引**”边栏选项卡中，执行以下操作以配置新的“**名称**”字段：
    
    12. 在“**字段名称**”字段中，输入 **name**。
    
    13. 在“**类型**”列表中，选择“**Edm.String**”。
    
    14. 选择“**可检索**”。
    
    15. 将“**可筛选**”保留为不选定。
    
    16. 选择“**可排序**”。
    
    17. 将“**可查找**”保留为不选定。
    
    18. 选择“**可搜索**”。
    
    19. 在“**分析器**”列表中，选择“**标准 - Lucene**”。

8.  在“**添加索引**”边栏选项卡中，执行以下操作以配置新的“**价格**”字段：
    
    20. 在“**字段名称**”字段中，输入 **price**。
    
    21. 在“**类型**”列表中，选择“**Edm.Double**”。
    
    22. 选择“**可检索**”。
    
    23. 选择“**可筛选**”。
    
    24. 选择“**可排序**”。
    
    25. 选择“**可查找**”。

9.  在“**添加索引**”边栏选项卡中，执行以下操作以配置新的“**数量**”字段：
    
    26. 在“**字段名称**”字段中，输入 **quantity**。
    
    27. 在“**类型**”列表中，选择“**Edm.Int32**”。
    
    28. 选择“**可检索**”。
    
    29. 选择“**可筛选**”。
    
    30. 选择“**可排序**”。
    
    31. 选择“**可查找**”。

10. 在“**添加索引**”边栏选项卡中，执行以下操作以配置新的“**制造商**”字段：
    
    32. 在“**字段名称**”字段中，输入 **manufacturer**。
    
    33. 在“**类型**”列表中，选择“**Edm.String**”。
    
    34. 选择“**可检索**”。
    
    35. 选择“**可筛选**”。
    
    36. 选择“**可排序**”。
    
    37. 选择“**可查找**”。
    
    38. 将“**可搜索**”保留为不选定。

11. 在“**添加索引**”边栏选项卡中，选择“**创建**”。

#### 回顾

在本练习中，你创建了一个新的 Azure 存储帐户并在该帐户中构建了一个索引。

### 练习 2：在 Azure 搜索中为 Azure 存储表编制索引

#### 任务 1：创建 Azure 存储帐户

1.  在门户的左侧导航窗格，单击“**+ 创建资源**”。

2.  在“**新建**”边栏选项卡顶部，找到“**搜索市场**”字段。

3.  在搜索字段中，输入 **Storage**，然后按 Enter 键。

4.  在“**全部内容**”搜索结果边栏选项卡中，选择“**存储帐户**”结果。

5.  在“**存储帐户**”边栏选项卡中，选择“**创建**”。

6.  在“**创建存储帐户**”边栏选项卡中，观察边栏选项卡顶部的选项卡。

> **注**：每个选项卡代表工作流中创建新“**存储帐户**”的一个步骤。你可以随时选择“**查看 + 创建**”跳过剩余标签。

7.  在“**基本**”选项卡中，执行以下操作：
    
    1.  将“**订阅**”字段保留设置为默认值。
    
    2.  在“**资源组**”列表中，选择“**MultiTierService**”。
    
    3.  在“**存储帐户名称**”字段中，输入 **prodstorage\[*your name in lowercase*\]**。
    
    4.  在“**位置**”拉列表中，选择“**美国东部**”。
    
    5.  在“**性能**”部分，选择“**标准**”。
    
    6.  在“**帐户类型**”列表中，选择 **StorageV2（通用 v2）**。
    
    7.  在“**复制**”列表中，选择“**读取访问异地冗余存储 (RA-GRS)**”。
    
    8.  在“**访问层**”部分，确保“**热**”已选中。
    
    9.  选择“**查看 + 创建**”。

8.  在“**查看 + 创建**”选项卡中，查看在之前步骤中输入的选项。

9.  选择“**创建**”以使用指定的配置创建存储帐户。

10. 等待创建任务完成后，再继续本实验室。

11. 在门户左侧的导航窗格中，选择“**资源组**”。

12. 在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

13. 在“**MultiTierService**”边栏选项卡中，选择你之前在本实验室中创建的 **prodstorage\*** 存储帐户。

14. 在“**存储帐户**”边栏选项卡中，在边栏选项卡左侧的“**设置**”部分，选择“**访问密钥**”链接。

15. 在“**访问密钥**”边栏选项卡中，选择任意一个密钥并记录“**连接字符串**”字段中的任意一个值。你将稍后在本实验室中使用此值。

> > **注**：选择哪个连接字符串无关紧要。它们可以互换。

#### 任务 2：将表实体上传到 Azure 存储

1.  在门户左侧的导航窗格中，选择“**资源组**”。

2.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

3.  在“**MultiTierService**”边栏选项卡中，选择你之前在本实验室中创建的 **prodstorage\*** 存储帐户。

4.  在“**存储帐户**”边栏选项卡中，在边栏选项卡左侧的“**表服务**”部分，选择“**表**”链接。

5.  在“**表**”部分，选择“**+ 表**”。

6.  在“**添加表格**”窗口中，执行以下操作：
    
    1.  在“**表****名称**”字段中，输入 **products**。
    
    2.  选择“**确定**”。

7.  返回边栏选项卡左侧的“**表**”，选择“**概述**”链接。

> > **注**：你可能必须在边栏选项卡左侧的菜单中上下滚动菜单。

8.  返回“**概述**”部分，选择“**在资源管理器**”中打开。

9.  在“**Azure 存储资源管理器**”窗口中，选择“**打开 Azure 存储资源管理器**”链接。

> > **注**：如果这是你第一次使用门户打开 **Azure 存储资源管理器**，可能会提示你允许门户未来打开这些类型的链接。你应接受该提示。

10. 在显示的 **Azure 存储资源管理器**应用程序中，找到并展开之前在本实验室中创建的 **prodstorage\* 存储帐户。

11. 在 **prodstorage\*** 存储帐户中，找到并展开**表**节点。

12. 在“**表**”节点中，选择之前在本实验室中创建的 **products** 表。

13. 在“**产品表**”选项卡中，选择“**导入**”。

14. 在显示的“**文件资源管理器**”对话框中，执行以下操作：
    
    3.  转到 **Allfiles (F):\\Labfiles\\06\\Starter**。
    
    4.  选择 **products.csv** 文件。
    
    5.  选择“**打开**”。

15. 在显示的“**导入实体**”窗口中，选择“**插入**”。

16. 等待表实体更新再继续本实验室。

17. 观察已添加到 **products** 表的五个实体。

18. 返回显示 **Azure 门户**的浏览器窗口。

#### 任务 3：创建 Azure 搜索索引器

1.  在门户左侧的导航窗格中，选择“**资源组**”。

2.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

3.  在“**MultiTierService**”边栏选项卡中，选择之前在此实验室中创建的 **prodsearch\*** 搜索服务。

4.  在“**搜索服务**”边栏选项卡中，选择“**导入数据**”。

5.  在“**导入数据**”边栏选项卡中，观察边栏选项卡顶部的选项卡。

6.  在“**连接数据**”选项卡中，执行以下操作：
    
    1.  在“**数据来源**”列表中，选择“**Azure 表存储**”。
    
    2.  在“**名称**”字段中，输入 **tabledatasource**。
    
    3.  在“**连接字符串**”字段中，选择“**选择现有连接**”。在“**选择存储帐户**”窗口中，选择你之前在本实验室中创建的 **prodstorage\*** 存储帐户。
    
    4.  在“**表名称**”字段中，输入 **products**。
    
    5.  将“**查询**”字段保留空白。
    
    6.  将“**描述**”字段保留空白。
    
    7.  选择“**下一步：**”**添加认知搜索（可选）**。

> > **注**：Azure 搜索会在每个步骤验证您的设置。可能需要几分钟才能完成验证并转到列表中的下一个选项卡。

7.  在“**添加认知搜索**”选项卡中，选择“**下一个：**”**自定义目标索引**。

8.  在“**自定义目标索引**”选项卡中，执行以下操作：
    
    8.  在“**索引名称**”字段中，输入 **products**。
    
    9.  在“**密钥**”列表中，选择“**RowKey**”。

9.  在“**自定义目标索引**”选项卡中，将显示字段列表。将“**PartitionKey**”、“**RowKey**”、“**ETag**”和“**时间戳**”保留设置为默认值。

10. 在“**自定义目标索引**”选项卡中，执行以下操作以配置“**密钥**”字段：
    
    39. 在“**字段名称**”字段中，观察**密钥**的硬编码值。
    
    40. 在“**类型**”列表中，观察 **Edm.String** 的硬编码选项。
    
    41. 选择“**可检索**”。
    
    42. 将“**可筛选**”保留为不选定。
    
    43. 选择“**可排序**”。
    
    44. 将“**可查找**”保留为不选定。
    
    45. 将“**可搜索**”保留为不选定。

11. 在“**自定义目标索引**”选项卡中，执行以下操作以配置“**名称**”字段：
    
    10. 在“**字段名称**”字段中，观察**名称**的硬编码值。
    
    11. 在“**类型**”列表中，观察 **Edm.String** 的硬编码选项。
    
    12. 选择“**可检索**”。
    
    13. 将“**可筛选**”保留为不选定。
    
    14. 选择“**可排序**”。
    
    15. 将“**可查找**”保留为不选定。
    
    16. 选择“**可搜索**”。
    
    17. 在“**分析器**”列表中，选择“**标准 - Lucene**”。

12. 在“**自定义目标索引**”选项卡中，执行以下操作以配置“**价格**”字段：
    
    18. 在“**字段名称**”字段中，观察**价格**的硬编码值。
    
    19. 在“**类型**”列表中，观察 **Edm.Double** 的硬编码选项。
    
    20. 选择“**可检索**”。
    
    21. 选择“**可筛选**”。
    
    22. 选择“**可排序**”。
    
    23. 选择“**可查找**”。

13. 在“**自定义目标索引**”选项卡中，执行以下操作以配置“**数量**”字段：
    
    24. 在“**字段名称**”字段中，观察**数量**的硬编码值。
    
    25. 在“**类型**”列表中，观察 **Edm.Int32** 的硬编码选项。
    
    26. 选择“**可检索**”。
    
    27. 选择“**可筛选**”。
    
    28. 选择“**可排序**”。
    
    29. 选择“**可查找**”。

14. 在“**自定义目标索引**”选项卡中，选择“**下一个：**”**创建索引器**。

> > **注**：Azure 搜索会在每个步骤验证您的设置。可能需要几分钟才能完成验证并转到列表中的下一个选项卡。

15. 在“**创建索引器**”选项卡中，执行以下操作：
    
    30. 在“**名称**”字段中，输入 **tableindexer**。
    
    31. 在“**计划**”部分，选择“**自定义**”。
    
    32. 在“**间隔**”字段，输入 **5**。
    
    33. 将“**开始时间**”字段保留设置为默认值。
    
    34. 将“**跟踪删除**”字段保留设置为默认值。
    
    35. 将“**描述**”字段保留空。
    
    36. 选择“**提交**”。

16. 返回“**搜索服务**”边栏选项卡中，选择“**索引器**”标签。

17. 在“**索引器**”选项卡中，选择你之前在本实验室中创建的 **tableindexer** 索引器。

18. 在“**索引器**”边栏选项卡中，执行以下操作：
    
    37. 选择“**运行**”。
    
    38. 提示你确认时，选择“**是**”。
    
    39. 关闭“**索引器**”边栏选项卡。

19. 等待索引器完成运行，然后选择边栏选项卡顶部的“**刷新**”。

> > **注**：索引器运行可能需要一到五分钟。如果“**搜索服务**”边栏选项卡中的索引器状态列为“**成功**”，则表示索引器成功。

20. 返回“**搜索服务**”边栏选项卡中，选择“**索引器**”标签。

21. 在“**索引器**”标签中，观察 **tableindexer** 索引器的元数据，例如文档计数和上次索引操作的状态。

22. 关闭“**索引器**”边栏选项卡。

#### 任务 4：验证索引表数据

1.  在“**搜索服务**”边栏选项卡中，选择“**搜索浏览器**”。

2.  在“**搜索浏览器**”边栏选项卡中，选择“**搜索**”。

3.  观察所有文档的搜索结果。

4.  在“**查询字符串**”字段中，输入以下查询并按“**搜索**”：

<!-- end list -->

    search=seat

5.  观察搜索查询的结果。

6.  在“**查询字符串**”字段中，输入以下查询并按“**搜索**”：

<!-- end list -->

    $filter=price lt 100

7.  观察搜索查询的结果。

8.  在“**查询字符串**”字段中，输入以下查询并按“**搜索**”：

<!-- end list -->

    facet=quantity,interval:25

9.  观察搜索查询的结果。

10. 在“**查询字符串**”字段中，输入以下查询并按“**搜索**”：

<!-- end list -->

    $filter=quantity gt 25&facet=price,values:100|1000|10000

11. 观察搜索查询的结果。

#### 任务 5：检索 Azure 搜索基本 URL

1.  在门户左侧的导航窗格中，选择“**资源组**”。

2.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

3.  在“**MultiTierService**”边栏选项卡中，选择你之前在此实验室中创建的 **prodsearch\*** 搜索服务。

4.  在“**搜索服务**”边栏选项卡，复制“**URL**”字段的值。你将稍后在本实验室中使用此值。

#### 回顾

在本练习中，你通过使用 Azure 搜索创建了 Azure 存储帐户并在帐户中为存储表创建了索引。为表创建索引后，您可以对存储表中的实体副本发出搜索查询。

### 练习 3：使用 Azure API 管理构建 API 代理层

#### 任务 1：创建 API 管理资源

1.  在门户的左侧导航窗格，单击“**+ 创建资源**”。

2.  在“**新建**”边栏选项卡顶部，找到“**搜索市场**”字段。

3.  在搜索字段中，输入 **API**，然后按 Enter 键。

4.  在“**全部内容**”搜索结果边栏选项卡中，选择“**API 管理**”结果。

5.  在“**API 管理**”边栏选项卡中，选择“**创建**”。

6.  在“**API 管理服务**”边栏选项卡中，执行以下操作：
    
    1.  在“**名称**”字段中，输入 **prodapi\[*your name in lowercase*\]**。
    
    2.  将“**订阅**”字段保留设置为默认值。
    
    3.  在“**资源组**”列表中，选择“**MultiTierService**”。
    
    4.  在“**位置**”拉列表中，选择“**美国东部**”。
    
    5.  在“**组织名称**”字段中，输入 **Contoso**。
    
    6.  将“**管理员电子邮件**”字段保留设置为默认值。
    
    7.  在“**定价层**”列表中，选择“**开发人员（无 SLA）**”。
    
    8.  选择“**创建**”。

7.  等待创建任务完成后，再继续本实验室。

> > **注**：创建 API 管理服务通常需要 20 到 30 分钟。

#### 任务 2：定义一个新的 API

1.  在门户左侧的导航窗格中，选择“**资源组**”。

2.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

3.  在“**MultiTierService**”边栏选项卡中，选择你之前在本实验室中创建的 **prodapi\*** API 管理帐户。

4.  在“**API 管理服务**”边栏选项卡中，在边栏选项卡左侧的“**API 管理**”部分，选择“**API**”。

5.  在“**添加新的 API**”部分，**选择“空白 API**”。

6.  在“**创建空白 API**”窗口中，执行以下操作：
    
    1.  在“**显示名称**”字段中，输入 **Search API**。
    
    2.  在“**名称**”字段中，输入 **images-thumbnails**。
    
    3.  在“**Web 服务 URL**”字段中，输入之前在本实验室中复制的“**搜索服务 URL**”字段的 URL。
    
    4.  通过以下相关 URL 追加 **Web 服务 URL** 字段的值：

> 
> 
>     /indexes/products/docs
> 
> > **注**：例如，如果 Web 服务 URL 为 https://prodsearchstudent.search.windows.net，新的 URL 将为 https://prodsearchstudent.search.windows.net/indexes/products/docs。

5.  在“**API URL 后缀**”字段中，输入 **search**。

6.  在“**产品**”字段中，同时选择“**起动器**”和“**无限**”。

7.  选择“**创建**”。

<!-- end list -->

7.  等待新 API 完成创建。

8.  在“**设计**”选项卡中，选择“**+ 添加操作**”。

9.  在“**添加操作**”部分，执行以下操作：
    
    8.  在“**显示名称**”字段中，输入 **List All Documents**。
    
    9.  在“**名称**”字段中，输入 **list-all-documents**。
    
    10. 在“**URL**”列表中，选择“**GET**”。
    
    11. 在“**URL**”字段中，输入 **/**。
    
    12. 选择“**保存**”。

10. 返回“**设计**”选项卡，在操作列表中选择“**所有操作**”。

11. 在“**所有操作**”的“**设计**”部分，找到“**入站处理**”磁贴并选择“**+ 添加策略**”。

12. 在“**添加入站策略**”部分，选择“**设置标题**”磁贴。

13. 在“**入站处理，设置标题**”部分，执行以下操作：
    
    13. 在“**名称**”字段中，输入 **api-key**。
    
    14. 在“**值**”字段中，选择列表，选择“**+ 添加值**”，然后输入之前在本实验室中记录的“**搜索服务密钥**”的值。
    
    15. 在“**操作**”列表中，选择“**替代**”选项。
    
    16. 选择“**保存**”。

14. 返回“**设计**”选项卡，在操作列表中选择“**所有操作**”。

15. 在“**所有操作**”的“**设计**”部分，找到“**入站处理**”磁贴并选择“**+ 添加策略**”。

16. 在“**添加入站策略**”部分，选择“**设置查询参数**”磁贴。

17. 在“**入站处理，设置查询参数**”部分，执行以下操作：
    
    17. 在“**名称**”字段中，输入 **api-version**。
    
    18. 在“**值**”字段中，输入 **2017-11-11**。
    
    19. 在“**操作**”列表中，选择“**替代**”。
    
    20. 选择“**保存**”。

18. 返回“**设计**”选项卡，在操作列表中选择“**列出所有文档**”。

19. 在“**列出所有文档**”操作的“**设计**”部分，找到“**入站处理**”磁贴，然后选择“**+ 添加策略**”按钮。

20. 在“**添加入站策略**”部分，选择“**设置查询参数**”磁贴。

21. 在“**入站处理，设置查询参数**”部分，执行以下操作：
    
    21. 在“**名称**”字段中，输入 **search**。
    
    22. 在“**值**”字段中，输入 **\***。
    
    23. 在“**操作**”列表中，选择“**替代**”。
    
    24. 选择“**保存**”。

22. 返回“**设计**”选项卡，在操作列表中选择“**列出所有文档**”。

23. 选择“**测试**”选项卡。

24. 选择“**列出所有文档**”操作。

25. 在“**列出所有文档**”部分，选择“**发送**”。

26. 观察 API 请求结果。

> > **注**：观察响应中是否存在大量 Azure 搜索元数据。你可能不希望 API 用户了解幕后发生的实现细节。在下一个任务中，你将混淆大部分此类数据。

27. 选择“**设计**”选项卡返回操作列表。

#### 任务 3：操纵 API 响应

1.  返回“**设计**”选项卡，在操作列表中选择“**列出所有文档**”。

2.  在“**列出所有文档**”操作的“**设计**”部分，找到“**出站处理**”磁贴，然后选择“**+ 添加策略**”。

3.  在“**添加出站策略**”部分，选择“**其他策略**”磁贴。

4.  在策略代码编辑器中，找到以下 XML 内容块：

<!-- end list -->

    <outbound>
        <base />
    </outbound>

使用以下 XML 替换该 XML 块：

    <outbound>
        <base />
        <set-body>
        @{ 
            var response = context.Response.Body.As<JObject>();
            return response.Property("value").Value.ToString();
        }
        </set-body>
    </outbound>

5.  在策略代码编辑器中，选择“**保存**”。

6.  返回“**设计**”选项卡，在操作列表中选择“**列出所有文档**”。

7.  在“**列出所有文档**”操作的“**设计**”部分，找到“**出站处理**”磁贴，然后选择“**+ 添加策略**”。

8.  在“**添加出站策略**”部分，选择“**设置标题**”磁贴。

9.  在“**出站处理，设置标题**”部分，执行以下操作：
    
    1.  在“**名称**”字段中，输入 **preference-applied**。
    
    2.  在“**操作**”列表中，选择“**删除**”。
    
    3.  选择“**+** **添加标题**”。
    
    4.  在新的“**名称**”字段中，输入 **odata-version**。
    
    5.  在新的“**操作**”列表中，选择“**删除**”。
    
    6.  选择“**+ 添加标题**”。
    
    7.  在新的“**名称**”字段中，输入 **powered-by**。
    
    8.  在新的“**值**”字段中，选择列表，选择“**+ 添加值**”链接，然后输入 **Contoso**。
    
    9.  在新的“**操作**”列表中，选择“**替代**”。
    
    10. 选择“**保存**”。

10. 返回“**设计**”选项卡，在操作列表中选择“**列出所有文档**”。

11. 选择“**测试**”选项卡。

12. 选择“**列出所有文档**”操作。

13. 在“**列出所有文档**”部分，选择“**发送**”。

14. 观察 API 请求结果。

> > **注**：你将观察到你指定的 **preference-applied** 和 **odata-version** 标题已被删除并被新的 **powered-by** 标题替换。你还将注意到响应不包含有关 OData 响应的上下文数据，而是包含平展 JSON 数组作为响应正文。

#### 回顾

在本练习中，你在 Azure 搜索帐户和任何希望进行搜索查询的开发人员之间构建了代理层。

### 练习 4：使用 Azure 逻辑应用创建新的表实体

#### 任务 1：创建逻辑应用资源

1.  在门户的左侧导航窗格，单击“**+ 创建资源**”。

2.  在“**新建**”边栏选项卡顶部，找到“**搜索市场**”字段。

3.  在搜索字段中，输入 **Logic**，然后按 Enter 键。

4.  在“**全部内容**”搜索结果边栏选项卡中，选择“**逻辑应用**”结果。

5.  在“**逻辑应用**”边栏选项卡中，选择“**创建**”。

6.  在“**逻辑应用**”边栏选项卡中，执行以下操作：
    
    1.  在“**名称**”字段中，输入 **prodworkflow\[*your name in lowercase*\]**。
    
    2.  将“**订阅**”字段保留设置为默认值。
    
    3.  在“**资源组**”部分，选择“**使用现有**”，然后从列表选择“**MultiTierService**”选项。
    
    4.  在“**位置**”拉列表中，选择“**美国东部**”。
    
    5.  在“**日志分析**”部分，选择“**关**”。
    
    6.  选择“**创建**”。

7.  等待创建任务完成后，再继续本实验室。

#### 任务 2：创建逻辑应用工作流触发器

1.  在门户左侧的导航窗格中，选择“**资源组**”。

2.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

3.  在“**MultiTierService**”边栏选项卡中，选择你之前在本实验室中创建的 **prodworkflow\*** 逻辑应用。

4.  在“**逻辑应用设计器**”边栏选项卡中，选择“**空白逻辑应用**”模板。

5.  在“**设计器**”区域，执行以下操作以添加 **HTTP 触发器**：
    
    1.  在“**搜索连接器和触发器**”字段，输入 **HTTP**。
    
    2.  在“**触发器**”结果列表中，选择“**收到 HTTP 求时**”。
    
    3.  选择“**使用示例有效负载生成架构**”。
    
    4.  在“**输入或粘贴示例 JSON 有效负载**”窗口中，输入以下 JSON 对象：

> 
> 
> ``` 
> { 
> ```
> 
> ``` 
>     "id": "",
> ```
> 
> ``` 
>     "manufacturer": "",
> ```
> 
> ``` 
>     "price": 0.00,
> ```
> 
> ``` 
>     "quantity": 0,
> ```
> 
> ``` 
>     "name": ""
> ```
> 
> ``` 
> }
> ```

5.  选择“**完成**”。

6.  观察“**请求正文 JSON 架构**”字段中的架构。此架构由 Azure 根据你在上一步中输入的 JSON 内容自动构建。

#### 任务 3：构建 Azure 存储连接器

1.  在“**设计器**”区域，选择“**+ 新建步骤**”。

2.  在“**设计器**”区域，执行以下操作以添加 **插入或替换实体操作**：
    
    1.  在“**搜索连接器和触发器**”字段，输入 **Table**。
    
    2.  在类别列表中，选择“**Azure 表存储**”。
    
    3.  在“**操作**”结果列表中，选择“**插入或替换实体**”。
    
    4.  在“**连接名称**”字段中，输入 **tableconnection**。
    
    5.  在“**存储帐户**”部分，选择你之前在本实验室中创建的 **prodstorage\*** 存储帐户。
    
    6.  选择“**创建**”。
    
    7.  等待连接器资源完成创建。

> **注**：这些资源需要一到五分钟才能创建。

8.  在“**表**”列表中，选择“**产品**”。

9.  在“**分区键**”字段右侧“**动态内容**”窗格的“**收到 HTTP 请求时**”类别中，选择“**制造商**”。

10. 在“**行键**”字段右侧“**动态内容**”窗格的“**收到 HTTP 请求时**”类别中，选择“**id**”。

11. 在“**实体**”字段右侧“**动态内容**”窗格的“**收到 HTTP 请求时**”类别中，选择“**正文**”。

#### 任务 4：构建 HTTP 响应操作

1.  在“**设计器**”区域，选择“**+ 新建步骤**”。

2.  在“**设计器**”区域，执行以下操作以添加 **响应操作**：
    
    1.  在“**搜索连接器和触发器**”字段，输入 **Response**。
    
    2.  在“**操作**”结果列表中，选择“**响应**”。
    
    3.  在“**状态代码**”字段，输入 **201**。
    
    4.  在“**正文**”字段右侧“**动态内容**”窗格的“**替换实体插入**”类别中，选择“**正文**”。

#### 任务 5：检索 HTTP 触发器 POST URL

1.  在“**设计器**”区域，选择“**保存**”。

2.  保存工作流之后，“**收到 HTTP 请求时**”触发器中的“**HTTP POST URL**”字段将更新为启动此工作流所需的新 URL。复制“**HTTP POST URL**”字段中的 URL。你将稍后在此实验室中使用此 URL。

> > **注**：此 URL 非常长，因为其包含 URL 和 SAS 令牌。确保复制整个 URL。

#### 任务 6：验证逻辑应用程序结果是否已编制索引

1.  在门户顶部，选择 **Cloud Shell** 图标打开一个新的 Shell 实例。

> **注**：**Cloud Shell** 图标使用大于符号和下划线字符表示。

![](media/image1.png)

2.  如果这是你第一次使用订阅打开 **Cloud Shell**，将显示**欢迎使用 Azure Cloud Shell 向导**，显示在第一次使用时如何配置 **Cloud Shell**。执行以下操作：
    
    1.  系统提示你在 **Bash** 或 **PowerShell** 之间选择时，请选择“**Bash**”。
    
    2.  将显示一个对话框，提示你创建新的存储帐户以开始使用 Shell。接受默认设置并选择“**创建存储**”。
    
    3.  等待 **Cloud Shell** 完成首次设置程序再继续此实验室。

> > **注**：如果 **Cloud Shell** 配置选项未显示，这很可能是因为你在本课程实验室中使用的是现有订阅。实验室是在你使用新订阅的假设条件下编写的。

3.  在门户底部的 **Cloud Shell** 命令提示符中，输入以下部分 **CURL** 命令以将 **HTTP POST** 请求发出到逻辑应用实例，然后按 **Enter** 键：

<!-- end list -->

    curl \
    --header "Content-Type: application/json" \
    --data '{"id":"6","manufacturer":"VEHTOP","price":750,"quantity":6,"name":"car roof rack"}' \

4.  然后，输入之前在本实验室中复制的逻辑应用  **HTTP POST URL**，确保将 URL 置于**引号**内，防止 URL 字符转义。按 **Enter** 键执行命令。

> > **注**：例如，如果 URL 为 https://prod.eastus.logic.azure.com:443/workflows/test/triggers/invoke?api-version=2016\&sig=3，则你将插入“https://prod.eastus.logic.azure.com:443/workflows/test/triggers/manual?invoke?api-version=2016\&sig=3”。如果不包含引号，则会收到一条错误消息，指出 SAS 令牌已被截断并且需要发出请求。这是由于查询字符串分隔符 **&** 导致的，如果不用引号将其括起，则会被截断。

5.  在门户左侧的导航窗格中，选择“**资源组**”。

6.  在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

7.  在“**MultiTierService**”边栏选项卡中，选择你之前在此实验室中创建的 **prodsearch\*** 搜索服务。

8.  在“**搜索服务**”边栏选项卡中，选择“**索引器**”标签。

9.  在“**索引器**”选项卡中，选择你之前在本实验室中创建的 **tableindexer** 索引器。

10. 在“**索引器**”边栏选项卡中，执行以下操作：
    
    40. 选择“**运行**”。
    
    41. 提示你确认时，选择“**是**”。
    
    42. 关闭“**索引器**”边栏选项卡。

11. 等待索引器完成运行，然后选择边栏选项卡顶部的“**刷新**”。

<!-- end list -->

12. 返回“**搜索服务**”边栏选项卡，选择“**搜索浏览器**”。

13. 在“**搜索浏览器**”边栏选项卡中，选择“**搜索**”。

14. 观察所有文档的搜索结果。

> > **注**：此时，您将注意到索引中的第六个文档，该文档表示逻辑应用插入的新文档。

15. 在门户左侧的导航窗格中，选择“**资源组**”。

16. 在“**资源组**”边栏选项卡中，选择你之前在本实验室中创建的 **MultiTierService** 资源组。

17. 在“**MultiTierService**”边栏选项卡中，选择你之前在本实验室中创建的 **prodapi\*** API 管理帐户。

18. 在“**API 管理服务**”边栏选项卡中，在边栏选项卡左侧的“**API 管理**”部分，选择“**API**”。

19. 在“**API**”部分，选择“**搜索 API**”。

20. 在“**设计**”选项卡中，选择“**测试**”选项卡。

21. 选择“**列出所有文档**”操作。

22. 在“**列出所有文档**”部分，选择“**发送**”。

23. 观察 API 请求结果。

> > **注**：观察到现在有六个文档而不是五个。

#### 回顾

在本练习中，你创建了一个接受 HTTP 请求，然后将请求的 JSON 正文保留为新的 Azure 存储表实体的逻辑应用。

### 练习 5：清理订阅 

#### 任务 1：打开 Cloud Shell

1.  在门户顶部，选择 **Cloud Shell** 图标打开一个新的 Shell 实例。

2.  在门户底部的 **Cloud Shell** 命令提示符下，输入以下命令并按 Enter 键以列出订阅中的所有资源组。

<!-- end list -->

    az group list

3.  输入以下命令，然后按 Enter 键查看删除资源组的可能命令列表：

<!-- end list -->

    az group delete --help

#### 任务 2：删除资源组

1.  输入以下命令，然后按 Enter 键删除 **MultiTierService** 资源组：

<!-- end list -->

    az group delete --name MultiTierService --no-wait --yes

2.  关闭门户底部的“**Cloud Shell**”窗格。

#### 任务 3：关闭活动应用程序

1.  关闭当前正在运行的 **Microsoft Edge** 应用程序。

2.  关闭当前正在运行的 **Microsoft Azure 存储资源管理器** 应用程序。

#### 回顾

在本练习中，你通过移除本实验室中使用过的 **资源组** 来清理订阅。
