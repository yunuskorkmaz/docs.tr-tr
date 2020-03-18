---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77466000"
---

<span data-ttu-id="7287f-101">Paket yöneticisi beslemelerine eklenen paketler hacklenebilir bir biçimde adlandırılır: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="7287f-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="7287f-102">**Ürün**</span><span class="sxs-lookup"><span data-stu-id="7287f-102">**product**</span></span>\
<span data-ttu-id="7287f-103">Yüklenmesi gereken .NET ürün türü.</span><span class="sxs-lookup"><span data-stu-id="7287f-103">The type of .NET product to install.</span></span> <span data-ttu-id="7287f-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7287f-104">Valid options are:</span></span>

  - <span data-ttu-id="7287f-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="7287f-105">dotnet</span></span>
  - <span data-ttu-id="7287f-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="7287f-106">aspnetcore</span></span>

- <span data-ttu-id="7287f-107">**Türü**</span><span class="sxs-lookup"><span data-stu-id="7287f-107">**type**</span></span>\
<span data-ttu-id="7287f-108">SDK'yı veya çalışma saatini seçer.</span><span class="sxs-lookup"><span data-stu-id="7287f-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="7287f-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7287f-109">Valid options are:</span></span>

  - <span data-ttu-id="7287f-110">sdk</span><span class="sxs-lookup"><span data-stu-id="7287f-110">sdk</span></span>
  - <span data-ttu-id="7287f-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="7287f-111">runtime</span></span>

- <span data-ttu-id="7287f-112">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="7287f-112">**version**</span></span>\
<span data-ttu-id="7287f-113">SDK sürümü veya yüklemek için çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="7287f-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="7287f-114">Bu makalede, her zaman en son desteklenen sürümü için talimatlar verecektir.</span><span class="sxs-lookup"><span data-stu-id="7287f-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="7287f-115">Geçerli seçenekler, şu lar gibi serbest bırakılmış sürümlerdir:</span><span class="sxs-lookup"><span data-stu-id="7287f-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="7287f-116">3.1</span><span class="sxs-lookup"><span data-stu-id="7287f-116">3.1</span></span>
  - <span data-ttu-id="7287f-117">3,0</span><span class="sxs-lookup"><span data-stu-id="7287f-117">3.0</span></span>
  - <span data-ttu-id="7287f-118">2.1</span><span class="sxs-lookup"><span data-stu-id="7287f-118">2.1</span></span>

  <span data-ttu-id="7287f-119">İndirmeye çalıştığınız SDK/runtime'ın Linux dağıtımınız için kullanılamaması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="7287f-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="7287f-120">Desteklenen dağıtımların listesi için [bkz.](../dependencies.md?pivots=os-linux)</span><span class="sxs-lookup"><span data-stu-id="7287f-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="7287f-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7287f-121">Examples</span></span>

- <span data-ttu-id="7287f-122">Core 3.1 çalışma süresini ASP.NET yükleyin:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="7287f-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="7287f-123">.NET Core 2.1 çalışma süresini yükleyin:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="7287f-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="7287f-124">.NET Core 3.0 SDK'yı yükleyin:`dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="7287f-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="7287f-125">Paket eksik</span><span class="sxs-lookup"><span data-stu-id="7287f-125">Package missing</span></span>

<span data-ttu-id="7287f-126">Paket sürüm birleşimi çalışmıyorsa, kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="7287f-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="7287f-127">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK ile birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="7287f-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="7287f-128">Değer `aspnetcore-sdk-2.2` yanlıştır ve `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="7287f-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="7287f-129">.NET Core tarafından desteklenen Linux dağıtımlarının listesi [için](../dependencies.md?pivots=os-linux)bkz.</span><span class="sxs-lookup"><span data-stu-id="7287f-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
