---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394150"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="0610c-101">Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="0610c-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="0610c-102">ASP.NET Core 3,0 ' den itibaren Windows barındırma paketi, AspNetCoreModule (ANCM) v1 'yi içermez.</span><span class="sxs-lookup"><span data-stu-id="0610c-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="0610c-103">ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="0610c-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="0610c-104">Tartışma için bkz. [ASPNET/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095).</span><span class="sxs-lookup"><span data-stu-id="0610c-104">For discussion, see [aspnet/AspNetCore#7095](https://github.com/aspnet/AspNetCore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0610c-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0610c-105">Version introduced</span></span>

<span data-ttu-id="0610c-106">3.0</span><span class="sxs-lookup"><span data-stu-id="0610c-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0610c-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="0610c-107">Old behavior</span></span>

<span data-ttu-id="0610c-108">ANCM v1, Windows barındırma paketi 'ne dahildir.</span><span class="sxs-lookup"><span data-stu-id="0610c-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0610c-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="0610c-109">New behavior</span></span>

<span data-ttu-id="0610c-110">ANCM v1, Windows barındırma paketi 'ne dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="0610c-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0610c-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0610c-111">Reason for change</span></span>

<span data-ttu-id="0610c-112">ANCM v2, ANCM OutOfProcess ile geriye dönük olarak uyumludur ve ASP.NET Core 3,0 uygulamalarıyla birlikte kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="0610c-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0610c-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0610c-113">Recommended action</span></span>

<span data-ttu-id="0610c-114">ASP.NET Core 3,0 uygulamalarıyla birlikte ANCM v2 kullanın.</span><span class="sxs-lookup"><span data-stu-id="0610c-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="0610c-115">ANCM v1 gerekliyse, ASP.NET Core 2,1 veya 2,2 Windows barındırma paketi kullanılarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0610c-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="0610c-116">Bu değişiklik, şu şekilde ASP.NET Core 3,0 uygulamalarını keser:</span><span class="sxs-lookup"><span data-stu-id="0610c-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="0610c-117">@No__t-0 ile birlikte ANCM v1 kullanarak açıkça kabul edildi.</span><span class="sxs-lookup"><span data-stu-id="0610c-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="0610c-118">@No__t-1 ile özel bir *Web. config* dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0610c-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="0610c-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="0610c-119">Category</span></span>

<span data-ttu-id="0610c-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0610c-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0610c-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0610c-121">Affected APIs</span></span>

<span data-ttu-id="0610c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="0610c-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
