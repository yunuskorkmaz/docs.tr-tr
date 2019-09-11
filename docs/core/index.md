---
title: .NET Core Kılavuzu
description: .NET Core, Windows, Linux ve Mac uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 0007c1c6a9939c46f123535f9053ac1d4ced7266
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848937"
---
# <a name="net-core-guide"></a><span data-ttu-id="55762-104">.NET Core Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="55762-104">.NET Core Guide</span></span>

<span data-ttu-id="55762-105">[.NET Core](about.md) , [GitHub](https://github.com/dotnet/core)'da Microsoft ve .net Community tarafından sürdürülen [Açık kaynaklı](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="55762-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="55762-106">Platformlar arası bir platformdur (Windows, macOS ve Linux 'u destekleme) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55762-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="55762-107">.NET Core hakkında özellikler, desteklenen diller ve çerçeveler ve anahtar API 'Leri dahil olmak üzere .NET Core hakkında daha fazla bilgi için bkz. [.NET Core hakkında](about.md) .</span><span class="sxs-lookup"><span data-stu-id="55762-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="55762-108">[.NET Core öğreticilerine](tutorials/index.md) göz atın ve basit bir .NET Core uygulaması oluşturma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="55762-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="55762-109">İlk uygulamanızı çalışır duruma getirmek için yalnızca birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="55762-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="55762-110">Tarayıcınızda .NET Core 'u denemek istiyorsanız çevrimiçi öğreticideki [numaralara C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) bakın.</span><span class="sxs-lookup"><span data-stu-id="55762-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="55762-111">.NET Core 2,2 'yi indirin</span><span class="sxs-lookup"><span data-stu-id="55762-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="55762-112">Windows, macOS veya Linux makinenizde .NET Core 'u denemek için [.net core 2,2 SDK 'sını](https://dotnet.microsoft.com/download) indirin.</span><span class="sxs-lookup"><span data-stu-id="55762-112">Download the [.NET Core  2.2 SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="55762-113">Docker Kapsayıcıları kullanmayı tercih ediyorsanız [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) adresini ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="55762-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="55762-114">Başka bir .NET Core sürümü arıyorsanız, tüm .NET Core sürümleri [.NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core) ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55762-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="55762-115">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="55762-115">.NET Core 2.2</span></span>

<span data-ttu-id="55762-116">En son sürüm [.NET Core 2,2](whats-new/dotnet-core-2-2.md)' dir.</span><span class="sxs-lookup"><span data-stu-id="55762-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="55762-117">Yeni özellikler şunlardır: çerçeveye bağımlı dağıtımlar, başlangıç kancaları, Azure SQL ile AAD kimlik doğrulaması ve Windows ARM32 desteği.</span><span class="sxs-lookup"><span data-stu-id="55762-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="55762-118">İlk uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="55762-118">Create your first application</span></span>

<span data-ttu-id="55762-119">.NET Core SDK yükledikten sonra bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="55762-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="55762-120">Bir C# uygulama oluşturmak `dotnet` ve çalıştırmak için aşağıdaki komutları yazın.</span><span class="sxs-lookup"><span data-stu-id="55762-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="55762-121">Aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="55762-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="55762-122">Destek</span><span class="sxs-lookup"><span data-stu-id="55762-122">Support</span></span>

<span data-ttu-id="55762-123">.NET Core, Windows, macOS ve Linux 'ta [Microsoft tarafından desteklenir](https://dotnet.microsoft.com/platform/support/policy).</span><span class="sxs-lookup"><span data-stu-id="55762-123">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="55762-124">Genellikle ayda bir yılda birkaç kez güvenlik ve kalite için güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="55762-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="55762-125">.NET Core ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve tıpkı tüm Microsoft ürünleri gibi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="55762-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="55762-126">[Red Hat](http://redhatloves.net/) Red Hat Enterprise Linux (RHEL) üzerinde .NET Core 'u destekler.</span><span class="sxs-lookup"><span data-stu-id="55762-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="55762-127">Red hat, kaynaktan .NET Core 'u oluşturur ve [Red Hat yazılım koleksiyonlarında](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="55762-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="55762-128">Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="55762-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
