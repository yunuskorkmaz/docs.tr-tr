---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920662"
---

<span data-ttu-id="dcbe4-101">Paket Yöneticisi akışlarına eklenen paketlerin adı, uyumlu bir biçimde: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="dcbe4-102">**ürün**</span><span class="sxs-lookup"><span data-stu-id="dcbe4-102">**product**</span></span>\
<span data-ttu-id="dcbe4-103">Yüklenecek .NET Ürün türü.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-103">The type of .NET product to install.</span></span> <span data-ttu-id="dcbe4-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dcbe4-104">Valid options are:</span></span>

  - <span data-ttu-id="dcbe4-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="dcbe4-105">dotnet</span></span>
  - <span data-ttu-id="dcbe4-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="dcbe4-106">aspnetcore</span></span>

- <span data-ttu-id="dcbe4-107">**tür**</span><span class="sxs-lookup"><span data-stu-id="dcbe4-107">**type**</span></span>\
<span data-ttu-id="dcbe4-108">SDK 'Yı veya çalışma zamanını seçer.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="dcbe4-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dcbe4-109">Valid options are:</span></span>

  - <span data-ttu-id="dcbe4-110">'sının</span><span class="sxs-lookup"><span data-stu-id="dcbe4-110">sdk</span></span>
  - <span data-ttu-id="dcbe4-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="dcbe4-111">runtime</span></span>

- <span data-ttu-id="dcbe4-112">**sürüm**</span><span class="sxs-lookup"><span data-stu-id="dcbe4-112">**version**</span></span>\
<span data-ttu-id="dcbe4-113">Yüklenecek SDK veya çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="dcbe4-114">Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="dcbe4-115">Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:</span><span class="sxs-lookup"><span data-stu-id="dcbe4-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="dcbe4-116">3.0</span><span class="sxs-lookup"><span data-stu-id="dcbe4-116">3.0</span></span>
  - <span data-ttu-id="dcbe4-117">2.2</span><span class="sxs-lookup"><span data-stu-id="dcbe4-117">2.2</span></span>
  - <span data-ttu-id="dcbe4-118">2.1</span><span class="sxs-lookup"><span data-stu-id="dcbe4-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="dcbe4-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dcbe4-119">Examples</span></span>

- <span data-ttu-id="dcbe4-120">.NET Core 2,2 SDK 'sını yükler: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="dcbe4-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="dcbe4-121">ASP.NET Core 3,1 çalışma zamanını yükler: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="dcbe4-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="dcbe4-122">.NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="dcbe4-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="dcbe4-123">Paket eksik</span><span class="sxs-lookup"><span data-stu-id="dcbe4-123">Package missing</span></span>

<span data-ttu-id="dcbe4-124">Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-124">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="dcbe4-125">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="dcbe4-126">`aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dcbe4-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span>
