---
title: ASP.NET Web Forms 'den Blazor 'ye geçiş
description: Mevcut bir ASP.NET Web Forms uygulamasını Blazor 'e geçirmeye nasıl yaklaşımınızı öğrenin.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 78742fc0d998a70c6e3992041d1fa62f2fe53f39
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520276"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="0d237-103">ASP.NET Web Forms 'den Blazor 'ye geçiş</span><span class="sxs-lookup"><span data-stu-id="0d237-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0d237-104">Kod tabanının ASP.NET Web Forms 'den Blazor 'e geçirilmesi, planlamayı gerektiren zaman alan bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="0d237-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="0d237-105">Bu bölümde işlem özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0d237-105">This chapter outlines the process.</span></span> <span data-ttu-id="0d237-106">Geçişi kolaylaştırmaya yönelik bir şey, uygulamanın, uygulama modelinde (Bu durumda Web Forms) iş mantığındaki bir *N katmanlı* mimariye uyduğundan emin olunması olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="0d237-107">Katmanlara yönelik bu mantıksal ayrım, .NET Core ve Blazor 'a ne kadar taşınabilmesini temizler.</span><span class="sxs-lookup"><span data-stu-id="0d237-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="0d237-108">Bu örnekte, [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) 'Da bulunan eShop uygulaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d237-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="0d237-109">eShop, form girişi ve doğrulaması aracılığıyla CRUD özellikleri sağlayan bir katalog hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="0d237-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="0d237-110">Çalışma uygulaması neden Blazor 'e geçirilir?</span><span class="sxs-lookup"><span data-stu-id="0d237-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="0d237-111">Birçok kez ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d237-111">Many times, there's no need.</span></span> <span data-ttu-id="0d237-112">ASP.NET Web Forms, birçok yıl boyunca desteklenmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="0d237-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="0d237-113">Ancak, Blazor 'in sağladığı özelliklerin birçoğu yalnızca geçirilmiş bir uygulamada desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0d237-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="0d237-114">Bu tür özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0d237-114">Such features include:</span></span>

- <span data-ttu-id="0d237-115">Çerçevede `Span<T>` gibi performans iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="0d237-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="0d237-116">WebAssembly olarak çalıştırma olanağı</span><span class="sxs-lookup"><span data-stu-id="0d237-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="0d237-117">Linux ve macOS için platformlar arası destek</span><span class="sxs-lookup"><span data-stu-id="0d237-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="0d237-118">Diğer uygulamaları etkilemeden uygulama yerel dağıtımı veya paylaşılan çerçeve dağıtımı</span><span class="sxs-lookup"><span data-stu-id="0d237-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="0d237-119">Bu veya diğer yeni özellikler yeterince etkileyici ise, uygulamayı geçirmede bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="0d237-120">Geçiş farklı şekiller alabilir; Bu, tüm uygulama veya yalnızca değişiklik gerektiren belirli uç noktalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="0d237-121">Geçiş kararı, sonuçta geliştirici tarafından çözülmesi gereken iş sorunlarına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0d237-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="0d237-122">Sunucu tarafı ve istemci tarafı barındırma</span><span class="sxs-lookup"><span data-stu-id="0d237-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="0d237-123">[Barındırma modelleri](hosting-models.md) bölümünde açıklandığı gibi, bir Blazor uygulaması iki farklı şekilde barındırılabilir: sunucu tarafı ve istemci tarafı.</span><span class="sxs-lookup"><span data-stu-id="0d237-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="0d237-124">Sunucu tarafı modeli, sunucuda herhangi bir gerçek kod çalıştırırken DOM güncelleştirmelerini yönetmek için ASP.NET Core SignalR bağlantılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="0d237-125">İstemci tarafı modeli bir tarayıcı içinde WebAssembly olarak çalışır ve sunucu bağlantısı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0d237-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="0d237-126">Belirli bir uygulama için en iyi sonucu etkileyebilecek birçok fark vardır:</span><span class="sxs-lookup"><span data-stu-id="0d237-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="0d237-127">WebAssembly olarak çalıştırmak hala geliştirme aşamasındadır ve geçerli zamanda tüm özellikleri (iş parçacığı oluşturma gibi) desteklemeyebilir</span><span class="sxs-lookup"><span data-stu-id="0d237-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="0d237-128">İstemci ile sunucu arasındaki geveze iletişimi, sunucu tarafı modunda gecikme sorunlarına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="0d237-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="0d237-129">Veritabanlarına ve iç veya korumalı hizmetlere erişim, istemci tarafı barındırma ile ayrı bir hizmet gerektirir</span><span class="sxs-lookup"><span data-stu-id="0d237-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="0d237-130">Yazma sırasında, sunucu tarafı modeli Web Forms daha yakından benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0d237-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="0d237-131">Bu bölümün çoğu, üretime hazırsa da sunucu tarafı barındırma modeline odaklanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="0d237-132">Yeni bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d237-132">Create a new project</span></span>

