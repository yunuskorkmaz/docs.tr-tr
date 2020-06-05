---
ms.openlocfilehash: 2094da7ec94028c112d6683620ac1146a1544dab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446984"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="0c9f5-101">Yerelleştirme: "Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="0c9f5-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="0c9f5-102">ASP.NET Core ortak API yüzeyini daha iyi korumak için bazı :::no-loc text="\"pubternal\""::: Yerelleştirme API 'leri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="0c9f5-103">Bir :::no-loc text="\"pubternal\""::: API 'nin `public` erişim değiştiricisi vardır ve bir [iç](/dotnet/csharp/language-reference/keywords/internal) amacı gösteren bir ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](/dotnet/csharp/language-reference/keywords/internal) intent.</span></span>

<span data-ttu-id="0c9f5-104">Tartışma için bkz. [DotNet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="0c9f5-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c9f5-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0c9f5-105">Version introduced</span></span>

<span data-ttu-id="0c9f5-106">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="0c9f5-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0c9f5-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="0c9f5-107">Old behavior</span></span>

<span data-ttu-id="0c9f5-108">Aşağıdaki API 'Ler `public` :</span><span class="sxs-lookup"><span data-stu-id="0c9f5-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="0c9f5-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri:</span><span class="sxs-lookup"><span data-stu-id="0c9f5-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="0c9f5-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="0c9f5-110">New behavior</span></span>

<span data-ttu-id="0c9f5-111">Aşağıdaki listede değişiklikler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="0c9f5-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="0c9f5-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="0c9f5-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="0c9f5-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="0c9f5-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="0c9f5-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri artık şunlardır `internal` :</span><span class="sxs-lookup"><span data-stu-id="0c9f5-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="0c9f5-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0c9f5-115">Reason for change</span></span>

<span data-ttu-id="0c9f5-116">[ASPNET/Duyurular # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)'de daha kapsamlı bir şekilde açıklanmıştı, :::no-loc text="\"pubternal\""::: türler `public` API yüzeyinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="0c9f5-117">Bu değişiklikler, bu tasarım kararına daha fazla sınıf uyarlar.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="0c9f5-118">Söz konusu sınıflar, takımın iç testi için uzantı noktaları olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c9f5-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0c9f5-119">Recommended action</span></span>

<span data-ttu-id="0c9f5-120">Büyük olasılıkla, bazı uygulamalar kasıtlı veya yanlışlıkla türlerine bağlı olabilir :::no-loc text="\"pubternal\""::: .</span><span class="sxs-lookup"><span data-stu-id="0c9f5-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="0c9f5-121">Türlerin dışında nasıl geçiş yapılacağını öğrenmek için [Yeni davranış](#new-behavior) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="0c9f5-122">Ortak API 'nin bu değişiklikten önce izin verilen ancak şimdi olmayan bir senaryo belirlediyseniz, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="0c9f5-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="0c9f5-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="0c9f5-123">Category</span></span>

<span data-ttu-id="0c9f5-124">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="0c9f5-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c9f5-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0c9f5-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
