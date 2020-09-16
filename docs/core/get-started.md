---
title: .NET Core ile çalışmaya başlama
description: Windows, Linux ve macOS 'ta .NET Core uygulamaları oluşturmayı öğrenmek için kaynakları bulun.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 6106f66dfbbe382ee9f61eb8b7bda70ab9b72d0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538557"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="c86e4-103">.NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="c86e4-103">Get started with .NET Core</span></span>

<span data-ttu-id="c86e4-104">Bu makalede, .NET Core ile çalışmaya başlama hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c86e4-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="c86e4-105">.NET Core, Windows, Linux ve macOS 'a yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c86e4-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="c86e4-106">En sevdiğiniz metin düzenleyicinizde kod oluşturabilir ve platformlar arası kitaplıklar ve uygulamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c86e4-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="c86e4-107">.NET Core 'un ne olduğu veya diğer .NET teknolojileriyle nasıl ilişkili olduğu konusunda emin değilseniz, [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) genel bakış ile başlayın.</span><span class="sxs-lookup"><span data-stu-id="c86e4-107">If you're unsure what .NET Core is or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="c86e4-108">.NET Core, .NET ' in açık kaynaklı ve platformlar arası bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c86e4-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="c86e4-109">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-109">Create an application</span></span>

<span data-ttu-id="c86e4-110">İlk olarak, [.NET Core SDK](https://dotnet.microsoft.com/download) bilgisayarınıza indirip yükleyin.</span><span class="sxs-lookup"><span data-stu-id="c86e4-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="c86e4-111">Ardından, **PowerShell**, **komut istemi**veya **Bash**gibi bir Terminal açın.</span><span class="sxs-lookup"><span data-stu-id="c86e4-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="c86e4-112">`dotnet`Bir C# uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:</span><span class="sxs-lookup"><span data-stu-id="c86e4-112">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="c86e4-113">Aşağıdaki çıkışı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="c86e4-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="c86e4-114">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="c86e4-114">Congratulations!</span></span> <span data-ttu-id="c86e4-115">Basit bir .NET Core uygulaması oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="c86e4-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="c86e4-116">.NET Core uygulaması oluşturmak için [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (yalnızca Windows) veya [Mac için Visual Studio](tutorials/with-visual-studio-mac.md) (yalnızca MacOS) de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c86e4-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="c86e4-117">Öğreticiler</span><span class="sxs-lookup"><span data-stu-id="c86e4-117">Tutorials</span></span>

<span data-ttu-id="c86e4-118">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:</span><span class="sxs-lookup"><span data-stu-id="c86e4-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="c86e4-119">Windows</span><span class="sxs-lookup"><span data-stu-id="c86e4-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="c86e4-120">Visual Studio 2019 ' de ilk .NET Core konsol uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="c86e4-121">Visual Studio 'da .NET Standard bir sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="c86e4-122">Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-122">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="c86e4-123">![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="c86e4-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="c86e4-124">[Visual Studio Code ve .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) videosunu Kanal 9 ' da nasıl yükleyip kullanacağınızı izleyin.</span><span class="sxs-lookup"><span data-stu-id="c86e4-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="c86e4-125">![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="c86e4-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="c86e4-126">YouTube 'daki [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videolarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="c86e4-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="c86e4-127">Desteklenen Windows sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](./install/windows.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="c86e4-127">See the [.NET Core dependencies and requirements](./install/windows.md) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="c86e4-128">Linux</span><span class="sxs-lookup"><span data-stu-id="c86e4-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="c86e4-129">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:</span><span class="sxs-lookup"><span data-stu-id="c86e4-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="c86e4-130">Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-130">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="c86e4-131">![video için film kamerası simgesi](./media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="c86e4-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="c86e4-132">[Ubuntu 'Da C# ve .NET Core kullanarak Visual Studio Code kullanmaya başlama](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)hakkında bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="c86e4-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="c86e4-133">Desteklenen Linux desteklerinin ve sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve gereksinimler](./install/linux.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="c86e4-133">See the [.NET Core dependencies and requirements](./install/linux.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="c86e4-134">macOS</span><span class="sxs-lookup"><span data-stu-id="c86e4-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="c86e4-135">Aşağıdaki adım adım öğreticilerden yararlanarak .NET Core uygulamaları geliştirmeye başlayın:</span><span class="sxs-lookup"><span data-stu-id="c86e4-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="c86e4-136">Öğretici: Visual Studio Code kullanarak bir .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-136">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)
- [<span data-ttu-id="c86e4-137">Öğretici: Mac için Visual Studio kullanarak bir .NET Core konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-137">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>](tutorials/with-visual-studio-mac.md)
- [<span data-ttu-id="c86e4-138">Mac için Visual Studio kullanarak macOS 'ta .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c86e4-138">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="c86e4-139">![video için film kamerası simgesi](media/video-icon.png "Nasıl yapılacağını görmek için")</span><span class="sxs-lookup"><span data-stu-id="c86e4-139">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="c86e4-140">[MacOS 'Ta C# ve .NET Core kullanarak Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)kullanmaya başlama hakkında bir video izleyin.</span><span class="sxs-lookup"><span data-stu-id="c86e4-140">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="c86e4-141">Desteklenen OS X/macOS sürümlerinin bir listesi için bkz. [.NET Core Dependencies ve Requirements](./install/macos.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="c86e4-141">See the [.NET Core dependencies and requirements](./install/macos.md) article for a list of the supported OS X / macOS versions.</span></span>

---
