---
title: .NET Core giriş ve genel bakış
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmak için .NET'in modüler, yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a20cdda5cbd366d04e7ee9e8df3d1b15d10c1f4a
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391162"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="2d4a1-104">NET Core’a giriş</span><span class="sxs-lookup"><span data-stu-id="2d4a1-104">Introduction to .NET Core</span></span>

<span data-ttu-id="2d4a1-105">[.NET Core](about.md) [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="2d4a1-106">Birden çok programlama dilini kullanarak x64, x86, ARM32 ve ARM64 işlemcileri için Windows, macOS ve Linux için .NET Core uygulamaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="2d4a1-107">Çerçeveler ve API'ler [bulut,](/aspnet/core/) [IoT,](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) [istemci UI](/dotnet/desktop-wpf/overview/index)ve [makine öğrenimi](/dotnet/machine-learning/)için sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](/dotnet/desktop-wpf/overview/index), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="2d4a1-108">.NET Core'u makinenizde denemek için [.NET Core SDK'yı indirin.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="2d4a1-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="2d4a1-109">En son sürümü [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="2d4a1-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="2d4a1-110">Karşıdan yükleme .NET Core</span><span class="sxs-lookup"><span data-stu-id="2d4a1-110">Download .NET Core</span></span>

<span data-ttu-id="2d4a1-111">.NET Core'u aşağıdaki yollarla alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2d4a1-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="2d4a1-112">Windows ve macOS için yükleyiciler</span><span class="sxs-lookup"><span data-stu-id="2d4a1-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="2d4a1-113">Linux paketleri</span><span class="sxs-lookup"><span data-stu-id="2d4a1-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="2d4a1-114">Docker kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="2d4a1-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="2d4a1-115">Fermuarlar ve katran topları</span><span class="sxs-lookup"><span data-stu-id="2d4a1-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="2d4a1-116">Komut dosyalarını yükleme</span><span class="sxs-lookup"><span data-stu-id="2d4a1-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="2d4a1-117">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="2d4a1-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="2d4a1-118">İlk uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="2d4a1-118">Create your first application</span></span>

<span data-ttu-id="2d4a1-119">.NET Core SDK'yı yükledikten sonra bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="2d4a1-120">Bir uygulama oluşturmak ve çalıştırmak için aşağıdaki komutları kullanın:</span><span class="sxs-lookup"><span data-stu-id="2d4a1-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="2d4a1-121">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="2d4a1-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="2d4a1-122">Katkıda Bulun</span><span class="sxs-lookup"><span data-stu-id="2d4a1-122">Contribute</span></span>

<span data-ttu-id="2d4a1-123">.NET Core açık bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-123">.NET Core is an open platform.</span></span> <span data-ttu-id="2d4a1-124">Herkes katılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="2d4a1-125">[Geliştirici Topluluğu'nda](https://developercommunity.visualstudio.com/spaces/61/index.html)ürün sorunlarını ve sorularını dosyalayın.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="2d4a1-126">Ürün katkıları, proje depolarından birinde yapılmalıdır, örneğin [dotnet/runtime,](https://github.com/dotnet/runtime) [dotnet/sdk,](https://github.com/dotnet/sdk) [dotnet/rosyln](https://github.com/dotnet/roslyn)veya [aspnetcore.](https://github.com/dotnet/aspnetcore)</span><span class="sxs-lookup"><span data-stu-id="2d4a1-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="2d4a1-127">Daha fazla bilgi için [bkz.](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)</span><span class="sxs-lookup"><span data-stu-id="2d4a1-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="2d4a1-128">Destek</span><span class="sxs-lookup"><span data-stu-id="2d4a1-128">Support</span></span>

<span data-ttu-id="2d4a1-129">.NET Core, Windows, macOS ve Linux'ta Microsoft tarafından ve Red Hat Enterprise Linux'ta Red Hat tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2d4a1-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2d4a1-130">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2d4a1-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d4a1-131">.NET Çekirdek eğitimleri</span><span class="sxs-lookup"><span data-stu-id="2d4a1-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="2d4a1-132">Tarayıcınızda .NET Core'u deneyin</span><span class="sxs-lookup"><span data-stu-id="2d4a1-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
