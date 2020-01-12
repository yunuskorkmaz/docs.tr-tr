---
ms.openlocfilehash: 2067ea2a70277d188950c449d3990f4426f69beb
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901965"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="f36a0-101">Paylaşılan çerçeve: Microsoft. AspNetCore. app öğesinden kaldırılan derlemeler</span><span class="sxs-lookup"><span data-stu-id="f36a0-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="f36a0-102">ASP.NET Core 3,0 ' den başlayarak, ASP.NET Core paylaşılan çerçeve (`Microsoft.AspNetCore.App`) yalnızca Microsoft tarafından tam olarak geliştirilen, desteklenen ve hizmet veren birinci taraf derlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f36a0-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f36a0-103">Change description</span></span>

<span data-ttu-id="f36a0-104">ASP.NET Core "Platform" için sınırları yeniden tanımlayarak değişikliği düşünün.</span><span class="sxs-lookup"><span data-stu-id="f36a0-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="f36a0-105">Paylaşılan Framework, [GitHub aracılığıyla herkes tarafından kaynak tarafından](https://github.com/dotnet/source-build) oluşturulabilir ve .NET Core paylaşılan çerçevelerinin mevcut avantajlarını uygulamalarınıza sunmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="f36a0-106">Bazı avantajlar, daha küçük dağıtım boyutu, merkezi düzeltme eki uygulama ve daha hızlı başlangıç süresi içerir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="f36a0-107">Değişikliğin bir parçası olarak, bazı önemli değişiklikler `Microsoft.AspNetCore.App`sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f36a0-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f36a0-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f36a0-108">Version introduced</span></span>

<span data-ttu-id="f36a0-109">3.0</span><span class="sxs-lookup"><span data-stu-id="f36a0-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f36a0-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="f36a0-110">Old behavior</span></span>

<span data-ttu-id="f36a0-111">Proje dosyasındaki `<PackageReference>` bir öğe aracılığıyla `Microsoft.AspNetCore.App` başvurulan projeler.</span><span class="sxs-lookup"><span data-stu-id="f36a0-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="f36a0-112">Ayrıca, `Microsoft.AspNetCore.App` aşağıdaki alt bileşenleri içeriyordu:</span><span class="sxs-lookup"><span data-stu-id="f36a0-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="f36a0-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="f36a0-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="f36a0-114">Entity Framework Core (`Microsoft.EntityFrameworkCore.`ön ekli derlemeler)</span><span class="sxs-lookup"><span data-stu-id="f36a0-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="f36a0-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="f36a0-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f36a0-116">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="f36a0-116">New behavior</span></span>

