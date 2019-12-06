---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve macOS 'ta .NET Core uygulamaları oluşturmayı öğrenmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 89db6d79336c01315983133d9041904d88cba301
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884260"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="d53e8-103">.NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d53e8-103">Get started with .NET Core</span></span>

<span data-ttu-id="d53e8-104">Bu makalede, .NET Core ile çalışmaya başlama hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d53e8-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="d53e8-105">.NET Core, Windows, Linux ve macOS 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d53e8-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="d53e8-106">En sevdiğiniz metin düzenleyicinizde kod oluşturabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53e8-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="d53e8-107">.NET Core 'un ne olduğunu veya diğer .NET teknolojileriyle nasıl ilişkili olduğunu bilmiyorsanız, [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="d53e8-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="d53e8-108">.NET Core, .NET ' in açık kaynaklı ve platformlar arası bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d53e8-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="d53e8-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d53e8-109">Create an application</span></span>

<span data-ttu-id="d53e8-110">İlk olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) bilgisayarınıza indirip yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d53e8-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="d53e8-111">Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın.</span><span class="sxs-lookup"><span data-stu-id="d53e8-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="d53e8-112">Bir C# uygulama oluşturmak ve çalıştırmak için aşağıdaki `dotnet` komutlarını yazın:</span><span class="sxs-lookup"><span data-stu-id="d53e8-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="d53e8-113">Aşağıdaki çıkışı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="d53e8-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="d53e8-114">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="d53e8-114">Congratulations!</span></span> <span data-ttu-id="d53e8-115">Basit bir .NET Core uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="d53e8-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="d53e8-116">.NET Core uygulaması oluşturmak için [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](tutorials/using-on-mac-vs.md) (yalnızca MacOS) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53e8-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="d53e8-117">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="d53e8-117">Tutorials</span></span>

<span data-ttu-id="d53e8-118">Bu adım adım öğreticilerini izleyerek .NET Core uygulamaları geliştirmeye başlamanızı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d53e8-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="d53e8-119">Windows</span><span class="sxs-lookup"><span data-stu-id="d53e8-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="d53e8-120">Visual Studio C# 2017 ' de .NET Core ile bir "Merhaba Dünya" uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d53e8-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="d53e8-121">Visual Studio C# 2017 ' de .NET Core ile bir sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d53e8-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="d53e8-122">Visual Studio 2017 ' de .NET Core ile bir Visual Basic "Merhaba Dünya" uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d53e8-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)
- [<span data-ttu-id="d53e8-123">Visual Studio 2017 ' de Visual Basic ve .NET Core ile bir sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d53e8-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  
- <span data-ttu-id="d53e8-124">[Visual Studio Code ve .NET Core 'u yüklemek ve kullanmak için](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="d53e8-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>
- <span data-ttu-id="d53e8-125">[Visual Studio 2017 ve .NET Core 'u yüklemek ve kullanmak için](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="d53e8-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>
- [<span data-ttu-id="d53e8-126">Komut satırını kullanarak .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="d53e8-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)

<span data-ttu-id="d53e8-127">Desteklenen Windows sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) makalesi.</span><span class="sxs-lookup"><span data-stu-id="d53e8-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="d53e8-128">Linux</span><span class="sxs-lookup"><span data-stu-id="d53e8-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="d53e8-129">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulaması geliştirmeye başlamanızı sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d53e8-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="d53e8-130">Komut satırını kullanarak .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="d53e8-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)
- <span data-ttu-id="d53e8-131">[Ubuntu 'da ve .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)kullanmaya başlama hakkında bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="d53e8-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="d53e8-132">Desteklenen Linux desteklerinin ve sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve gereksinimler](install/dependencies.md?tabs=netcore30&pivots=os-linux) makalesi.</span><span class="sxs-lookup"><span data-stu-id="d53e8-132">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="d53e8-133">macOS</span><span class="sxs-lookup"><span data-stu-id="d53e8-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="d53e8-134">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulaması geliştirmeye başlamanızı sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d53e8-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- <span data-ttu-id="d53e8-135">[MacOS 'ta .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)kullanmaya başlama hakkında bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="d53e8-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>
- [<span data-ttu-id="d53e8-136">Visual Studio Code kullanarak macOS 'ta .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="d53e8-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)
- [<span data-ttu-id="d53e8-137">Komut satırını kullanarak .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="d53e8-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)
- [<span data-ttu-id="d53e8-138">Mac için Visual Studio kullanarak macOS 'ta .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="d53e8-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="d53e8-139">Mac için Visual Studio kullanarak macOS 'ta kapsamlı bir .NET Core çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d53e8-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="d53e8-140">Desteklenen OS X/macOS sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) makalesi.</span><span class="sxs-lookup"><span data-stu-id="d53e8-140">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
