---
title: .NET Core kılavuzu
description: .NET Core, Windows, Linux ve macOS uygulamaları oluşturmak için .NET'in modüler, yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75740749"
---
# <a name="net-core-guide"></a><span data-ttu-id="751f6-104">.NET Core kılavuzu</span><span class="sxs-lookup"><span data-stu-id="751f6-104">.NET Core guide</span></span>

<span data-ttu-id="751f6-105">[.NET Core,](about.md) Microsoft ve [GitHub'daki](https://github.com/dotnet/core).NET topluluğu tarafından korunan [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="751f6-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="751f6-106">Bu çapraz platform (Windows, macOS ve Linux destekleyen) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="751f6-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="751f6-107">Özellikleri, desteklenen dilleri ve çerçeveleri ve önemli API'leri de dahil olmak üzere .NET Core hakkında daha fazla bilgi edinmek için [.NET Core](about.md) hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="751f6-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="751f6-108">Basit bir .NET Core uygulaması nın nasıl oluşturulacağımı öğrenmek için [.NET Core Eğitimlerine](tutorials/index.md) göz atın.</span><span class="sxs-lookup"><span data-stu-id="751f6-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="751f6-109">İlk uygulamanızı çalışır hale getirmek yalnızca birkaç dakika nızı alır.</span><span class="sxs-lookup"><span data-stu-id="751f6-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="751f6-110">Tarayıcınızda .NET Core'u denemek istiyorsanız, [C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online öğreticideki Sayılar'a bakın.</span><span class="sxs-lookup"><span data-stu-id="751f6-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="751f6-111">Karşıdan yükleme .NET Core</span><span class="sxs-lookup"><span data-stu-id="751f6-111">Download .NET Core</span></span>

<span data-ttu-id="751f6-112">Windows, macOS veya Linux makinenizde .NET Core'u denemek için [.NET Core SDK'yı](https://www.microsoft.com/net/download) indirin.</span><span class="sxs-lookup"><span data-stu-id="751f6-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="751f6-113">Docker konteynerlerini kullanmayı tercih ederseniz [,NET Core Docker Hub'ı](https://hub.docker.com/_/microsoft-dotnet-core/)ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="751f6-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="751f6-114">Başka bir .NET Core sürümü arıyorsanız tüm .NET Core sürümleri [.NET Core İndirme sürümlerinde](https://dotnet.microsoft.com/download/dotnet-core) mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="751f6-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="751f6-115">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="751f6-115">.NET Core 3.1</span></span>

<span data-ttu-id="751f6-116">En son sürümü .NET Core 3.1 olduğunu.</span><span class="sxs-lookup"><span data-stu-id="751f6-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="751f6-117">3.1 .NET Core 3.0 üzerinde küçük iyileştirmeler içerir, ancak, .NET Core 3.1 [uzun vadeli desteklenen bir sürümdür.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="751f6-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="751f6-118">.NET Core 3.1 sürümü hakkında daha fazla bilgi için [.NET Core 3.1'deki yeniliklere](./whats-new/dotnet-core-3-1.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="751f6-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="751f6-119">İlk uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="751f6-119">Create your first application</span></span>

<span data-ttu-id="751f6-120">.NET Core SDK'yı yükledikten sonra bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="751f6-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="751f6-121">C# `dotnet` uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:</span><span class="sxs-lookup"><span data-stu-id="751f6-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="751f6-122">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="751f6-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="751f6-123">Destek</span><span class="sxs-lookup"><span data-stu-id="751f6-123">Support</span></span>

<span data-ttu-id="751f6-124">.NET Core, Windows, macOS ve Linux'ta [Microsoft tarafından desteklenir.](https://dotnet.microsoft.com/platform/support/policy)</span><span class="sxs-lookup"><span data-stu-id="751f6-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="751f6-125">Genellikle aylık olarak yılda birkaç kez güvenlik ve kalite için güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="751f6-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="751f6-126">.NET Core ikili dağıtımları, Azure'da Microsoft tarafından korunan sunucularda oluşturulur ve test edilir ve tıpkı herhangi bir Microsoft ürünü gibi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="751f6-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="751f6-127">Red Hat, Red Hat Enterprise Linux (RHEL) üzerinde [.NET Core'u destekler.](http://redhatloves.net/)</span><span class="sxs-lookup"><span data-stu-id="751f6-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="751f6-128">Red Hat kaynaktan .NET Core oluşturur ve [Red Hat Yazılım Koleksiyonları'nda](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="751f6-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="751f6-129">Red Hat ve Microsoft, .NET Core'un RHEL'de iyi çalışmasını sağlamak için işbirliği içindedir.</span><span class="sxs-lookup"><span data-stu-id="751f6-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
