---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134100"
---

<span data-ttu-id="f5498-101">Paket yöneticisi beslemelerine eklenen paketler hacklenebilir bir biçimde adlandırılır: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="f5498-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="f5498-102">**Ürün**</span><span class="sxs-lookup"><span data-stu-id="f5498-102">**product**</span></span>\
<span data-ttu-id="f5498-103">Yüklenmesi gereken .NET ürün türü.</span><span class="sxs-lookup"><span data-stu-id="f5498-103">The type of .NET product to install.</span></span> <span data-ttu-id="f5498-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5498-104">Valid options are:</span></span>

  - <span data-ttu-id="f5498-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="f5498-105">dotnet</span></span>
  - <span data-ttu-id="f5498-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="f5498-106">aspnetcore</span></span>

- <span data-ttu-id="f5498-107">**Türü**</span><span class="sxs-lookup"><span data-stu-id="f5498-107">**type**</span></span>\
<span data-ttu-id="f5498-108">SDK'yı veya çalışma saatini seçer.</span><span class="sxs-lookup"><span data-stu-id="f5498-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="f5498-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5498-109">Valid options are:</span></span>

  - <span data-ttu-id="f5498-110">sdk</span><span class="sxs-lookup"><span data-stu-id="f5498-110">sdk</span></span>
  - <span data-ttu-id="f5498-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f5498-111">runtime</span></span>

- <span data-ttu-id="f5498-112">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="f5498-112">**version**</span></span>\
<span data-ttu-id="f5498-113">SDK sürümü veya yüklemek için çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="f5498-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="f5498-114">Bu makalede, her zaman en son desteklenen sürümü için talimatlar verecektir.</span><span class="sxs-lookup"><span data-stu-id="f5498-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="f5498-115">Geçerli seçenekler, şu lar gibi serbest bırakılmış sürümlerdir:</span><span class="sxs-lookup"><span data-stu-id="f5498-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="f5498-116">3.1</span><span class="sxs-lookup"><span data-stu-id="f5498-116">3.1</span></span>
  - <span data-ttu-id="f5498-117">3,0</span><span class="sxs-lookup"><span data-stu-id="f5498-117">3.0</span></span>
  - <span data-ttu-id="f5498-118">2.1</span><span class="sxs-lookup"><span data-stu-id="f5498-118">2.1</span></span>

  <span data-ttu-id="f5498-119">İndirmeye çalıştığınız SDK/runtime'ın Linux dağıtımınız için kullanılamaması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f5498-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="f5498-120">Desteklenen dağıtımların listesi için [bkz.](../dependencies.md?pivots=os-linux)</span><span class="sxs-lookup"><span data-stu-id="f5498-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="f5498-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f5498-121">Examples</span></span>

- <span data-ttu-id="f5498-122">Core 3.1 çalışma süresini ASP.NET yükleyin:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="f5498-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="f5498-123">.NET Core 2.1 çalışma süresini yükleyin:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="f5498-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="f5498-124">.NET Core 3.1 SDK'yı yükleyin:`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="f5498-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="f5498-125">Paket eksik</span><span class="sxs-lookup"><span data-stu-id="f5498-125">Package missing</span></span>

<span data-ttu-id="f5498-126">Paket sürüm birleşimi çalışmıyorsa, kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f5498-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="f5498-127">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK ile birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="f5498-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="f5498-128">Değer `aspnetcore-sdk-2.2` yanlıştır ve `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="f5498-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="f5498-129">.NET Core tarafından desteklenen Linux dağıtımlarının listesi [için](../dependencies.md?pivots=os-linux)bkz.</span><span class="sxs-lookup"><span data-stu-id="f5498-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
