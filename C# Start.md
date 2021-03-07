# C#/.NET开始编程

## 配置本地环境

### 下载并安装
从[此网页](https://dotnet.microsoft.com/download)下载 .NET  
根据你想要的版本，下载 .NET 5.0 或者 .NET 3.1，单击页面上的`Download .NET SDK x64`即可开始下载。更多版本可以单击下方的`All .NET downloads` 。  

下载完成后双击开始运行，等待其安装完成。

### 检查是否全部安装完成

打开一个 **新的** 命令行并且执行下面的指令。

```shell
dotnet
```

出现与下方所示相似的内容即为成功安装。
```
Usage: dotnet [options]
Usage: dotnet [path-to-application]

Options:
-h|--help         Display help.
--info            Display .NET information.
--list-sdks       Display the installed SDKs.
--list-runtimes   Display the installed runtimes.

path-to-application:
The path to an application .dll file to execute.
```

## 开始第一个App

### 创建一个初始化的应用程序

在命令提示符中，运行以下命令以创建新的应用程序

```shell
dotnet new console -o myApp
```
（此命令执行时间可能较长，请耐心等候）

然后你就可以进入这个目录
```shell
cd myApp
```

#### 这些命令是什么意思？
- 该dotnet new console命令为你创建一个新的控制台应用程序。
- 该-o参数创建一个名为的目录myApp，用于存储您的应用程序，并使用所需的文件填充该目录。
- 该命令cd myApp将当前目录更改为刚为新应用创建的目录。

文件myApp夹中的主文件是Program.cs。默认情况下，它已经包含了编写“Hello World！”输出到控制台所需的代码。

### 运行你的应用

在命令提示符中运行以下指令
```shell
dotnet run
```

略作等待后（这个等待可能比较长，请耐心），屏幕上会出现Hello World!的字符。  
此时你已经成功构建并运行了您的第一个.NET应用程序！

### 编辑代码并再次运行

用文本或代码编辑器（例如Sublime Text或者记事本）中打开`Program.cs`文件。该Program.cs文件位于新创建的myApp目录中。  

修改代码如下所示
```C#
using System;

namespace myApp
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
            Console.WriteLine("The current time is " + DateTime.Now);
        }
    }
}

```

保存`Program.cs`文件，然后再次运行
```shell
dotnet run
```

如果成功，您将看到类似于以下内容的输出
```
Hello World!
The current time is 11/10/2020 8:00:00 AM
```

## 开始第一个WebApp

### 创建一个初始化的应用程序

打开命令提示符，运行以下命令来创建您的应用程序
```shell
dotnet new webApp -o myWebApp --no-https
```

#### 这些命令是什么意思？

该dotnet new命令将创建一个新的应用程序。

- 该webApp参数选择创建应用程序时要使用的模板。
- 该-o参数将创建一个名为myWebApp您的应用程序存储位置的目录。
- 该--no-https标志指定不启用HTTPS。

#### 创建了什么文件？
在myWebApp目录中创建了几个文件，为您提供了一个可以运行的简单Web应用程序。

- Startup.cs 包含应用启动代码和中间件配置。
- 该myWebApp/Pages目录包含该应用程序的一些示例网页。
- myWebApp.csproj 定义引用了哪些库等。

### 运行此WebApp

在命令提示符下，运行以下命令
```shell
dotnet watch run
```

该命令将生成并启动该应用程序，然后在您更改代码时重新生成并重新启动该应用程序。  
您可以随时选择`Ctrl+C`来停止应用程序。（此命令运行时可能较为缓慢，请耐心等待）  
  
一段时间后，浏览器会自动打开`http://localhost:5000`网页  
至此，恭喜您已经构建并运行了您的第一个.NET Web应用程序！

### 编辑您的代码并再次运行

在文本编辑器中打开`Pages/Index.cshtml`，将所有代码替换为以下代码，然后保存文件。

```cshtml
@page
@model IndexModel
@{
    ViewData["Title"] = "Home page";
}

<div class="text-center">
    <h1>Hello, world!</h1>
    <p>The time on the server is @DateTime.Now</p>
</div>
```

一旦您保存了此文件，命令`dotnet watch run`会重启此应用程序并且在浏览器中刷新它，以便您可以在正在运行的应用程序中查看更改。