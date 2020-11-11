---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506884"
---

<span data-ttu-id="83e71-101">Paket Yöneticisi akışlarına eklenen paketler, uyumlu olmayan biçimde adlandırılır: `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="83e71-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="83e71-102">**ürünüyle**</span><span class="sxs-lookup"><span data-stu-id="83e71-102">**product**</span></span>\
<span data-ttu-id="83e71-103">Yüklenecek .NET Ürün türü.</span><span class="sxs-lookup"><span data-stu-id="83e71-103">The type of .NET product to install.</span></span> <span data-ttu-id="83e71-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83e71-104">Valid options are:</span></span>

  - <span data-ttu-id="83e71-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="83e71-105">dotnet</span></span>
  - <span data-ttu-id="83e71-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="83e71-106">aspnetcore</span></span>

- <span data-ttu-id="83e71-107">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="83e71-107">**type**</span></span>\
<span data-ttu-id="83e71-108">SDK 'Yı veya çalışma zamanını seçer.</span><span class="sxs-lookup"><span data-stu-id="83e71-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="83e71-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="83e71-109">Valid options are:</span></span>

  - <span data-ttu-id="83e71-110">sdk</span><span class="sxs-lookup"><span data-stu-id="83e71-110">sdk</span></span>
  - <span data-ttu-id="83e71-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="83e71-111">runtime</span></span>

- <span data-ttu-id="83e71-112">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="83e71-112">**version**</span></span>\
<span data-ttu-id="83e71-113">Yüklenecek SDK veya çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="83e71-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="83e71-114">Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="83e71-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="83e71-115">Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:</span><span class="sxs-lookup"><span data-stu-id="83e71-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="83e71-116">5.0</span><span class="sxs-lookup"><span data-stu-id="83e71-116">5.0</span></span>
  - <span data-ttu-id="83e71-117">3,1</span><span class="sxs-lookup"><span data-stu-id="83e71-117">3.1</span></span>
  - <span data-ttu-id="83e71-118">3,0</span><span class="sxs-lookup"><span data-stu-id="83e71-118">3.0</span></span>
  - <span data-ttu-id="83e71-119">2.1</span><span class="sxs-lookup"><span data-stu-id="83e71-119">2.1</span></span>

  <span data-ttu-id="83e71-120">İndirmeyi denediğiniz SDK/çalışma zamanı Linux dağıtım için kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="83e71-120">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="83e71-121">Desteklenen dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="83e71-121">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="83e71-122">Örnekler</span><span class="sxs-lookup"><span data-stu-id="83e71-122">Examples</span></span>

- <span data-ttu-id="83e71-123">ASP.NET Core 5,0 çalışma zamanını yükler: `aspnetcore-runtime-5.0`</span><span class="sxs-lookup"><span data-stu-id="83e71-123">Install the ASP.NET Core 5.0 runtime: `aspnetcore-runtime-5.0`</span></span>
- <span data-ttu-id="83e71-124">.NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="83e71-124">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="83e71-125">.NET 5,0 SDK 'sını yükler: `dotnet-sdk-5.0`</span><span class="sxs-lookup"><span data-stu-id="83e71-125">Install the .NET 5.0 SDK: `dotnet-sdk-5.0`</span></span>
- <span data-ttu-id="83e71-126">.NET Core 3,1 SDK 'sını yükler: `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="83e71-126">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="83e71-127">Paket eksik</span><span class="sxs-lookup"><span data-stu-id="83e71-127">Package missing</span></span>

<span data-ttu-id="83e71-128">Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="83e71-128">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="83e71-129">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET SDK 'ya dahildir.</span><span class="sxs-lookup"><span data-stu-id="83e71-129">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET SDK.</span></span> <span data-ttu-id="83e71-130">Değer `aspnetcore-sdk-2.2` yanlış ve olmalıdır `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="83e71-130">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="83e71-131">.NET Core tarafından desteklenen Linux dağıtımların listesi için bkz. [.net bağımlılıkları ve gereksinimleri](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="83e71-131">For a list of Linux distributions supported by .NET Core, see [.NET dependencies and requirements](../linux.md).</span></span>