<span data-ttu-id="0d237-133">Bu ilk geçiş adımı yeni bir proje oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0d237-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="0d237-134">Bu proje türü, .NET Core SDK stili projelerine dayalıdır ve önceki proje biçimlerinde kullanılan ortak alanının çoğunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d237-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="0d237-135">Daha fazla ayrıntı için lütfen [Proje yapısındaki](project-structure.md)bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="0d237-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="0d237-136">Proje oluşturulduktan sonra, önceki projede kullanılan kitaplıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="0d237-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="0d237-137">Daha eski Web Forms projelerinde, gerekli NuGet paketlerini listelemek için *Packages. config* dosyasını kullanmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d237-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="0d237-138">Yeni SDK stili projesinde, *Packages. config* proje dosyasındaki `<PackageReference>` öğeleriyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d237-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="0d237-139">Bu yaklaşımın bir avantajı, tüm bağımlılıkların geçişli olarak yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d237-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="0d237-140">Yalnızca ilgilendiğiniz en üst düzey bağımlılıkları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="0d237-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="0d237-141">Kullandığınız bağımlılıkların birçoğu .NET Core için Entity Framework 6 ve Log4net dahil olmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="0d237-142">.NET Core veya .NET Standard sürümü yoksa, .NET Framework sürüm genellikle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="0d237-143">Mesafe, farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-143">Your mileage may vary.</span></span> <span data-ttu-id="0d237-144">.NET Core 'da kullanılamayan API 'leri, çalışma zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0d237-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="0d237-145">Visual Studio bu tür paketleri size bildirir.</span><span class="sxs-lookup"><span data-stu-id="0d237-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="0d237-146">Projenin **Başvurular** düğümünde **Çözüm Gezgini**sarı bir simge görünür.</span><span class="sxs-lookup"><span data-stu-id="0d237-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="0d237-147">Blazor tabanlı eShop projesinde, yüklü olan paketleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d237-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="0d237-148">Daha önce, projede kullanılan her pakette listelenen *Packages. config* dosyası, neredeyse 50 satır uzunluğuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="0d237-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="0d237-149">*Packages. config* kod parçacığı:</span><span class="sxs-lookup"><span data-stu-id="0d237-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="0d237-150">@No__t_0 öğesi tüm gerekli bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="0d237-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="0d237-151">İhtiyaç duyduğunuz bu paketlerin hangisinin dahil edileceğini belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="0d237-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="0d237-152">Bazı `<package>` öğeleri, gereken bağımlılıkların ihtiyaçlarını karşılamak için yalnızca listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d237-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="0d237-153">Blazor projesi, proje dosyasındaki bir `<ItemGroup>` öğesi içinde gerekli olan bağımlılıkları listeler:</span><span class="sxs-lookup"><span data-stu-id="0d237-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="0d237-154">Web Forms geliştiricilerin ömrünü basitleştiren bir NuGet paketi [Windows Uyumluluk paketidir](/dotnet/core/porting/windows-compat-pack).</span><span class="sxs-lookup"><span data-stu-id="0d237-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](/dotnet/core/porting/windows-compat-pack).</span></span> <span data-ttu-id="0d237-155">.NET Core platformlar arası olsa da bazı özellikler yalnızca Windows 'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="0d237-156">Windows 'a özgü özellikler, uyumluluk paketi yüklenerek kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="0d237-157">Bu özelliklere örnek olarak kayıt defteri, WMI ve dizin hizmetleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="0d237-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="0d237-158">Paket, 20.000 API etrafında ekleme yapar ve çok daha bildiğiniz hizmetleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d237-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="0d237-159">EShop projesi, uyumluluk paketi gerektirmez; Ancak projeleriniz Windows 'a özgü özellikler kullanıyorsa, paket geçiş çalışmalarını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0d237-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="0d237-160">Başlatma işlemini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="0d237-160">Enable startup process</span></span>

