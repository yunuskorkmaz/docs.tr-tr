---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032740"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="8c6a6-101">Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="8c6a6-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="8c6a6-102">ASP.NET Core 3,0 ' den itibaren Windows barındırma paketi, AspNetCoreModule (ANCM) v1 'yi içermez.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="8c6a6-103">ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="8c6a6-104">Tartışma için bkz. [DotNet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="8c6a6-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c6a6-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="8c6a6-105">Version introduced</span></span>

<span data-ttu-id="8c6a6-106">3,0</span><span class="sxs-lookup"><span data-stu-id="8c6a6-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8c6a6-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="8c6a6-107">Old behavior</span></span>

<span data-ttu-id="8c6a6-108">ANCM v1, Windows barındırma paketi 'ne dahildir.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8c6a6-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="8c6a6-109">New behavior</span></span>

<span data-ttu-id="8c6a6-110">ANCM v1, Windows barındırma paketi 'ne dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c6a6-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="8c6a6-111">Reason for change</span></span>

<span data-ttu-id="8c6a6-112">ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c6a6-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="8c6a6-113">Recommended action</span></span>

<span data-ttu-id="8c6a6-114">ASP.NET Core 3,0 uygulamalarıyla birlikte ANCM v2 kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="8c6a6-115">ANCM v1 gerekliyse, ASP.NET Core 2,1 veya 2,2 Windows barındırma paketi kullanılarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8c6a6-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="8c6a6-116">Bu değişiklik, şu şekilde ASP.NET Core 3,0 uygulamalarını keser:</span><span class="sxs-lookup"><span data-stu-id="8c6a6-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="8c6a6-117">İle ANCM v1 kullanarak açıkça kabul edildi `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` .</span><span class="sxs-lookup"><span data-stu-id="8c6a6-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="8c6a6-118">İle özel bir *web.config* dosyası olmalıdır `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` .</span><span class="sxs-lookup"><span data-stu-id="8c6a6-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="8c6a6-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="8c6a6-119">Category</span></span>

<span data-ttu-id="8c6a6-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8c6a6-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c6a6-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8c6a6-121">Affected APIs</span></span>

<span data-ttu-id="8c6a6-122">Yok</span><span class="sxs-lookup"><span data-stu-id="8c6a6-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
