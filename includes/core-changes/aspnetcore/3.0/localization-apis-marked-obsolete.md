---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901892"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="e5f6a-101">Yerelleştirme: ResourceManagerWithCultureStringLocalizer ve WithCulture eski olarak işaretlenmiş</span><span class="sxs-lookup"><span data-stu-id="e5f6a-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="e5f6a-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) sınıf ve [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) arayüz üyesi genellikle kendi `IStringLocalizer` uygulama oluştururken, yerelleştirme kullanıcıları için karışıklık kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="e5f6a-103">Bu öğeler, kullanıcıya bir `IStringLocalizer` örneğin "dil başına, kaynak başına" olduğu izlenimini verir.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="e5f6a-104">Gerçekte, örnekleri sadece "kaynak başına" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="e5f6a-105">Aranan dil, infaz zamanına `CultureInfo.CurrentUICulture` göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="e5f6a-106">Karışıklığın kaynağını ortadan kaldırmak için API'ler Core 3.0 Preview 3'ASP.NET geçersiz olarak işaretlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="e5f6a-107">API'ler ileride yayınlanacak bir sürümde kaldırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="e5f6a-108">Bağlam için [dotnet/aspnetcore#3324'e](https://github.com/dotnet/aspnetcore/issues/3324)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="e5f6a-109">Tartışma için [dotnet/aspnetcore#7756'ya](https://github.com/dotnet/aspnetcore/issues/7756)bakın.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e5f6a-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="e5f6a-110">Version introduced</span></span>

<span data-ttu-id="e5f6a-111">3,0</span><span class="sxs-lookup"><span data-stu-id="e5f6a-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e5f6a-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e5f6a-112">Old behavior</span></span>

<span data-ttu-id="e5f6a-113">Yöntemler ' olarak `Obsolete`işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e5f6a-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e5f6a-114">New behavior</span></span>

<span data-ttu-id="e5f6a-115">Yöntemler işaretlenir. `Obsolete`</span><span class="sxs-lookup"><span data-stu-id="e5f6a-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e5f6a-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e5f6a-116">Reason for change</span></span>

<span data-ttu-id="e5f6a-117">API'ler önerilmez bir kullanım örneği temsil etti.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="e5f6a-118">Yerelleştirme tasarımı hakkında karışıklık vardı.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5f6a-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e5f6a-119">Recommended action</span></span>

<span data-ttu-id="e5f6a-120">Öneri bunun yerine `ResourceManagerStringLocalizer` kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="e5f6a-121">Kültür tarafından `CurrentCulture`ayarlansın.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="e5f6a-122">Bu bir seçenek değilse, [KaynakYöneticisiWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)bir kopyasını oluşturun ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5f6a-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="e5f6a-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="e5f6a-123">Category</span></span>

<span data-ttu-id="e5f6a-124">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="e5f6a-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5f6a-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e5f6a-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
