---
title: .NET Core giriş ve genel bakış
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmak için .NET'in modüler, yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351703"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="78105-104">.NET Core'a Giriş</span><span class="sxs-lookup"><span data-stu-id="78105-104">Introduction to .NET Core</span></span>

<span data-ttu-id="78105-105">[.NET Core,](about.md) Microsoft ve [GitHub'daki](https://github.com/dotnet/core).NET topluluğu tarafından korunan [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="78105-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="78105-106">Bu çapraz platform (Windows, macOS ve Linux destekleyen) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78105-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="78105-107">Karşıdan yükleme .NET Core</span><span class="sxs-lookup"><span data-stu-id="78105-107">Download .NET Core</span></span>

<span data-ttu-id="78105-108">Windows, macOS veya Linux makinenizde .NET Core'u denemek için [.NET Core SDK'yı](https://dotnet.microsoft.com/download) indirin.</span><span class="sxs-lookup"><span data-stu-id="78105-108">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="78105-109">Docker kapsayıcılarını kullanmayı tercih [ediyorsanız,.NET Core Docker Hub'ı](https://hub.docker.com/_/microsoft-dotnet-core/)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="78105-109">If you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

## <a name="net-core-31"></a><span data-ttu-id="78105-110">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="78105-110">.NET Core 3.1</span></span>

<span data-ttu-id="78105-111">En son sürümü .NET Core 3.1 olduğunu.</span><span class="sxs-lookup"><span data-stu-id="78105-111">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="78105-112">3.1 .NET Core 3.0 üzerinde küçük iyileştirmeler içerir, ancak, .NET Core 3.1 [uzun vadeli desteklenen bir sürümdür.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="78105-112">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="78105-113">.NET Core 3.1 sürümü hakkında daha fazla bilgi için [.NET Core 3.1'deki yeniliklere](./whats-new/dotnet-core-3-1.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="78105-113">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

<span data-ttu-id="78105-114">.NET Core'un başka bir sürümünü arıyorsanız, tüm [sürümlere .NET Core indirmelerinde](https://dotnet.microsoft.com/download/dotnet-core)ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78105-114">If you're looking for another version of .NET Core, all the versions are available at [.NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="78105-115">İlk uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="78105-115">Create your first application</span></span>

<span data-ttu-id="78105-116">.NET Core SDK'yı yükledikten sonra bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="78105-116">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="78105-117">C# `dotnet` uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:</span><span class="sxs-lookup"><span data-stu-id="78105-117">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="78105-118">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="78105-118">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="78105-119">Destek</span><span class="sxs-lookup"><span data-stu-id="78105-119">Support</span></span>

<span data-ttu-id="78105-120">.NET Core, Windows, macOS ve Linux'ta [Microsoft tarafından desteklenir.](https://dotnet.microsoft.com/platform/support/policy)</span><span class="sxs-lookup"><span data-stu-id="78105-120">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy) on Windows, macOS, and Linux.</span></span> <span data-ttu-id="78105-121">Genellikle aylık olarak yılda birkaç kez güvenlik ve kalite için güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="78105-121">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="78105-122">.NET Core ikili dağıtımları, Azure'da Microsoft tarafından korunan sunucularda oluşturulur ve test edilir ve tıpkı herhangi bir Microsoft ürünü gibi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="78105-122">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="78105-123">Red Hat, Red Hat Enterprise Linux (RHEL) üzerinde [.NET Core'u destekler.](http://redhatloves.net/)</span><span class="sxs-lookup"><span data-stu-id="78105-123">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="78105-124">Red Hat kaynaktan .NET Core oluşturur ve [Red Hat Yazılım Koleksiyonları'nda](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="78105-124">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="78105-125">Red Hat ve Microsoft, .NET Core'un RHEL'de iyi çalışmasını sağlamak için işbirliği içindedir.</span><span class="sxs-lookup"><span data-stu-id="78105-125">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

## <a name="next-steps"></a><span data-ttu-id="78105-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="78105-126">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78105-127">.NET Çekirdek eğitimleri</span><span class="sxs-lookup"><span data-stu-id="78105-127">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="78105-128">Tarayıcınızda .NET Core'u deneyin</span><span class="sxs-lookup"><span data-stu-id="78105-128">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
