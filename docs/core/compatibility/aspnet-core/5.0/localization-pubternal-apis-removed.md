---
title: "Son değişiklik: Pubternal API 'Ler kaldırıldı"
description: ASP.NET Core 5,0 ' deki, bazı pubternal yerelleştirme API 'Lerinin kaldırıldığı Son değişiklik hakkında bilgi edinin
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761406"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="5ce13-103">Yerelleştirme: "Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="5ce13-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="5ce13-104">ASP.NET Core ortak API yüzeyini daha iyi korumak için bazı :::no-loc text="\"pubternal\""::: Yerelleştirme API 'leri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5ce13-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="5ce13-105">Bir :::no-loc text="\"pubternal\""::: API 'nin `public` erişim değiştiricisi vardır ve bir [iç](../../../../csharp/language-reference/keywords/internal.md) amacı gösteren bir ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5ce13-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="5ce13-106">Tartışma için bkz. [DotNet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="5ce13-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5ce13-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5ce13-107">Version introduced</span></span>

<span data-ttu-id="5ce13-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="5ce13-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="5ce13-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="5ce13-109">Old behavior</span></span>

<span data-ttu-id="5ce13-110">Aşağıdaki API 'Ler `public` :</span><span class="sxs-lookup"><span data-stu-id="5ce13-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="5ce13-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri:</span><span class="sxs-lookup"><span data-stu-id="5ce13-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="5ce13-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="5ce13-112">New behavior</span></span>

<span data-ttu-id="5ce13-113">Aşağıdaki listede değişiklikler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="5ce13-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="5ce13-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="5ce13-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="5ce13-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="5ce13-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="5ce13-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri artık şunlardır `internal` :</span><span class="sxs-lookup"><span data-stu-id="5ce13-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="5ce13-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5ce13-117">Reason for change</span></span>

<span data-ttu-id="5ce13-118">[ASPNET/Duyurular # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)'de daha kapsamlı bir şekilde açıklanmıştı, :::no-loc text="\"pubternal\""::: türler `public` API yüzeyinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5ce13-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="5ce13-119">Bu değişiklikler, bu tasarım kararına daha fazla sınıf uyarlar.</span><span class="sxs-lookup"><span data-stu-id="5ce13-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="5ce13-120">Söz konusu sınıflar, takımın iç testi için uzantı noktaları olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5ce13-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5ce13-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5ce13-121">Recommended action</span></span>

<span data-ttu-id="5ce13-122">Büyük olasılıkla, bazı uygulamalar kasıtlı veya yanlışlıkla türlerine bağlı olabilir :::no-loc text="\"pubternal\""::: .</span><span class="sxs-lookup"><span data-stu-id="5ce13-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="5ce13-123">Türlerin dışında nasıl geçiş yapılacağını öğrenmek için [Yeni davranış](#new-behavior) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5ce13-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="5ce13-124">Ortak API 'nin bu değişiklikten önce izin verilen ancak şimdi olmayan bir senaryo belirlediyseniz, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="5ce13-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5ce13-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5ce13-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
