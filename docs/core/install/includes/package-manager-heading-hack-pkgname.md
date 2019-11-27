---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450886"
---

<span data-ttu-id="5b7a3-101">Paket Yöneticisi akışlarına eklenen paketlerin adı, uyumlu bir biçimde: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="5b7a3-102">**ürün**</span><span class="sxs-lookup"><span data-stu-id="5b7a3-102">**product**</span></span>\
<span data-ttu-id="5b7a3-103">Yüklenecek .NET Ürün türü.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-103">The type of .NET product to install.</span></span> <span data-ttu-id="5b7a3-104">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5b7a3-104">Valid options are:</span></span>

  - <span data-ttu-id="5b7a3-105">DotNet</span><span class="sxs-lookup"><span data-stu-id="5b7a3-105">dotnet</span></span>
  - <span data-ttu-id="5b7a3-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="5b7a3-106">aspnetcore</span></span>

- <span data-ttu-id="5b7a3-107">**tür**</span><span class="sxs-lookup"><span data-stu-id="5b7a3-107">**type**</span></span>\
<span data-ttu-id="5b7a3-108">SDK 'Yı veya çalışma zamanını seçer.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="5b7a3-109">Geçerli seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5b7a3-109">Valid options are:</span></span>

  - <span data-ttu-id="5b7a3-110">'sının</span><span class="sxs-lookup"><span data-stu-id="5b7a3-110">sdk</span></span>
  - <span data-ttu-id="5b7a3-111">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="5b7a3-111">runtime</span></span>

- <span data-ttu-id="5b7a3-112">**sürüm**</span><span class="sxs-lookup"><span data-stu-id="5b7a3-112">**version**</span></span>\
<span data-ttu-id="5b7a3-113">Yüklenecek SDK veya çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="5b7a3-114">Bu makale her zaman desteklenen en son sürüme yönelik yönergelere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="5b7a3-115">Geçerli seçenekler, şu gibi yayınlanmış bir sürümdür:</span><span class="sxs-lookup"><span data-stu-id="5b7a3-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="5b7a3-116">3,0</span><span class="sxs-lookup"><span data-stu-id="5b7a3-116">3.0</span></span>
  - <span data-ttu-id="5b7a3-117">2.2</span><span class="sxs-lookup"><span data-stu-id="5b7a3-117">2.2</span></span>
  - <span data-ttu-id="5b7a3-118">2.1</span><span class="sxs-lookup"><span data-stu-id="5b7a3-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="5b7a3-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5b7a3-119">Examples</span></span>

- <span data-ttu-id="5b7a3-120">.NET Core 2,2 SDK 'sını yükler: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="5b7a3-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="5b7a3-121">ASP.NET Core 3,0 çalışma zamanını yükler: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="5b7a3-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="5b7a3-122">.NET Core 2,1 çalışma zamanını yükler: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="5b7a3-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="5b7a3-123">Sorunları Gider</span><span class="sxs-lookup"><span data-stu-id="5b7a3-123">Troubleshoot</span></span>

<span data-ttu-id="5b7a3-124">Paket birleşimi işe yaramazsa, kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="5b7a3-125">Örneğin, ASP.NET Core SDK yoktur, SDK bileşenleri .NET Core SDK eklenir.</span><span class="sxs-lookup"><span data-stu-id="5b7a3-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="5b7a3-126">`aspnetcore-sdk-2.2` değeri hatalı ve `dotnet-sdk-2.2` olmalıdır</span><span class="sxs-lookup"><span data-stu-id="5b7a3-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
