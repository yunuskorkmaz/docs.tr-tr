---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539513"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="e9ce2-101">Yerelleştirme: "Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="e9ce2-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="e9ce2-102">ASP.NET Core ortak API yüzeyini daha iyi korumak için bazı :::no-loc text="\"pubternal\""::: Yerelleştirme API 'leri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="e9ce2-103">Bir :::no-loc text="\"pubternal\""::: API 'nin `public` erişim değiştiricisi vardır ve bir [iç](../../../../docs/csharp/language-reference/keywords/internal.md) amacı gösteren bir ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../docs/csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="e9ce2-104">Tartışma için bkz. [DotNet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="e9ce2-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e9ce2-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e9ce2-105">Version introduced</span></span>

<span data-ttu-id="e9ce2-106">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="e9ce2-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e9ce2-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e9ce2-107">Old behavior</span></span>

<span data-ttu-id="e9ce2-108">Aşağıdaki API 'Ler `public` :</span><span class="sxs-lookup"><span data-stu-id="e9ce2-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="e9ce2-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri:</span><span class="sxs-lookup"><span data-stu-id="e9ce2-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="e9ce2-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e9ce2-110">New behavior</span></span>

<span data-ttu-id="e9ce2-111">Aşağıdaki listede değişiklikler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="e9ce2-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="e9ce2-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="e9ce2-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="e9ce2-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`Şimdi geldi `internal` .</span><span class="sxs-lookup"><span data-stu-id="e9ce2-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="e9ce2-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri artık şunlardır `internal` :</span><span class="sxs-lookup"><span data-stu-id="e9ce2-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="e9ce2-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e9ce2-115">Reason for change</span></span>

<span data-ttu-id="e9ce2-116">[ASPNET/Duyurular # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)'de daha kapsamlı bir şekilde açıklanmıştı, :::no-loc text="\"pubternal\""::: türler `public` API yüzeyinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="e9ce2-117">Bu değişiklikler, bu tasarım kararına daha fazla sınıf uyarlar.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="e9ce2-118">Söz konusu sınıflar, takımın iç testi için uzantı noktaları olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e9ce2-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e9ce2-119">Recommended action</span></span>

<span data-ttu-id="e9ce2-120">Büyük olasılıkla, bazı uygulamalar kasıtlı veya yanlışlıkla türlerine bağlı olabilir :::no-loc text="\"pubternal\""::: .</span><span class="sxs-lookup"><span data-stu-id="e9ce2-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="e9ce2-121">Türlerin dışında nasıl geçiş yapılacağını öğrenmek için [Yeni davranış](#new-behavior) bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="e9ce2-122">Ortak API 'nin bu değişiklikten önce izin verilen ancak şimdi olmayan bir senaryo belirlediyseniz, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9ce2-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="e9ce2-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="e9ce2-123">Category</span></span>

<span data-ttu-id="e9ce2-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e9ce2-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e9ce2-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e9ce2-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
