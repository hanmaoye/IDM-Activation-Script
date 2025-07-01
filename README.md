# IDM 激活脚本
一个开源工具，用于激活和重置试用期 [Internet Download Manager](https://www.internetdownloadmanager.com/)

# 免责声明
我想澄清一下，我不是这个脚本的原作者。我创建这个仓库的主要目的是为中文用户简化流程。此外，作为对脚本原作者工作的尊重，我确保注明了他们。

# 特点
* IDM 冻结试用及使用注册表键锁定方法进行激活
* 即使安装了 IDM 更新，激活和试用仍然存在。
* IDM 试用重置
* 完全开源
* 基于透明批处理脚本

# IAS 最新版本
最新版本 - v1.2 (12-Feb-2024)
[GitHub](https://github.com/hanmaoye/IDM-Activation-Script)

# 下载 / 如何使用它？
首先安装最新的 [Internet Download Manager](https://www.internetdownloadmanager.com/). 如果有任何以前的破解补丁，请确保将其删除或卸载。
之后，按照以下步骤激活它。

# 日志
* 📌 该激活选项目前在脚本中无法使用，请使用 “冻结试用” 选项将 30 天的试用期锁定为终身有效。

# 方法 1 - PowerShell
(推荐的)

* 右键单击 Windows 开始菜单，然后选择 “PowerShell” 或 “终端”（不要选 “CMD命令提示符”）。

* 复制粘贴下面的代码并按回车键

  ```shell
  iex(irm is.gd/idm_AS)
  ```

  或

  ```shell
  iwr -useb https://raw.githubusercontent.com/hanmaoye/IDM-Activation-Script/main/IDM_AS.ps1 | iex
  ```

  或

  ```shell
  iwr -useb https://is.gd/idm_AS | iex
  ```

* 你将看到激活选项，请按照屏幕上的说明操作。

* 就这些。

# 方法 2 - Traditional

* 从 [GitHub](https://github.com/hanmaoye/IDM-Activation-Script/archive/refs/heads/main.zip)下载该文件
* 右键点击下载的压缩文件并解压
* 右键点击下载的压缩文件并解压 `IAS.cmd`
* 你将看到激活选项，并按照屏幕上的说明操作。
* 就这些。

# 信息
## 冻结试验
* IDM 提供 30 天的试用期，你可以在脚本中使用此选项将此试用期锁定终身，这样你就无需再次重置试用期，而且你的试用期也不会过期。
* 应用此选项时，此方法需要联网。
* IDM更新可以直接安装，无需再次冻结。

## 激活
(***目前无法正常工作**)

* 此脚本应用注册表锁定方法来激活互联网下载管理器（IDM）。
* 此方法在激活时需要联网。
* IDM更新可以直接安装，无需再次激活。
* 激活后，如果在某些情况下，IDM开始显示激活提示屏幕，那么只需再次运行激活选项，无需使用重置选项。

## 重置IDM激活/试用
* 互联网下载管理器提供30天的试用期，你可以随时使用此脚本重置激活/试用期。
* 此选项也可用于在IDM报告假序列号密钥及其他类似错误的情况下恢复状态。

## 操作系统要求
* 该项目支持 Windows 7/8/8.1/10/11 及其对应的服务器版本。
* 在Windows 8及更高版本上支持使用PowerShell方法运行IAS。

## 高级信息
* 要在无人参与模式下激活，请使用 /act 参数运行脚本。
* 要在无人值守模式下冻结试验，请使用 /frz 参数运行脚本。
* 要在无人参与模式下重置，请使用/res参数运行脚本。

# 它是如何工作的？
* IDM会在各种注册表项中存储与试用和激活相关的数据。其中一些注册表项被锁定，以防止篡改，并且数据以一种特定模式存储，用于追踪伪造序列号问题和剩余试用天数。要激活它，此处的脚本只需通过在IDM中触发一些下载来生成这些注册表项，识别这些注册表项并将其锁定，这样IDM就无法编辑和查看它们。通过这种方式，IDM就不会显示它是使用伪造序列号激活的警告。 

# 排查故障
* 浏览器集成修复: [Chrome](https://www.internetdownloadmanager.com/register/new_faq/bi9.html) - [Firefox](https://www.internetdownloadmanager.com/register/new_faq/bi4.html)

# 变更日志
## v1.2
* 添加了带有随机生成的姓名、电子邮件和注册详细信息中的密钥的激活选项，并附带警告，称该选项对部分用户不起作用，建议的选项是使用冻结试用。
## v1.1
* IDM 6.42b3版本更新后，在使用IAS激活时开始出现虚假的序列号弹窗。因此，我们移除了激活选项，取而代之的是“冻结试用”选项，以便终身锁定30天的试用期。 
* 现在，该脚本将使用Powershell禁用CMD窗口中的快速编辑功能，而无需编辑注册表。感谢@abbodi1406提供的代码，以及@awuctl提出的想法。
* 用于通过conhost.exe重新启动脚本以避免终端应用程序的代码，现已合并到禁用快速编辑的代码中，感谢@abbodi1406。
来自 [WindowsAddict ](https://massgrave.dev/idm-activation-script)的更新完整代码
## v1.0
* 添加了代码，以便在脚本从终端应用程序运行时使用 conhost.exe 重新启动脚本。
* 修复了获取当前用户账户安全标识符（SID）时的一个问题。
## v0.9
* 修复了一个脚本在非管理员用户账户中无法激活和重置IDM的问题。
* 修复了一个脚本错误显示IDM已激活的问题。
* 修复了可能出现虚假序列号弹窗的问题。该脚本还将显示信息，以便在不使用重置选项的情况下再次运行激活选项。
* IDM注册表扫描和锁定代码现在用Powershell编写。
* 该脚本更新检查器代码已添加到脚本中。
* 该脚本现在将暂时禁用快速编辑模式，因为用户经常在脚本窗口内点击，这会使脚本暂停。
* 该脚本将在对CLSISD注册表项执行操作之前对其进行备份。
* 增加了许多错误检查，以便更好地识别问题。
## v0.8
* 将项目转移到 [Github](https://github.com/hanmaoye/IDM-Activation-Script)
* 小错误修复
* 添加信息以告知用户，当脚本删除大量空注册表项时，这些空注册表项正在被删除。

# 屏幕截图
![IAS](https://github.com/lstprjct/IDM-Activation-Script/assets/88411318/fafdb481-c497-464f-b1e6-9a4254eaf880)

![IAS_Freeze_Trial](https://github.com/lstprjct/IDM-Activation-Script/assets/88411318/76b36582-8cf4-4d1e-870f-6e8e57c80a87)

# 致谢

|                                             |                                                              |
| ------------------------------------------- | ------------------------------------------------------------ |
| Dukun Cabul                                 | 此IDM试用重置和激活逻辑的最初研究者，为这些方法制作了一款Autoit工具, [IDM-AIO_2020_Final](https://nsaneforums.com/topic/371047-discussion-internet-download-manager-fixes/page/8/#comment-1632062) |
| AveYo aka BAU                               | [reg_own lean and mean snippet](https://pastebin.com/XTPt0JSC) |
| [abbodi1406](https://github.com/abbodi1406) | 编码方面的帮助                                               |
| WindowsAddict                               | 最初的 [IAS](https://github.com/WindowsAddict/IDM-Activation-Script) 作者 |

感谢IAS的用户们的关注、反馈与协助。

------------------------------------------------------------------------

用爱制作 ❤️
