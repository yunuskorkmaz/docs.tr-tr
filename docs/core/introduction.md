---
title: .NET Core tanıtımı ve genel bakış
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 350fd50bee3403a05d1c19c9a692535613b17498
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538282"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="ff63d-104">NET Core’a giriş</span><span class="sxs-lookup"><span data-stu-id="ff63d-104">Introduction to .NET Core</span></span>

<span data-ttu-id="ff63d-105">[.NET Core](about.md) , [Açık kaynaklı](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="ff63d-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="ff63d-106">Windows, macOS ve Linux için, birden çok programlama dilini kullanarak x64, x, ARM32 ve ARM64 işlemcileri için .NET Core uygulamaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff63d-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="ff63d-107">Çerçeveler ve API 'Ler [bulut](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [istemci kullanıcı arabirimi](../desktop-wpf/overview/index.md)ve [makine öğrenimi](../machine-learning/index.yml)için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ff63d-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](../machine-learning/index.yml).</span></span>

<span data-ttu-id="ff63d-108">Makinenizde .NET Core 'u denemek için [.NET Core SDK indirin](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="ff63d-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="ff63d-109">En son sürüm [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)' dir.</span><span class="sxs-lookup"><span data-stu-id="ff63d-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="ff63d-110">.NET Core indirin</span><span class="sxs-lookup"><span data-stu-id="ff63d-110">Download .NET Core</span></span>

<span data-ttu-id="ff63d-111">Aşağıdaki yollarla .NET Core edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff63d-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="ff63d-112">Windows ve macOS yükleyicileri</span><span class="sxs-lookup"><span data-stu-id="ff63d-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="ff63d-113">Linux paketleri</span><span class="sxs-lookup"><span data-stu-id="ff63d-113">Linux packages</span></span>](./install/linux.md)
* [<span data-ttu-id="ff63d-114">Docker kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="ff63d-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="ff63d-115">ZIP 'ler ve tartopları</span><span class="sxs-lookup"><span data-stu-id="ff63d-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="ff63d-116">Betikleri yükler</span><span class="sxs-lookup"><span data-stu-id="ff63d-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="ff63d-117">Sürüm notları</span><span class="sxs-lookup"><span data-stu-id="ff63d-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="ff63d-118">İlk uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="ff63d-118">Create your first application</span></span>

<span data-ttu-id="ff63d-119">.NET Core SDK yükledikten sonra bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="ff63d-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="ff63d-120">Bir uygulamayı oluşturmak ve çalıştırmak için aşağıdaki komutları kullanın:</span><span class="sxs-lookup"><span data-stu-id="ff63d-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="ff63d-121">Aşağıdaki çıkışı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ff63d-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="ff63d-122">Katkıda Bulunun</span><span class="sxs-lookup"><span data-stu-id="ff63d-122">Contribute</span></span>

<span data-ttu-id="ff63d-123">.NET Core, açık bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="ff63d-123">.NET Core is an open platform.</span></span> <span data-ttu-id="ff63d-124">Herkese katılmak için hoş geldiniz.</span><span class="sxs-lookup"><span data-stu-id="ff63d-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="ff63d-125">[Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/61/index.html)'nda ürün sorunlarını ve soruları dosya.</span><span class="sxs-lookup"><span data-stu-id="ff63d-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="ff63d-126">Ürün katkıları [DotNet/Runtime](https://github.com/dotnet/runtime), [DotNet/SDK](https://github.com/dotnet/sdk), [DotNet/Rosyln](https://github.com/dotnet/roslyn)veya [aspnetcore](https://github.com/dotnet/aspnetcore)gibi proje depolarından birinde yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff63d-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="ff63d-127">Daha fazla bilgi için bkz. [.NET Core depoları](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span><span class="sxs-lookup"><span data-stu-id="ff63d-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="ff63d-128">Destek</span><span class="sxs-lookup"><span data-stu-id="ff63d-128">Support</span></span>

<span data-ttu-id="ff63d-129">.NET Core, Microsoft 'un Windows, macOS ve Linux 'ta ve Red Hat Enterprise Linux üzerinde Red Hat ile desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ff63d-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff63d-130">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ff63d-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ff63d-131">.NET Core öğreticileri</span><span class="sxs-lookup"><span data-stu-id="ff63d-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="ff63d-132">Tarayıcınızda .NET Core ' u deneyin</span><span class="sxs-lookup"><span data-stu-id="ff63d-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
