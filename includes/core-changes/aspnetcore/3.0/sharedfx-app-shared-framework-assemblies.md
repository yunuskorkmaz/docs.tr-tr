---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549611"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="3fbe8-101">Paylaşılan çerçeve: Microsoft.AspNetCore.App'ten kaldırılan derlemeler</span><span class="sxs-lookup"><span data-stu-id="3fbe8-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="3fbe8-102">Core 3.0ASP.NETdan başlayarak, ASP.NET`Microsoft.AspNetCore.App`Core paylaşılan çerçevesi ( ) yalnızca Microsoft tarafından tamamen geliştirilen, desteklenen ve hizmet verilen birinci taraf derlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3fbe8-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="3fbe8-103">Change description</span></span>

<span data-ttu-id="3fbe8-104">Değişimi ASP.NET Core "platformu" için sınırların yeniden tanımlanması olarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="3fbe8-105">Paylaşılan [çerçeve, GitHub üzerinden herkes tarafından kaynak oluşturabilen](https://github.com/dotnet/source-build) bir çerçeve olacak ve .NET Core paylaşılan çerçevelerinin mevcut avantajlarını uygulamalarınız için sunmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="3fbe8-106">Bazı avantajlar daha küçük dağıtım boyutu, merkezi yama ve daha hızlı başlatma süresi içerir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="3fbe8-107">Değişikliğin bir parçası olarak, bazı önemli kırılma `Microsoft.AspNetCore.App`değişiklikleri tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3fbe8-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="3fbe8-108">Version introduced</span></span>

<span data-ttu-id="3fbe8-109">3,0</span><span class="sxs-lookup"><span data-stu-id="3fbe8-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3fbe8-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3fbe8-110">Old behavior</span></span>

<span data-ttu-id="3fbe8-111">Proje dosyasındaki `Microsoft.AspNetCore.App` `<PackageReference>` bir öğe üzerinden başvurulan projeler.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="3fbe8-112">Ayrıca, `Microsoft.AspNetCore.App` aşağıdaki alt bileşenleri içeriyordu:</span><span class="sxs-lookup"><span data-stu-id="3fbe8-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="3fbe8-113">Json.NET`Newtonsoft.Json`( )</span><span class="sxs-lookup"><span data-stu-id="3fbe8-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="3fbe8-114">Varlık Çerçeve Çekirdeği (montajlar `Microsoft.EntityFrameworkCore.`ile önceden belirlenmiş)</span><span class="sxs-lookup"><span data-stu-id="3fbe8-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="3fbe8-115">Roslyn`Microsoft.CodeAnalysis`( )</span><span class="sxs-lookup"><span data-stu-id="3fbe8-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3fbe8-116">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3fbe8-116">New behavior</span></span>

<span data-ttu-id="3fbe8-117">Artık başvuru, `Microsoft.AspNetCore.App` proje `<PackageReference>` dosyasında bir öğe gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="3fbe8-118">.NET Core `<FrameworkReference>`SDK, kullanımını değiştiren yeni bir öğeyi `<PackageReference>`destekler.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="3fbe8-119">Daha fazla bilgi için [dotnet/aspnetcore#3612'ye](https://github.com/dotnet/aspnetcore/issues/3612)bakın.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="3fbe8-120">NuGet paketleri olarak Entity Framework Core gemileri.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="3fbe8-121">Bu değişiklik, gönderi modelini .NET'teki diğer tüm veri erişim kitaplıklarıyla hizalar.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="3fbe8-122">Çeşitli .NET platformlarını desteklerken yenilik yapmaya devam etmek için en basit yolu Entity Framework Core sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="3fbe8-123">Entity Framework Core'un paylaşılan çerçevenin dışına taşınmasının, Microsoft tarafından geliştirilen, desteklenen ve hizmet verilen kitaplık olarak durumu üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="3fbe8-124">[.NET Core destek politikası](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) bunu karşılamaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="3fbe8-125">Json.NET ve Entity Framework Core ASP.NET Core ile çalışmaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="3fbe8-126">Ancak, ortak çerçeveye dahil edilmeyecekler.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="3fbe8-127">Daha fazla bilgi için [.NET Core 3.0'daki JSON'un geleceği](https://github.com/dotnet/announcements/issues/90)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="3fbe8-128">Ayrıca paylaşılan çerçeveden kaldırılan [ikililerin tam listesine](https://github.com/dotnet/aspnetcore/issues/3755) bakın.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3fbe8-129">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3fbe8-129">Reason for change</span></span>

<span data-ttu-id="3fbe8-130">Bu değişiklik, NuGet `Microsoft.AspNetCore.App` paketleri ve paylaşılan çerçeveler arasındaki yinelemenin tüketimini kolaylaştırır ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="3fbe8-131">Bu değişiklik için motivasyon hakkında daha fazla bilgi için, [bu blog yazısı](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3fbe8-132">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3fbe8-132">Recommended action</span></span>

<span data-ttu-id="3fbe8-133">Projelerin, derlemeleri NuGet paketleri `Microsoft.AspNetCore.App` olarak tüketmesi gerekli olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="3fbe8-134">ASP.NET Core paylaşılan çerçevesinin hedeflemesini ve kullanımını kolaylaştırmak için, Core 1.0'ASP.NET dan bu yana gönderilen birçok NuGet paketi artık üretilmemaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="3fbe8-135">Bu paketlerin sağladığı API'ler, bir `<FrameworkReference>` `Microsoft.AspNetCore.App`to kullanarak uygulamalar için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="3fbe8-136">Yaygın API örnekleri kerkenez, MVC ve Razor içerir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="3fbe8-137">Bu değişiklik, ASP.NET Core `Microsoft.AspNetCore.App` 2.x'te başvurulan tüm ikili dosyalar için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="3fbe8-138">Önemli istisnalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fbe8-138">Notable exceptions include:</span></span>

- <span data-ttu-id="3fbe8-139">`Microsoft.Extensions`.NET Standard'ı hedeflemeye devam eden kitaplıklar https://github.com/dotnet/extensions)NuGet paketleri olarak kullanılabilir (bkz.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="3fbe8-140">Bir parçası olmayan ASP.NET Core ekibi tarafından `Microsoft.AspNetCore.App`üretilen API'ler.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="3fbe8-141">Örneğin, aşağıdaki bileşenler NuGet paketleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3fbe8-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="3fbe8-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="3fbe8-142">Entity Framework Core</span></span>
  - <span data-ttu-id="3fbe8-143">Üçüncü taraf tümleştirmesağlayan API'ler</span><span class="sxs-lookup"><span data-stu-id="3fbe8-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="3fbe8-144">Deneysel özellikler</span><span class="sxs-lookup"><span data-stu-id="3fbe8-144">Experimental features</span></span>
  - <span data-ttu-id="3fbe8-145">[Paylaşılan çerçevede olması gereken gereksinimleri yerine getiremeyen bağımlılıklara](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md) sahip API'ler</span><span class="sxs-lookup"><span data-stu-id="3fbe8-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="3fbe8-146">Json.NET desteğini koruyan MVC uzantıları.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="3fbe8-147">Json.NET ve MVC'yi kullanarak desteklemek için NuGet paketi olarak bir API sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="3fbe8-148">SignalR .NET istemcisi .NET Standard'ı desteklemeye ve NuGet paketi olarak göndermeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="3fbe8-149">Xamarin ve UWP gibi birçok .NET çalışma zamanında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="3fbe8-150">Daha fazla bilgi için bkz: [3.0'daki paylaşılan çerçeve derlemeleri için paketleri üretmeyi durdurun.](https://github.com/dotnet/aspnetcore/issues/3756)</span><span class="sxs-lookup"><span data-stu-id="3fbe8-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="3fbe8-151">Tartışma için [dotnet/aspnetcore#3757'ye](https://github.com/dotnet/aspnetcore/issues/3757)bakın.</span><span class="sxs-lookup"><span data-stu-id="3fbe8-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="3fbe8-152">Kategori</span><span class="sxs-lookup"><span data-stu-id="3fbe8-152">Category</span></span>

<span data-ttu-id="3fbe8-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3fbe8-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3fbe8-154">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3fbe8-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