<span data-ttu-id="f36a0-117">`Microsoft.AspNetCore.App` bir başvuru artık proje dosyasında bir `<PackageReference>` öğesi gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="f36a0-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="f36a0-118">.NET Core SDK, `<PackageReference>`kullanımını değiştiren `<FrameworkReference>`adlı yeni bir öğeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="f36a0-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="f36a0-119">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="f36a0-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="f36a0-120">Entity Framework Core NuGet paketleri olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="f36a0-121">Bu değişiklik, .NET 'teki diğer tüm veri erişim kitaplıklarıyla birlikte teslim modelini hizalar.</span><span class="sxs-lookup"><span data-stu-id="f36a0-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="f36a0-122">Çeşitli .NET platformlarını destekleyerek sürmek devam etmek için en basit yolu Entity Framework Core sağlar.</span><span class="sxs-lookup"><span data-stu-id="f36a0-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="f36a0-123">Entity Framework Core paylaşılan çerçevenin dışına taşınması, Microsoft tarafından geliştirilen, desteklenen ve hizmet verebilir kitaplığı olarak durumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f36a0-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="f36a0-124">[.NET Core destek ilkesi](https://www.microsoft.com/net/platform/support-policy) onu kapsamaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="f36a0-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="f36a0-125">Json.NET ve Entity Framework Core ASP.NET Core ile çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="f36a0-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="f36a0-126">Ancak, paylaşılan çerçeveye dahil edilmezler.</span><span class="sxs-lookup"><span data-stu-id="f36a0-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="f36a0-127">Daha fazla bilgi için [.NET Core 3,0 ' de JSON 'nin geleceğe](https://github.com/dotnet/announcements/issues/90)bakın.</span><span class="sxs-lookup"><span data-stu-id="f36a0-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="f36a0-128">Ayrıca, paylaşılan çerçeveden kaldırılan [ikili dosyaların tüm listesine](https://github.com/dotnet/aspnetcore/issues/3755) bakın.</span><span class="sxs-lookup"><span data-stu-id="f36a0-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f36a0-129">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f36a0-129">Reason for change</span></span>

<span data-ttu-id="f36a0-130">Bu değişiklik, `Microsoft.AspNetCore.App` tüketimini basitleştirir ve NuGet paketleri ile paylaşılan Çerçeveler arasındaki yinelemeyi azaltır.</span><span class="sxs-lookup"><span data-stu-id="f36a0-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="f36a0-131">Bu değişiklik için mosyon hakkında daha fazla bilgi için [Bu blog gönderisine](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0)bakın.</span><span class="sxs-lookup"><span data-stu-id="f36a0-131">For more information on the motivation for this change, see [this blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f36a0-132">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f36a0-132">Recommended action</span></span>

<span data-ttu-id="f36a0-133">Projelerin NuGet paketleri olarak `Microsoft.AspNetCore.App` derlemeleri kullanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f36a0-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="f36a0-134">ASP.NET Core paylaşılan Framework 'ün hedeflediği ve kullanımının basitleşmesini sağlamak için, ASP.NET Core 1,0 ' den itibaren sevk edilen birçok NuGet paketi artık üretilmez.</span><span class="sxs-lookup"><span data-stu-id="f36a0-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="f36a0-135">Bu paketlerin sağladığı API 'Ler, `Microsoft.AspNetCore.App`için `<FrameworkReference>` kullanarak uygulamalar için hala kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="f36a0-136">Ortak API örnekleri Kestrel, MVC ve Razor içerir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="f36a0-137">Bu değişiklik, ASP.NET Core 2. x içinde `Microsoft.AspNetCore.App` tarafından başvurulan tüm ikili dosyalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="f36a0-138">Önemli özel durumlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f36a0-138">Notable exceptions include:</span></span>

- <span data-ttu-id="f36a0-139">hedef .NET Standard devam eden `Microsoft.Extensions` kitaplıkları, NuGet paketleri olarak kullanılabilir (bkz. https://github.com/dotnet/extensions).</span><span class="sxs-lookup"><span data-stu-id="f36a0-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="f36a0-140">`Microsoft.AspNetCore.App`parçası olmayan ASP.NET Core ekibi tarafından oluşturulan API 'Ler.</span><span class="sxs-lookup"><span data-stu-id="f36a0-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="f36a0-141">Örneğin, aşağıdaki bileşenler NuGet paketleri olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="f36a0-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="f36a0-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="f36a0-142">Entity Framework Core</span></span>
  - <span data-ttu-id="f36a0-143">Üçüncü taraf tümleştirme sağlayan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="f36a0-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="f36a0-144">Deneysel özellikler</span><span class="sxs-lookup"><span data-stu-id="f36a0-144">Experimental features</span></span>
  - <span data-ttu-id="f36a0-145">[Paylaşılan çerçevede olması gereken gereksinimleri yerine](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md) getiren bağımlılıklara sahip API 'ler</span><span class="sxs-lookup"><span data-stu-id="f36a0-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="f36a0-146">Json.NET desteğini sağlayan MVC uzantıları.</span><span class="sxs-lookup"><span data-stu-id="f36a0-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="f36a0-147">API, Json.NET ve MVC kullanımını desteklemek için bir NuGet paketi olarak sağlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f36a0-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="f36a0-148">SignalR .NET istemcisi .NET Standard desteklemeye ve bir NuGet paketi olarak göndermeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="f36a0-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="f36a0-149">Xamarin ve UWP gibi birçok .NET çalışma zamanı için kullanılması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f36a0-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="f36a0-150">Daha fazla bilgi için bkz. [3,0 ' de paylaşılan çerçeve derlemeleri için paketleri oluşturmayı durdurma](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="f36a0-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="f36a0-151">Tartışma için bkz. [DotNet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="f36a0-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="f36a0-152">Kategori</span><span class="sxs-lookup"><span data-stu-id="f36a0-152">Category</span></span>

<span data-ttu-id="f36a0-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f36a0-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f36a0-154">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f36a0-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
