---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901892"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="96035-101">Yerelleştirme: ResourceManagerWithCultureStringLocalizer ve WithCulture artık kullanılmıyor olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="96035-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="96035-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) sınıfı ve [withculture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) arabirim üyesi, genellikle yerelleştirme kullanıcıları için, özellikle kendi `IStringLocalizer` uygulamasını oluştururken karışıklık kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="96035-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="96035-103">Bu öğeler kullanıcıya bir `IStringLocalizer` örneği "dil başına, kaynak başına" olan izlenimi verir.</span><span class="sxs-lookup"><span data-stu-id="96035-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="96035-104">Gerçekte, örneklerin yalnızca "kaynak başına" olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="96035-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="96035-105">Aranan dil, yürütme sırasında `CultureInfo.CurrentUICulture` tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="96035-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="96035-106">Karışıklık kaynağını ortadan kaldırmak için, API 'Ler ASP.NET Core 3,0 Preview 3 ' te eski olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="96035-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="96035-107">API 'Ler gelecek bir sürümde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="96035-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="96035-108">Bağlam için bkz. [DotNet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="96035-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="96035-109">Tartışma için bkz. [DotNet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="96035-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="96035-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="96035-110">Version introduced</span></span>

<span data-ttu-id="96035-111">3.0</span><span class="sxs-lookup"><span data-stu-id="96035-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="96035-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="96035-112">Old behavior</span></span>

<span data-ttu-id="96035-113">Yöntemler `Obsolete`olarak işaretlenmedi.</span><span class="sxs-lookup"><span data-stu-id="96035-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="96035-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="96035-114">New behavior</span></span>

<span data-ttu-id="96035-115">Yöntemler `Obsolete`olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="96035-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="96035-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="96035-116">Reason for change</span></span>

<span data-ttu-id="96035-117">API 'Ler önerilmeyen bir kullanım durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96035-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="96035-118">Yerelleştirme tasarımı hakkında karışıklık vardı.</span><span class="sxs-lookup"><span data-stu-id="96035-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="96035-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="96035-119">Recommended action</span></span>

<span data-ttu-id="96035-120">Bunun yerine `ResourceManagerStringLocalizer` kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="96035-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="96035-121">Kültür `CurrentCulture`tarafından ayarlanmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="96035-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="96035-122">Bu seçenek değilse, bir [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)kopyası oluşturun ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="96035-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="96035-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="96035-123">Category</span></span>

<span data-ttu-id="96035-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96035-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="96035-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="96035-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
