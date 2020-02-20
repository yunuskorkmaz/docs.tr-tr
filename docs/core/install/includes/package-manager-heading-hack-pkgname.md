---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466000"
---

<span data-ttu-id="cc270-101">Paket Yöneticisi akışlarına eklenen paketlerin adı, uyumlu bir biçimde: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="cc270-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="cc270-102">**ürün**</span><span class="sxs-lookup"><span data-stu-id="cc270-102">**product**</span></span>\
<span data-ttu-id="cc270-103">Yüklenecek .NET Ürün türü.</span><span class="sxs-lookup"><span data-stu-id="cc270-103">The type of .NET product to install.</span></span> <span data-ttu-id="cc270-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cc270-104">Valid options are:</span></span>

  - <span data-ttu-id="cc270-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="cc270-105">dotnet</span></span>
  - <span data-ttu-id="cc270-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="cc270-106">aspnetcore</span></span>

- <span data-ttu-id="cc270-107">**tür**</span><span class="sxs-lookup"><span data-stu-id="cc270-107">**type**</span></span>\
<span data-ttu-id="cc270-108">SDK 'Yı veya çalışma zamanını seçer.</span><span class="sxs-lookup"><span data-stu-id="cc270-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="cc270-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cc270-109">Valid options are:</span></span>

  - <span data-ttu-id="cc270-110">sdk</span><span class="sxs-lookup"><span data-stu-id="cc270-110">sdk</span></span>
  - <span data-ttu-id="cc270-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="cc270-111">runtime</span></span>

- <span data-ttu-id="cc270-112">**sürüm**</span><span class="sxs-lookup"><span data-stu-id="cc270-112">**version**</span></span>\
<span data-ttu-id="cc270-113">Yüklenecek SDK veya çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="cc270-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="cc270-114">Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="cc270-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="cc270-115">Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:</span><span class="sxs-lookup"><span data-stu-id="cc270-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="cc270-116">3.1</span><span class="sxs-lookup"><span data-stu-id="cc270-116">3.1</span></span>
  - <span data-ttu-id="cc270-117">3.0</span><span class="sxs-lookup"><span data-stu-id="cc270-117">3.0</span></span>
  - <span data-ttu-id="cc270-118">2.1</span><span class="sxs-lookup"><span data-stu-id="cc270-118">2.1</span></span>

  <span data-ttu-id="cc270-119">İndirmeyi denediğiniz SDK/çalışma zamanı Linux dağıtım için kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc270-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="cc270-120">Desteklenen dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="cc270-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="cc270-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cc270-121">Examples</span></span>

- <span data-ttu-id="cc270-122">ASP.NET Core 3,1 çalışma zamanını yükler: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="cc270-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="cc270-123">.NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="cc270-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="cc270-124">.NET Core 3,0 SDK 'sını yükler: `dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="cc270-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="cc270-125">Paket eksik</span><span class="sxs-lookup"><span data-stu-id="cc270-125">Package missing</span></span>

<span data-ttu-id="cc270-126">Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="cc270-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="cc270-127">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir.</span><span class="sxs-lookup"><span data-stu-id="cc270-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="cc270-128">`aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc270-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="cc270-129">.NET Core tarafından desteklenen Linux dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="cc270-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
