---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve macOS 'ta .NET Core uygulamaları oluşturmayı öğrenmek için kaynakları bulun.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714390"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="6e3c3-103">.NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6e3c3-103">Get started with .NET Core</span></span>

<span data-ttu-id="6e3c3-104">Bu makalede, .NET Core ile çalışmaya başlama hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="6e3c3-105">.NET Core, Windows, Linux ve macOS 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="6e3c3-106">En sevdiğiniz metin düzenleyicinizde kod oluşturabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="6e3c3-107">.NET Core 'un ne olduğunu veya diğer .NET teknolojileriyle nasıl ilişkili olduğunu bilmiyorsanız, [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="6e3c3-108">.NET Core, .NET ' in açık kaynaklı ve platformlar arası bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="6e3c3-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e3c3-109">Create an application</span></span>

<span data-ttu-id="6e3c3-110">İlk olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) bilgisayarınıza indirip yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="6e3c3-111">Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="6e3c3-112">Bir C# uygulama oluşturmak ve çalıştırmak için aşağıdaki `dotnet` komutlarını yazın:</span><span class="sxs-lookup"><span data-stu-id="6e3c3-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="6e3c3-113">Aşağıdaki çıkışı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6e3c3-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="6e3c3-114">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="6e3c3-114">Congratulations!</span></span> <span data-ttu-id="6e3c3-115">Basit bir .NET Core uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="6e3c3-116">.NET Core uygulaması oluşturmak için [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](./tutorials/using-on-mac-vs.md) (yalnızca MacOS) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="6e3c3-117">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="6e3c3-117">Tutorials</span></span>

<span data-ttu-id="6e3c3-118">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:</span><span class="sxs-lookup"><span data-stu-id="6e3c3-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="6e3c3-119">Windows</span><span class="sxs-lookup"><span data-stu-id="6e3c3-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="6e3c3-120">Visual Studio 2019 ' de ilk .NET Core konsol uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e3c3-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="6e3c3-121">Visual Studio 'da .NET Standard bir sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e3c3-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="6e3c3-122">.NET Core CLI kullanarak .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6e3c3-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="6e3c3-123">![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="6e3c3-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="6e3c3-124">[Visual Studio Code ve .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) videosunu Kanal 9 ' da nasıl yükleyip kullanacağınızı izleyin.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="6e3c3-125">![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="6e3c3-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="6e3c3-126">YouTube 'daki [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videolarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="6e3c3-127">Desteklenen Windows sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?pivots=os-windows) makalesi.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="6e3c3-128">Linux</span><span class="sxs-lookup"><span data-stu-id="6e3c3-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="6e3c3-129">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:</span><span class="sxs-lookup"><span data-stu-id="6e3c3-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="6e3c3-130">Komut satırını kullanarak .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6e3c3-130">Get started with .NET Core using the command line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="6e3c3-131">![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="6e3c3-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="6e3c3-132">[Ubuntu 'da ve .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)kullanmaya başlama hakkında bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="6e3c3-133">Desteklenen Linux desteklerinin ve sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve gereksinimler](install/dependencies.md?pivots=os-linux) makalesi.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="6e3c3-134">macOS</span><span class="sxs-lookup"><span data-stu-id="6e3c3-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="6e3c3-135">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:</span><span class="sxs-lookup"><span data-stu-id="6e3c3-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="6e3c3-136">Visual Studio Code kullanarak macOS 'ta .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6e3c3-136">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="6e3c3-137">Komut satırını kullanarak .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6e3c3-137">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="6e3c3-138">Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6e3c3-138">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="6e3c3-139">Mac için Visual Studio kullanarak macOS 'ta kapsamlı bir .NET Core çözümü oluşturun</span><span class="sxs-lookup"><span data-stu-id="6e3c3-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="6e3c3-140">![video için film kamerası simgesi](media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="6e3c3-140">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="6e3c3-141">[MacOS 'ta .NET Core 'u kullanarak C# Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)kullanmaya başlama hakkında bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-141">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="6e3c3-142">Desteklenen OS X/macOS sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](install/dependencies.md?pivots=os-macos) makalesi.</span><span class="sxs-lookup"><span data-stu-id="6e3c3-142">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
