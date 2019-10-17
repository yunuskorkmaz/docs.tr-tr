---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394418"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="b3b6a-101">Yerelleştirme: ResourceManagerWithCultureStringLocalizer ve WithCulture artık kullanılmıyor olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="b3b6a-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="b3b6a-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) sınıfı ve [withculture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) arabirim üyesi, genellikle yerelleştirme kullanıcıları için, özellikle kendi `IStringLocalizer` uygulamasını oluştururken karışıklıklar kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="b3b6a-103">Bu öğeler kullanıcıya bir `IStringLocalizer` örneği "dil başına, kaynak başına" olan izlenimi verir.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="b3b6a-104">Gerçekte, örneklerin yalnızca "kaynak başına" olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="b3b6a-105">Aranan dil, yürütme sırasında `CultureInfo.CurrentUICulture` tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="b3b6a-106">Karışıklık kaynağını ortadan kaldırmak için, API 'Ler ASP.NET Core 3,0 Preview 3 ' te eski olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="b3b6a-107">API 'Ler gelecek bir sürümde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="b3b6a-108">Bağlam için bkz. [ASPNET/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="b3b6a-108">For context, see [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span></span> <span data-ttu-id="b3b6a-109">Tartışma için bkz. [ASPNET/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="b3b6a-109">For discussion, see [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3b6a-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b3b6a-110">Version introduced</span></span>

<span data-ttu-id="b3b6a-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b3b6a-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b3b6a-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b3b6a-112">Old behavior</span></span>

<span data-ttu-id="b3b6a-113">Metotlar `Obsolete` olarak işaretlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b3b6a-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b3b6a-114">New behavior</span></span>

<span data-ttu-id="b3b6a-115">Yöntemler @no__t olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b3b6a-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b3b6a-116">Reason for change</span></span>

<span data-ttu-id="b3b6a-117">API 'Ler önerilmeyen bir kullanım durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="b3b6a-118">Yerelleştirme tasarımı hakkında karışıklık vardı.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3b6a-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b3b6a-119">Recommended action</span></span>

<span data-ttu-id="b3b6a-120">Bunun yerine `ResourceManagerStringLocalizer` kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="b3b6a-121">Kültüre `CurrentCulture` tarafından ayarlanmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="b3b6a-122">Bu seçenek değilse, bir [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18)kopyası oluşturun ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3b6a-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="b3b6a-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="b3b6a-123">Category</span></span>

<span data-ttu-id="b3b6a-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3b6a-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3b6a-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b3b6a-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
