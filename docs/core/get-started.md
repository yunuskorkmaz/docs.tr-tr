---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve Macos'ta .NET Core uygulamaları oluşturma hakkında bilgi edinmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: 3fff7884082c46477d37b08560a2c71e7ee345e5
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121260"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="96f5d-103">.NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="96f5d-103">Get started with .NET Core</span></span>

<span data-ttu-id="96f5d-104">Bu makalede .NET Core kullanmaya başlama hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="96f5d-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="96f5d-105">Windows, Linux ve Macos'ta .NET core yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="96f5d-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="96f5d-106">Sık kullandığınız metin düzenleyicinizde kod ve platformlar arası kitaplıklar ve uygulamalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="96f5d-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="96f5d-107">.NET Core nedir ve .NET teknolojilerden nasıl ilişkili olduğu emin değilseniz başlayın [.NET nedir](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) genel bakış.</span><span class="sxs-lookup"><span data-stu-id="96f5d-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="96f5d-108">Kısacası, .NET Core açık kaynaklı, platformlar arası .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="96f5d-108">Put simply, .NET Core is an open-source, cross-platform, implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="96f5d-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="96f5d-109">Create an application</span></span>

<span data-ttu-id="96f5d-110">İlk olarak, indirme ve yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/download/) bilgisayarınızda.</span><span class="sxs-lookup"><span data-stu-id="96f5d-110">First, download and install the [.NET Core SDK](https://www.microsoft.com/net/download/) on your computer.</span></span>

<span data-ttu-id="96f5d-111">Ardından, aşağıdaki gibi bir terminal açın **PowerShell**, **komut istemi**, veya **bash**.</span><span class="sxs-lookup"><span data-stu-id="96f5d-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="96f5d-112">Aşağıdaki komutu yazın `dotnet` oluşturma ve C# uygulama çalıştırma için komutları.</span><span class="sxs-lookup"><span data-stu-id="96f5d-112">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="96f5d-113">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="96f5d-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="96f5d-114">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="96f5d-114">Congratulations!</span></span> <span data-ttu-id="96f5d-115">Basit bir .NET Core uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="96f5d-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="96f5d-116">Ayrıca [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](tutorials/using-on-mac-vs.md) (.NET Core uygulaması oluşturmak için macOS yalnızca).</span><span class="sxs-lookup"><span data-stu-id="96f5d-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="96f5d-117">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="96f5d-117">Tutorials</span></span>

<span data-ttu-id="96f5d-118">Bu adım adım öğreticileri izleyerek .NET Core uygulamaları geliştirmeye başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96f5d-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="96f5d-119">Windows</span><span class="sxs-lookup"><span data-stu-id="96f5d-119">Windows</span></span>](#tab/windows)

* [<span data-ttu-id="96f5d-120">Visual Studio 2017'de .NET Core ile C# "Hello World" uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96f5d-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)

* [<span data-ttu-id="96f5d-121">Bir Visual Studio 2017'de .NET Core ile C# sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96f5d-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)

* [<span data-ttu-id="96f5d-122">Visual Studio 2017'de .NET Core ile bir Visual Basic "Hello World" uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96f5d-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)

* [<span data-ttu-id="96f5d-123">Visual Basic ve Visual Studio 2017'de .NET Core ile bir sınıf kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="96f5d-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  

* <span data-ttu-id="96f5d-124">Üzerinde bir video izleyin [yüklemek ve Visual Studio Code ve .NET Core kullanmak nasıl](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="96f5d-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>

* <span data-ttu-id="96f5d-125">Üzerinde bir video izleyin [yüklemek ve Visual Studio 2017 ve .NET Core kullanmak nasıl](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="96f5d-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>

* [<span data-ttu-id="96f5d-126">Komut satırını kullanarak .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="96f5d-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="96f5d-127">Bkz: [Önkoşullar için Windows geliştirme](windows-prerequisites.md) desteklenen Windows sürümlerinin bir listesi için makale.</span><span class="sxs-lookup"><span data-stu-id="96f5d-127">See the [Prerequisites for Windows development](windows-prerequisites.md) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="96f5d-128">Linux</span><span class="sxs-lookup"><span data-stu-id="96f5d-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="96f5d-129">Bu adım adım öğreticileri izleyerek .NET Core uygulaması geliştirmeye başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96f5d-129">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* [<span data-ttu-id="96f5d-130">Komut satırını kullanarak .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="96f5d-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* <span data-ttu-id="96f5d-131">Üzerinde bir video izleyin [Ubuntu üzerinde C# ve .NET Core kullanarak Visual Studio Code kullanmaya başlama](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="96f5d-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="96f5d-132">Bkz: [Linux geliştirme için Önkoşullar](linux-prerequisites.md) makale listesi için desteklenen Linux dağıtımları ve sürümleri.</span><span class="sxs-lookup"><span data-stu-id="96f5d-132">See the [Prerequisites for Linux development](linux-prerequisites.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="96f5d-133">macOS</span><span class="sxs-lookup"><span data-stu-id="96f5d-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="96f5d-134">Bu adım adım öğreticileri izleyerek .NET Core uygulaması geliştirmeye başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96f5d-134">You can get started developing .NET Core application by following these step-by-step tutorials.</span></span>

* <span data-ttu-id="96f5d-135">Üzerinde bir video izleyin [macOS üzerinde C# ve .NET Core kullanarak Visual Studio Code kullanmaya başlama](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="96f5d-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>

* [<span data-ttu-id="96f5d-136">Visual Studio Code kullanarak macOS üzerinde .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="96f5d-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)

* [<span data-ttu-id="96f5d-137">Komut satırını kullanarak .NET Core ile çalışmaya başlama.</span><span class="sxs-lookup"><span data-stu-id="96f5d-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

* [<span data-ttu-id="96f5d-138">Mac için Visual Studio kullanarak macos'ta .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="96f5d-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)

* [<span data-ttu-id="96f5d-139">Mac için Visual Studio kullanarak macos'ta eksiksiz bir .NET Core çözümü derleme</span><span class="sxs-lookup"><span data-stu-id="96f5d-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="96f5d-140">Bkz: [macOS geliştirme önkoşulları](macos-prerequisites.md) makale listesi için desteklenen işletim sistemi x / macOS sürümleri.</span><span class="sxs-lookup"><span data-stu-id="96f5d-140">See the [Prerequisites for macOS development](macos-prerequisites.md) article for a list of the supported OS X / macOS versions.</span></span>

***