<span data-ttu-id="0d237-161">Blazor için başlangıç işlemi Web Forms ' den değişmiştir ve diğer ASP.NET Core Hizmetleri için benzer bir kuruluma uyar.</span><span class="sxs-lookup"><span data-stu-id="0d237-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="0d237-162">Barındırılan sunucu tarafında, Blazor bileşenleri normal ASP.NET Core uygulamasının bir parçası olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0d237-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="0d237-163">WebAssembly ile tarayıcıda barındırıldığında, Blazor bileşenleri benzer bir barındırma modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="0d237-164">Bunun farkı, bileşenlerin arka uç işlemlerinden herhangi birinden ayrı bir hizmet olarak çalıştırılmaktır.</span><span class="sxs-lookup"><span data-stu-id="0d237-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="0d237-165">Her iki durumda da başlatma benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0d237-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="0d237-166">*Global.asax.cs* dosyası Web Forms projeler için varsayılan başlangıç sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="0d237-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="0d237-167">EShop projesinde, bu dosya denetim (IOC) kapsayıcısının Inversion öğesini yapılandırır ve uygulamanın veya isteğin çeşitli yaşam döngüsü olaylarını işler.</span><span class="sxs-lookup"><span data-stu-id="0d237-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="0d237-168">Bu olaylardan bazıları ara yazılım (örneğin, `Application_BeginRequest`) ile işlenir.</span><span class="sxs-lookup"><span data-stu-id="0d237-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="0d237-169">Diğer olaylar, bağımlılık ekleme (dı) aracılığıyla belirli Hizmetleri geçersiz kılmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0d237-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="0d237-170">Örnek olarak, eShop için *Global.asax.cs* dosyası aşağıdaki kodu içerir:</span><span class="sxs-lookup"><span data-stu-id="0d237-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="0d237-171">Yukarıdaki dosya, sunucu tarafı Blazor `Startup` sınıfı olur:</span><span class="sxs-lookup"><span data-stu-id="0d237-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="0d237-172">Web Forms fark ettiğiniz önemli bir değişiklik, dı 'nin göze çarkadır.</span><span class="sxs-lookup"><span data-stu-id="0d237-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="0d237-173">DI, ASP.NET Core tasarımında bir temel prensibi ilkesidir.</span><span class="sxs-lookup"><span data-stu-id="0d237-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="0d237-174">ASP.NET Core çerçevesinin neredeyse tüm yönlerini özelleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="0d237-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="0d237-175">Birçok senaryo için kullanılabilen yerleşik bir hizmet sağlayıcısı da vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="0d237-176">Daha fazla özelleştirme gerekliyse, bu, çok sayıda topluluk projesi tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="0d237-177">Örneğin, üçüncü taraf dı kitaplığı yatırımınızdan ileri taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d237-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="0d237-178">Özgün eShop uygulamasında, oturum yönetimi için bir yapılandırma vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="0d237-179">Sunucu tarafı Blazor iletişim için ASP.NET Core SignalR kullandığından, bağlantılar bir HTTP bağlamından bağımsız olarak gerçekleşemediğinden oturum durumu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0d237-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="0d237-180">Oturum durumunu kullanan bir uygulama, bir Blazor uygulaması olarak çalışmadan önce yeniden mimari gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0d237-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="0d237-181">Uygulama başlatma hakkında daha fazla bilgi için bkz. [uygulama başlatma](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="0d237-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="0d237-182">HTTP modüllerini ve işleyicileri ara yazılıma geçirme</span><span class="sxs-lookup"><span data-stu-id="0d237-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="0d237-183">Http modülleri ve işleyicileri, HTTP isteği ardışık düzenini denetlemek için Web Forms içindeki yaygın desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="0d237-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="0d237-184">@No__t_0 veya `IHttpHandler` uygulayan sınıflar kaydedilebilir ve gelen istekleri işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="0d237-185">Web Forms, *Web. config* dosyasındaki modülleri ve işleyicileri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0d237-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="0d237-186">Web Forms Ayrıca uygulama yaşam döngüsü olay işlemeye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0d237-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="0d237-187">ASP.NET Core bunun yerine ara yazılım kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="0d237-188">Middlewares, `Startup` sınıfının `Configure` metoduna kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-188">Middlewares are registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="0d237-189">Ara yazılım yürütme sırası, kayıt sırasına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0d237-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="0d237-190">[Başlangıç Işlemini etkinleştir](#enable-startup-process) bölümünde, `Application_BeginRequest` yöntemi olarak Web Forms bir yaşam döngüsü olayı tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="0d237-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="0d237-191">Bu olay ASP.NET Core ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0d237-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="0d237-192">Bu davranışı gerçekleştirmenin bir yolu, ara yazılımı *Startup.cs* File örneğinde görüldüğü gibi uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="0d237-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="0d237-193">Bu ara yazılım aynı mantığı yapar ve denetimi, ara yazılım ardışık düzeninde bir sonraki işleyiciye aktarır.</span><span class="sxs-lookup"><span data-stu-id="0d237-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="0d237-194">Modül ve işleyicileri geçirme hakkında daha fazla bilgi için bkz. [http işleyicilerini ve modülleri ASP.NET Core ara yazılıma geçirme](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="0d237-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="0d237-195">Statik dosyaları geçirme</span><span class="sxs-lookup"><span data-stu-id="0d237-195">Migrate static files</span></span>

<span data-ttu-id="0d237-196">Statik dosyalara (örneğin, HTML, CSS, resim ve JavaScript) sahip olmak için dosyalar, ara yazılım tarafından sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d237-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="0d237-197">@No__t_0 yöntemi çağrılması, Web kök yolundan statik dosya sunma imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="0d237-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="0d237-198">Varsayılan Web kök dizini *Wwwroot*, ancak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="0d237-199">EShop 'ın `Startup` sınıfının `Configure` yöntemine dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d237-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="0d237-200">EShop projesi, temel statik dosya erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0d237-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="0d237-201">Statik dosya erişimi için kullanılabilen birçok özelleştirme vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="0d237-202">Varsayılan dosyaların veya bir dosya tarayıcısının etkinleştirilmesi hakkında daha fazla bilgi için [ASP.NET Core Içindeki statik dosyalar](/aspnet/core/fundamentals/static-files)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0d237-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="0d237-203">Çalışma zamanı paketleme ve küçültmeye yönelik kurulumu geçirme</span><span class="sxs-lookup"><span data-stu-id="0d237-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="0d237-204">Paketleme ve en iyi duruma getirme, belirli dosya türlerini almak üzere sunucu isteklerinin sayısını ve boyutunu azaltmak için performans iyileştirme tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="0d237-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="0d237-205">JavaScript ve CSS genellikle istemciye gönderilmeden önce bir dizi paketleme veya küçültmeye göre daha fazla gider.</span><span class="sxs-lookup"><span data-stu-id="0d237-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="0d237-206">ASP.NET Web Forms içinde, bu iyileştirmeler çalışma zamanında işlenir.</span><span class="sxs-lookup"><span data-stu-id="0d237-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="0d237-207">Optimizasyon kuralları bir *App_Start/paketleme Liconfig. cs* dosyası olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="0d237-208">ASP.NET Core, daha açıklayıcı bir yaklaşım benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="0d237-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="0d237-209">Bir dosya, Mini olarak kullanılacak dosyaları ve belirli bir küçültmeye yönelik ayarları listeler.</span><span class="sxs-lookup"><span data-stu-id="0d237-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="0d237-210">Paketleme ve küçültmeye yönelik daha fazla bilgi için, bkz. [ASP.NET Core statik varlıkları paketleme ve](/aspnet/core/client-side/bundling-and-minification)azaltma.</span><span class="sxs-lookup"><span data-stu-id="0d237-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="0d237-211">ASPX sayfalarını geçirme</span><span class="sxs-lookup"><span data-stu-id="0d237-211">Migrate ASPX pages</span></span>

<span data-ttu-id="0d237-212">Web Forms uygulamasındaki bir sayfa *. aspx* uzantılı bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="0d237-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="0d237-213">Bir Web Forms sayfası, genellikle Blazor ' deki bir bileşenle eşleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="0d237-214">Bir Blazor bileşeni *. Razor* uzantılı bir dosyada yazılır.</span><span class="sxs-lookup"><span data-stu-id="0d237-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="0d237-215">EShop projesi için beş sayfa Razor sayfasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="0d237-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="0d237-216">Örneğin, Ayrıntılar görünümü Web Forms projesindeki üç dosyadan oluşur: *details. aspx*, *details.aspx.cs*ve *details.aspx.Designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="0d237-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="0d237-217">Blazor 'e dönüştürürken, arka plan kodu ve biçimlendirme *details. Razor*içinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="0d237-218">Razor derlemesi ( *. Designer.cs* dosyaları için eşdeğer) *obj* dizininde depolanır ve varsayılan olarak **Çözüm Gezgini**görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="0d237-219">Web Forms sayfası aşağıdaki biçimlendirmeden oluşur:</span><span class="sxs-lookup"><span data-stu-id="0d237-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="0d237-220">Önceki biçimlendirmenin arka plan kodu aşağıdaki kodu içerir:</span><span class="sxs-lookup"><span data-stu-id="0d237-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="0d237-221">Blazor ' e dönüştürüldüğünde, Web Forms sayfası aşağıdaki koda çevirir:</span><span class="sxs-lookup"><span data-stu-id="0d237-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="0d237-222">Kodun ve biçimlendirmenin aynı dosyada olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0d237-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="0d237-223">Gerekli hizmetlere `@inject` özniteliğiyle erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="0d237-224">@No__t_0 yönergesine göre, bu sayfaya `Catalog/Details/{id}` rotasında erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="0d237-225">Yolun `{id}` yer tutucunun değeri bir tamsayı ile kısıtlanıyor.</span><span class="sxs-lookup"><span data-stu-id="0d237-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="0d237-226">[Yönlendirme](pages-routing-layouts.md) bölümünde açıklandığı gibi, Web Forms aksine bir Razor bileşeni, kendi yolunu ve dahil edilen tüm parametreleri açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d237-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="0d237-227">Birçok Web Forms denetimi Blazor içinde tam karşılıklarıyla eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="0d237-228">Genellikle aynı amacı sunan eşdeğer bir HTML kod parçacığı vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="0d237-229">Örneğin, `<asp:Label />` denetimi bir HTML `<label>` öğesi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="0d237-230">Blazor 'de model doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0d237-230">Model validation in Blazor</span></span>

<span data-ttu-id="0d237-231">Web Forms kodunuz doğrulamayı içeriyorsa, az sayıda değişiklik ile sahip olduğunuz kadarını aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d237-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="0d237-232">Blazor ' de çalıştırmanın bir avantajı, aynı doğrulama mantığının özel JavaScript gerekmeden çalıştırılmamasının bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="0d237-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="0d237-233">Veri ek açıklamaları kolay model doğrulamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d237-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="0d237-234">Örneğin, *Create. aspx* sayfasında doğrulama içeren bir veri girişi formu vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="0d237-235">Örnek parçacığı şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="0d237-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="0d237-236">Blazor ' de, eşdeğer biçimlendirme bir *Create. Razor* dosyasında verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d237-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>
    
    ...
</EditForm>
```

<span data-ttu-id="0d237-237">@No__t_0 bağlamı doğrulama desteğini içerir ve girişin etrafında sarmalanabilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="0d237-238">Veri ek açıklamaları, doğrulama eklemenin yaygın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="0d237-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="0d237-239">Bu tür doğrulama desteği `DataAnnotationsValidator` bileşeni aracılığıyla eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="0d237-240">Bu mekanizma hakkında daha fazla bilgi için bkz. [ASP.NET Core Blazor Forms and Validation](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="0d237-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="0d237-241">Yerleşik Web Forms denetimlerini geçirme</span><span class="sxs-lookup"><span data-stu-id="0d237-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="0d237-242">*Bu içerik yakında geliyor.*</span><span class="sxs-lookup"><span data-stu-id="0d237-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="0d237-243">Yapılandırmayı geçir</span><span class="sxs-lookup"><span data-stu-id="0d237-243">Migrate configuration</span></span>

<span data-ttu-id="0d237-244">Web Forms bir projede, yapılandırma verileri genellikle *Web. config* dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="0d237-245">Yapılandırma verilerine `ConfigurationManager` ile erişilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="0d237-246">Hizmetler genellikle nesneleri ayrıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0d237-246">Services were often required to parse objects.</span></span> <span data-ttu-id="0d237-247">.NET Framework 4.7.2 ile, `ConfigurationBuilders` aracılığıyla yapılandırma için bileşim eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d237-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="0d237-248">Bu oluşturucular, geliştiricilerin gerekli değerleri almak için çalışma zamanında oluşturulan yapılandırma için çeşitli kaynaklar eklemesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="0d237-249">ASP.NET Core, uygulamanız ve dağıtımınız tarafından kullanılan yapılandırma kaynağını veya kaynaklarını tanımlamanızı sağlayan esnek bir yapılandırma sistemi sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="0d237-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="0d237-250">Web Forms uygulamanızda kullandığınız `ConfigurationBuilder` altyapısı, ASP.NET Core yapılandırma sisteminde kullanılan kavramlardan sonra modellenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d237-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="0d237-251">Aşağıdaki kod parçacığında Web Forms eShop projesinin yapılandırma değerlerini depolamak için *Web. config* 'i nasıl kullandığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0d237-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
```

<span data-ttu-id="0d237-252">Veritabanı bağlantı dizeleri, *Web. config*içinde depolanacak gizli dizileri için yaygındır. Gizli dizileri, kaynak denetimi gibi güvenli olmayan konumlarda kalıcı olarak kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="0d237-253">ASP.NET Core üzerinde Blazor, önceki XML tabanlı yapılandırma aşağıdaki JSON ile değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d237-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="0d237-254">JSON varsayılan yapılandırma biçimidir; Ancak, ASP.NET Core XML gibi birçok diğer biçimi destekler.</span><span class="sxs-lookup"><span data-stu-id="0d237-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="0d237-255">Ayrıca, topluluk tarafından desteklenen birkaç biçim vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="0d237-256">Blazor projesinin `Startup` sınıfındaki Oluşturucu, Oluşturucu ekleme olarak bilinen bir DI tekniği aracılığıyla bir `IConfiguration` örneğini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="0d237-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="0d237-257">Varsayılan olarak, ortam değişkenleri, JSON dosyaları (*appSettings. JSON* ve *appSettings. { Environment}. JSON*) ve komut satırı seçenekleri yapılandırma nesnesinde geçerli yapılandırma kaynakları olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="0d237-258">Yapılandırma kaynaklarına `Configuration[key]` aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="0d237-259">Daha gelişmiş bir teknik, yapılandırma verilerini nesnelere bağlamak için seçenekler örüntüsünün kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d237-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="0d237-260">Yapılandırma ve seçenekler düzeniyle ilgili daha fazla bilgi için sırasıyla ASP.NET Core [ASP.NET Core](/aspnet/core/fundamentals/configuration/) ve [Seçenekler](/aspnet/core/fundamentals/configuration/options)düzeninde yapılandırma konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="0d237-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="0d237-261">Veri erişimini geçirme</span><span class="sxs-lookup"><span data-stu-id="0d237-261">Migrate data access</span></span>

<span data-ttu-id="0d237-262">Veri erişimi, tüm uygulamaların önemli bir yönüdür.</span><span class="sxs-lookup"><span data-stu-id="0d237-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="0d237-263">EShop projesi, katalog bilgilerini bir veritabanında depolar ve Entity Framework (EF) 6 ile verileri alır.</span><span class="sxs-lookup"><span data-stu-id="0d237-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="0d237-264">.NET Core 3,0 ' de EF 6 desteklendiğinden, proje onu kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="0d237-265">Aşağıdaki EF ile ilgili değişiklikler eShop için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0d237-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="0d237-266">.NET Framework, `DbContext` nesnesi *Name = ConnectionString* biçiminde bir dize kabul eder ve `ConfigurationManager.AppSettings[ConnectionString]` bağlantı dizesini bağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d237-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="0d237-267">.NET Core 'da bu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0d237-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="0d237-268">Bağlantı dizesinin sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d237-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="0d237-269">Veritabanına zaman uyumlu bir şekilde erişildi.</span><span class="sxs-lookup"><span data-stu-id="0d237-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="0d237-270">Bu işlem çalışsa da ölçeklenebilirlik düşebilir.</span><span class="sxs-lookup"><span data-stu-id="0d237-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="0d237-271">Bu mantık zaman uyumsuz bir modele taşınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d237-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="0d237-272">Veri kümesi bağlama için aynı yerel destek olmasa da Blazor, C# desteğiyle Razor sayfasında esneklik ve güç sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d237-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="0d237-273">Örneğin, hesaplamalar yapabilir ve sonucu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d237-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="0d237-274">Blazor içindeki veri desenleri hakkında daha fazla bilgi için bkz. [veri erişimi](data.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="0d237-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="0d237-275">Mimari değişiklikler</span><span class="sxs-lookup"><span data-stu-id="0d237-275">Architectural changes</span></span>

<span data-ttu-id="0d237-276">Son olarak, Blazor 'e geçiş yaparken göz önünde bulundurmanız gereken bazı önemli mimari farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="0d237-277">Bu değişikliklerin çoğu, .NET Core veya ASP.NET Core temel alınarak herhangi bir şey için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0d237-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="0d237-278">Blazor .NET Core üzerinde oluşturulduğundan, .NET Core üzerinde destek sağlamaya yönelik hususlar vardır.</span><span class="sxs-lookup"><span data-stu-id="0d237-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="0d237-279">Bazı önemli değişikliklerden bazıları aşağıdaki özelliklerin kaldırılmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="0d237-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="0d237-280">Birden çok AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d237-280">Multiple AppDomains</span></span>
- <span data-ttu-id="0d237-281">Uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="0d237-281">Remoting</span></span>
- <span data-ttu-id="0d237-282">Kod Erişimi Güvenliği (CAS)</span><span class="sxs-lookup"><span data-stu-id="0d237-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="0d237-283">Güvenlik saydamlığı</span><span class="sxs-lookup"><span data-stu-id="0d237-283">Security Transparency</span></span>

<span data-ttu-id="0d237-284">.NET Core üzerinde çalışmayı desteklemek için gereken değişiklikleri belirlemek için teknikler hakkında daha fazla bilgi için bkz. [.NET Framework kodunuzun bağlantı noktası, .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="0d237-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="0d237-285">ASP.NET Core, ASP.NET 'in yeniden oluşturulmuş bir sürümüdür ve başlangıçta belirgin bir şekilde görünmeyebilir bazı değişiklikler içerir.</span><span class="sxs-lookup"><span data-stu-id="0d237-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="0d237-286">Ana değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0d237-286">The main changes are:</span></span>

- <span data-ttu-id="0d237-287">@No__t_0, `Thread.CurrentPrincipal` veya diğer statik erişimciler olmadığı anlamına gelen hiçbir eşitleme bağlamı yok</span><span class="sxs-lookup"><span data-stu-id="0d237-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="0d237-288">Gölge kopyalama yok</span><span class="sxs-lookup"><span data-stu-id="0d237-288">No shadow copying</span></span>
- <span data-ttu-id="0d237-289">İstek kuyruğu yok</span><span class="sxs-lookup"><span data-stu-id="0d237-289">No request queue</span></span>

<span data-ttu-id="0d237-290">ASP.NET Core çok sayıda işlem zaman uyumsuzdur ve g/ç bağlantılı görevlerin daha kolay bir şekilde yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d237-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="0d237-291">İş parçacığı havuzu kaynaklarını hızlıca tüketebilen `Task.Wait()` veya `Task.GetResult()` kullanarak hiçbir şekilde engellenmemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0d237-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="0d237-292">Geçiş sonucu</span><span class="sxs-lookup"><span data-stu-id="0d237-292">Migration conclusion</span></span>

<span data-ttu-id="0d237-293">Bu noktada, bir Web Forms projesinin Blazor 'e taşınması hakkında birçok örnek gördünüz.</span><span class="sxs-lookup"><span data-stu-id="0d237-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="0d237-294">Tam bir örnek için bkz. [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) projesi.</span><span class="sxs-lookup"><span data-stu-id="0d237-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="0d237-295">Öncekini</span><span class="sxs-lookup"><span data-stu-id="0d237-295">Previous</span></span>](security-authentication-authorization.md)
