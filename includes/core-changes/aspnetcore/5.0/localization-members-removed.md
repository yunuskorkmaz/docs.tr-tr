---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728275"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="75bd7-101">Yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="75bd7-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="75bd7-102">.NET 5,0 Preview 1 ' de [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) Class ve [withculture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) yöntemi kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="75bd7-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="75bd7-103">Bağlam için bkz. [ASPNET/Duyurular # 346](https://github.com/aspnet/Announcements/issues/346) ve [DotNet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="75bd7-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="75bd7-104">Bu değişiklik hakkında tartışma için bkz. [DotNet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="75bd7-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="75bd7-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="75bd7-105">Version introduced</span></span>

<span data-ttu-id="75bd7-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="75bd7-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="75bd7-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="75bd7-107">Old behavior</span></span>

<span data-ttu-id="75bd7-108">`ResourceManagerWithCultureStringLocalizer` Sınıfı ve `ResourceManagerStringLocalizer.WithCulture` yöntemi [.NET Core 3,0 Preview 3 ve sonraki sürümlerde kullanılmıyor](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="75bd7-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="75bd7-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="75bd7-109">New behavior</span></span>

<span data-ttu-id="75bd7-110">`ResourceManagerWithCultureStringLocalizer` Sınıfı ve `ResourceManagerStringLocalizer.WithCulture` yöntemi .NET 5,0 Preview 1 ' de kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="75bd7-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="75bd7-111">Yapılan değişikliklerin envanterini görmek için [DotNet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files)konumundaki çekme isteğine bakın.</span><span class="sxs-lookup"><span data-stu-id="75bd7-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="75bd7-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="75bd7-112">Reason for change</span></span>

<span data-ttu-id="75bd7-113">[ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) sınıfı ve [Resourcemanagerstringlocalizer. withculture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) yöntemi genellikle yerelleştirme kullanıcıları için karışıklık kaynaklarıdır.</span><span class="sxs-lookup"><span data-stu-id="75bd7-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="75bd7-114">Özel <xref:Microsoft.Extensions.Localization.IStringLocalizer> bir uygulama oluşturulurken karışıklık özellikle yüksek.</span><span class="sxs-lookup"><span data-stu-id="75bd7-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="75bd7-115">Bu sınıf ve yöntem, tüketicilere bir `IStringLocalizer` örneğin "dil başına, kaynak başına" olması beklenme izlenimi verir.</span><span class="sxs-lookup"><span data-stu-id="75bd7-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="75bd7-116">Gerçekte, örnek yalnızca "kaynak başına" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75bd7-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="75bd7-117">Çalışma zamanında, <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliği kullanılacak dili belirler.</span><span class="sxs-lookup"><span data-stu-id="75bd7-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="75bd7-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="75bd7-118">Recommended action</span></span>

<span data-ttu-id="75bd7-119">`ResourceManagerWithCultureStringLocalizer` Sınıfını ve `ResourceManagerStringLocalizer.WithCulture` yöntemini kullanmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="75bd7-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="75bd7-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="75bd7-120">Category</span></span>

<span data-ttu-id="75bd7-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75bd7-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75bd7-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="75bd7-122">Affected APIs</span></span>

- [<span data-ttu-id="75bd7-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="75bd7-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="75bd7-124">ResourceManagerStringLocalizer. WithCulture</span><span class="sxs-lookup"><span data-stu-id="75bd7-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
