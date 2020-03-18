---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901985"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="613d8-101">Hosting: AspNetCoreModule V1 Windows Hosting Paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="613d8-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="613d8-102">Core 3.0 ASP.NET başlayarak, Windows Hosting Paketi AspNetCoreModule (ANCM) V1 içermez.</span><span class="sxs-lookup"><span data-stu-id="613d8-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="613d8-103">ANCM V2, ANCM OutOfProcess ile geriye doğru uyumludur ve ASP.NET Core 3.0 uygulamalarıyla kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="613d8-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="613d8-104">Tartışma için [dotnet/aspnetcore#7095'e](https://github.com/dotnet/aspnetcore/issues/7095)bakın.</span><span class="sxs-lookup"><span data-stu-id="613d8-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="613d8-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="613d8-105">Version introduced</span></span>

<span data-ttu-id="613d8-106">3,0</span><span class="sxs-lookup"><span data-stu-id="613d8-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="613d8-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="613d8-107">Old behavior</span></span>

<span data-ttu-id="613d8-108">ANCM V1, Windows Barındırma Paketi'ne dahildir.</span><span class="sxs-lookup"><span data-stu-id="613d8-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="613d8-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="613d8-109">New behavior</span></span>

<span data-ttu-id="613d8-110">ANCM V1, Windows Barındırma Paketi'ne dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="613d8-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="613d8-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="613d8-111">Reason for change</span></span>

<span data-ttu-id="613d8-112">ANCM V2, ANCM OutOfProcess ile geriye doğru uyumludur ve ASP.NET Core 3.0 uygulamalarıyla kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="613d8-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="613d8-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="613d8-113">Recommended action</span></span>

<span data-ttu-id="613d8-114">ASP.NET Core 3.0 uygulamalarıyla ANCM V2 kullanın.</span><span class="sxs-lookup"><span data-stu-id="613d8-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="613d8-115">ANCM V1 gerekirse, ASP.NET Core 2.1 veya 2.2 Windows Hosting Paketi kullanılarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="613d8-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="613d8-116">Bu değişiklik, Core 3.0 uygulamaları ASP.NET kıracak:</span><span class="sxs-lookup"><span data-stu-id="613d8-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="613d8-117">Açıkça ILE ANCM V1 kullanarak `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`tercih etti.</span><span class="sxs-lookup"><span data-stu-id="613d8-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="613d8-118">Özel bir *web.config* `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`dosyası var.</span><span class="sxs-lookup"><span data-stu-id="613d8-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="613d8-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="613d8-119">Category</span></span>

<span data-ttu-id="613d8-120">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="613d8-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="613d8-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="613d8-121">Affected APIs</span></span>

<span data-ttu-id="613d8-122">None</span><span class="sxs-lookup"><span data-stu-id="613d8-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
