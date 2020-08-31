---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602994"
---

<span data-ttu-id="08259-101">Paket Yöneticisi akışlarına eklenen paketler, uyumlu olmayan biçimde adlandırılır: `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="08259-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="08259-102">**ürünüyle**</span><span class="sxs-lookup"><span data-stu-id="08259-102">**product**</span></span>\
<span data-ttu-id="08259-103">Yüklenecek .NET Ürün türü.</span><span class="sxs-lookup"><span data-stu-id="08259-103">The type of .NET product to install.</span></span> <span data-ttu-id="08259-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="08259-104">Valid options are:</span></span>

  - <span data-ttu-id="08259-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="08259-105">dotnet</span></span>
  - <span data-ttu-id="08259-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="08259-106">aspnetcore</span></span>

- <span data-ttu-id="08259-107">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="08259-107">**type**</span></span>\
<span data-ttu-id="08259-108">SDK 'Yı veya çalışma zamanını seçer.</span><span class="sxs-lookup"><span data-stu-id="08259-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="08259-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="08259-109">Valid options are:</span></span>

  - <span data-ttu-id="08259-110">sdk</span><span class="sxs-lookup"><span data-stu-id="08259-110">sdk</span></span>
  - <span data-ttu-id="08259-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="08259-111">runtime</span></span>

- <span data-ttu-id="08259-112">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="08259-112">**version**</span></span>\
<span data-ttu-id="08259-113">Yüklenecek SDK veya çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="08259-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="08259-114">Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="08259-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="08259-115">Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:</span><span class="sxs-lookup"><span data-stu-id="08259-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="08259-116">3,1</span><span class="sxs-lookup"><span data-stu-id="08259-116">3.1</span></span>
  - <span data-ttu-id="08259-117">3.0</span><span class="sxs-lookup"><span data-stu-id="08259-117">3.0</span></span>
  - <span data-ttu-id="08259-118">2.1</span><span class="sxs-lookup"><span data-stu-id="08259-118">2.1</span></span>

  <span data-ttu-id="08259-119">İndirmeyi denediğiniz SDK/çalışma zamanı Linux dağıtım için kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="08259-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="08259-120">Desteklenen dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="08259-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="08259-121">Örnekler</span><span class="sxs-lookup"><span data-stu-id="08259-121">Examples</span></span>

- <span data-ttu-id="08259-122">ASP.NET Core 3,1 çalışma zamanını yükler: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="08259-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="08259-123">.NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="08259-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="08259-124">.NET Core 3,1 SDK 'sını yükler: `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="08259-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="08259-125">Paket eksik</span><span class="sxs-lookup"><span data-stu-id="08259-125">Package missing</span></span>

<span data-ttu-id="08259-126">Paket sürümü birleşimi işe yaramazsa, kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="08259-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="08259-127">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir.</span><span class="sxs-lookup"><span data-stu-id="08259-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="08259-128">Değer `aspnetcore-sdk-2.2` yanlış ve olmalıdır `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="08259-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="08259-129">.NET Core tarafından desteklenen Linux dağıtımların listesi için bkz. [.NET Core Dependencies ve Requirements](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="08259-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../linux.md).</span></span>
