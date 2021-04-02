---
title: ASP.NET Web Forms 'den geçiş Blazor
description: Var olan bir ASP.NET Web Forms uygulamasını ' ye geçirmeye nasıl yaklaşımınızı öğrenin Blazor .
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: 893b6f851681ec540629fe160749b2622b6d5440
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509838"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="def88-103">ASP.NET Web Forms 'den geçiş Blazor</span><span class="sxs-lookup"><span data-stu-id="def88-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

<span data-ttu-id="def88-104">Bir kod tabanının ASP.NET Web Forms ' den geçirilmesi Blazor , planlama gerektiren zaman alan bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="def88-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="def88-105">Bu bölümde işlem özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="def88-105">This chapter outlines the process.</span></span> <span data-ttu-id="def88-106">Geçişi kolaylaştırmaya yönelik bir şey, uygulamanın, uygulama modelinde (Bu durumda Web Forms) iş mantığındaki bir *N katmanlı* mimariye uyduğundan emin olunması olabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="def88-107">Katmanlara yönelik bu mantıksal ayrım, .NET Core 'a ve ne kadar taşınabilmesini temizler Blazor .</span><span class="sxs-lookup"><span data-stu-id="def88-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="def88-108">Bu örnekte, [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) 'Da bulunan eShop uygulaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="def88-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="def88-109">eShop, form girişi ve doğrulaması aracılığıyla CRUD özellikleri sağlayan bir katalog hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="def88-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="def88-110">Çalışma uygulaması neden geçirilecek Blazor ?</span><span class="sxs-lookup"><span data-stu-id="def88-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="def88-111">Birçok kez ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="def88-111">Many times, there's no need.</span></span> <span data-ttu-id="def88-112">ASP.NET Web Forms, birçok yıl boyunca desteklenmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="def88-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="def88-113">Ancak, tarafından sağlanan özelliklerin birçoğu Blazor yalnızca geçirilmiş bir uygulamada desteklenir.</span><span class="sxs-lookup"><span data-stu-id="def88-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="def88-114">Bu tür özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="def88-114">Such features include:</span></span>

- <span data-ttu-id="def88-115">Çerçevede performans iyileştirmeleri `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="def88-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="def88-116">Farklı Çalıştır WebAssembly</span><span class="sxs-lookup"><span data-stu-id="def88-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="def88-117">Linux ve macOS için platformlar arası destek</span><span class="sxs-lookup"><span data-stu-id="def88-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="def88-118">Diğer uygulamaları etkilemeden uygulama yerel dağıtımı veya paylaşılan çerçeve dağıtımı</span><span class="sxs-lookup"><span data-stu-id="def88-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="def88-119">Bu veya diğer yeni özellikler yeterince etkileyici ise, uygulamayı geçirmede bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="def88-120">Geçiş farklı şekiller alabilir; Bu, tüm uygulama veya yalnızca değişiklik gerektiren belirli uç noktalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="def88-121">Geçiş kararı, sonuçta geliştirici tarafından çözülmesi gereken iş sorunlarına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="def88-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="def88-122">Sunucu tarafı ve istemci tarafı barındırma</span><span class="sxs-lookup"><span data-stu-id="def88-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="def88-123">[Barındırma modelleri](hosting-models.md) bölümünde açıklandığı gibi, bir Blazor uygulama iki farklı şekilde barındırılabilir: sunucu tarafı ve istemci tarafı.</span><span class="sxs-lookup"><span data-stu-id="def88-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="def88-124">Sunucu tarafı modeli, sunucuda herhangi bir gerçek kod çalıştırırken DOM güncelleştirmelerini yönetmek için ASP.NET Core SignalR bağlantılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="def88-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="def88-125">İstemci tarafı modeli WebAssembly bir tarayıcı içinde olarak çalışır ve sunucu bağlantısı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="def88-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="def88-126">Belirli bir uygulama için en iyi sonucu etkileyebilecek birçok fark vardır:</span><span class="sxs-lookup"><span data-stu-id="def88-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="def88-127">Farklı çalıştırma WebAssembly , geçerli zamanda tüm özellikleri (örneğin, iş parçacığı) desteklemez</span><span class="sxs-lookup"><span data-stu-id="def88-127">Running as WebAssembly doesn't support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="def88-128">İstemci ile sunucu arasındaki geveze iletişimi, sunucu tarafı modunda gecikme sorunlarına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="def88-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="def88-129">Veritabanlarına ve iç veya korumalı hizmetlere erişim, istemci tarafı barındırma ile ayrı bir hizmet gerektirir</span><span class="sxs-lookup"><span data-stu-id="def88-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="def88-130">Yazma sırasında, sunucu tarafı modeli Web Forms daha yakından benzerdir.</span><span class="sxs-lookup"><span data-stu-id="def88-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="def88-131">Bu bölümün çoğu, üretime hazırsa da sunucu tarafı barındırma modeline odaklanır.</span><span class="sxs-lookup"><span data-stu-id="def88-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="def88-132">Yeni proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="def88-132">Create a new project</span></span>

<span data-ttu-id="def88-133">Bu ilk geçiş adımı yeni bir proje oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="def88-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="def88-134">Bu proje türü, .NET SDK stili projelerini temel alır ve önceki proje biçimlerinde kullanılan ortak alanının çoğunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="def88-134">This project type is based on the SDK style projects of .NET and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="def88-135">Daha fazla ayrıntı için lütfen [Proje yapısındaki](project-structure.md)bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="def88-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="def88-136">Proje oluşturulduktan sonra, önceki projede kullanılan kitaplıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="def88-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="def88-137">Daha eski Web Forms projelerinde, gerekli NuGet paketlerini listelemek için *packages.config* dosyasını kullanmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def88-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="def88-138">Yeni SDK stili projesinde *packages.config* `<PackageReference>` Proje dosyasındaki öğelerle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="def88-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="def88-139">Bu yaklaşımın bir avantajı, tüm bağımlılıkların geçişli olarak yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="def88-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="def88-140">Yalnızca ilgilendiğiniz en üst düzey bağımlılıkları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="def88-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="def88-141">Kullandığınız bağımlılıkların birçoğu, .NET için Entity Framework 6 ve Log4net dahil olmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-141">Many of the dependencies you're using are available for .NET, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="def88-142">Kullanılabilir .NET veya .NET Standard sürümü yoksa, .NET Framework sürümü genellikle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-142">If there's no .NET or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="def88-143">Mesafe, farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-143">Your mileage may vary.</span></span> <span data-ttu-id="def88-144">.NET ' te kullanılamayan API 'leri, çalışma zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="def88-144">Any API used that isn't available in .NET causes a runtime error.</span></span> <span data-ttu-id="def88-145">Visual Studio bu tür paketleri size bildirir.</span><span class="sxs-lookup"><span data-stu-id="def88-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="def88-146">Projenin **Başvurular** düğümünde **Çözüm Gezgini** sarı bir simge görünür.</span><span class="sxs-lookup"><span data-stu-id="def88-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="def88-147">BlazorTabanlı eShop projesinde, yüklü olan paketleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def88-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="def88-148">Daha önce, projede kullanılan her pakette listelenen *packages.config* dosyası, neredeyse 50 satır uzunluğuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="def88-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="def88-149">*packages.config* bir kod parçacığı:</span><span class="sxs-lookup"><span data-stu-id="def88-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="def88-150">`<packages>`Öğesi tüm gerekli bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="def88-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="def88-151">İhtiyaç duyduğunuz bu paketlerin hangisinin dahil edileceğini belirlemek zordur.</span><span class="sxs-lookup"><span data-stu-id="def88-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="def88-152">Bazı `<package>` öğeler yalnızca ihtiyaç duyduğunuz bağımlılıkların ihtiyaçlarını karşılamak için listelenir.</span><span class="sxs-lookup"><span data-stu-id="def88-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="def88-153">BlazorProje, proje dosyasındaki bir öğe içinde gerekli olan bağımlılıkları listeler `<ItemGroup>` :</span><span class="sxs-lookup"><span data-stu-id="def88-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.4.4" />
    <PackageReference Include="log4net" Version="2.0.12" />
    <PackageReference Include="Microsoft.Extensions.Logging.Log4Net.AspNetCore" Version="2.2.12" />
</ItemGroup>
```

<span data-ttu-id="def88-154">Web Forms geliştiricilerin ömrünü basitleştiren bir NuGet paketi [Windows Uyumluluk paketidir](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="def88-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="def88-155">.NET platformlar arası olsa da bazı özellikler yalnızca Windows 'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-155">Although .NET is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="def88-156">Windows 'a özgü özellikler, uyumluluk paketi yüklenerek kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="def88-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="def88-157">Bu özelliklere örnek olarak kayıt defteri, WMI ve dizin hizmetleri dahildir.</span><span class="sxs-lookup"><span data-stu-id="def88-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="def88-158">Paket, 20.000 API etrafında ekleme yapar ve çok daha bildiğiniz hizmetleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="def88-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="def88-159">EShop projesi, uyumluluk paketi gerektirmez; Ancak projeleriniz Windows 'a özgü özellikler kullanıyorsa, paket geçiş çalışmalarını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="def88-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="def88-160">Başlatma işlemini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="def88-160">Enable startup process</span></span>

<span data-ttu-id="def88-161">İçin başlatma işlemi Blazor Web Forms ' dan değişmiştir ve diğer ASP.NET Core Hizmetleri için benzer bir kuruluma uyar.</span><span class="sxs-lookup"><span data-stu-id="def88-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="def88-162">Sunucu tarafında barındırılan Blazor Bileşenler, normal ASP.NET Core uygulamasının bir parçası olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="def88-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="def88-163">Tarayıcıda barındırıldığında WebAssembly , Blazor Bileşenler benzer bir barındırma modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="def88-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="def88-164">Bunun farkı, bileşenlerin arka uç işlemlerinden herhangi birinden ayrı bir hizmet olarak çalıştırılmaktır.</span><span class="sxs-lookup"><span data-stu-id="def88-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="def88-165">Her iki durumda da başlatma benzerdir.</span><span class="sxs-lookup"><span data-stu-id="def88-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="def88-166">*Global. asax. cs* dosyası Web Forms projeler için varsayılan başlangıç sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="def88-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="def88-167">EShop projesinde, bu dosya denetim (IOC) kapsayıcısının Inversion öğesini yapılandırır ve uygulamanın veya isteğin çeşitli yaşam döngüsü olaylarını işler.</span><span class="sxs-lookup"><span data-stu-id="def88-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="def88-168">Bu olaylardan bazıları ara yazılım (gibi) ile işlenir `Application_BeginRequest` .</span><span class="sxs-lookup"><span data-stu-id="def88-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="def88-169">Diğer olaylar, bağımlılık ekleme (dı) aracılığıyla belirli Hizmetleri geçersiz kılmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="def88-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="def88-170">Örnek olarak, eShop için *Global. asax. cs* dosyası aşağıdaki kodu içerir:</span><span class="sxs-lookup"><span data-stu-id="def88-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
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

<span data-ttu-id="def88-171">Yukarıdaki dosya, `Startup` sunucu tarafında sınıfı olur Blazor :</span><span class="sxs-lookup"><span data-stu-id="def88-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="def88-172">Web Forms fark ettiğiniz önemli bir değişiklik, dı 'nin göze çarkadır.</span><span class="sxs-lookup"><span data-stu-id="def88-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="def88-173">DI, ASP.NET Core tasarımında bir temel prensibi ilkesidir.</span><span class="sxs-lookup"><span data-stu-id="def88-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="def88-174">ASP.NET Core çerçevesinin neredeyse tüm yönlerini özelleştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="def88-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="def88-175">Birçok senaryo için kullanılabilen yerleşik bir hizmet sağlayıcısı da vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="def88-176">Daha fazla özelleştirme gerekliyse, bu, birçok topluluk projesi tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-176">If more customization is required, it can be supported by many community projects.</span></span> <span data-ttu-id="def88-177">Örneğin, üçüncü taraf dı kitaplığı yatırımınızdan ileri taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def88-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="def88-178">Özgün eShop uygulamasında, oturum yönetimi için bir yapılandırma vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="def88-179">Sunucu tarafı Blazor iletişim için ASP.NET Core SignalR kullandığından, bağlantılar BIR http bağlamından bağımsız olarak gerçekleşemediğinden oturum durumu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="def88-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, the session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="def88-180">Oturum durumunu kullanan bir uygulama, uygulama olarak çalışmadan önce yeniden mimari gerektirir Blazor .</span><span class="sxs-lookup"><span data-stu-id="def88-180">An app that uses the session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="def88-181">Uygulama başlatma hakkında daha fazla bilgi için bkz. [uygulama başlatma](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="def88-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="def88-182">HTTP modüllerini ve işleyicileri ara yazılıma geçirme</span><span class="sxs-lookup"><span data-stu-id="def88-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="def88-183">Http modülleri ve işleyicileri, HTTP isteği ardışık düzenini denetlemek için Web Forms içindeki yaygın desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="def88-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="def88-184">`IHttpModule`Veya `IHttpHandler` ' i uygulayan veya gelen istekleri işleyecek sınıflar.</span><span class="sxs-lookup"><span data-stu-id="def88-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="def88-185">*web.config* dosyasında modül ve işleyicileri yapılandırma Web Forms.</span><span class="sxs-lookup"><span data-stu-id="def88-185">Web Forms configure modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="def88-186">Web Forms Ayrıca uygulama yaşam döngüsü olay işlemeye bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="def88-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="def88-187">ASP.NET Core bunun yerine ara yazılım kullanır.</span><span class="sxs-lookup"><span data-stu-id="def88-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="def88-188">Ara yazılım, `Configure` sınıfının yöntemine kaydedilir `Startup` .</span><span class="sxs-lookup"><span data-stu-id="def88-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="def88-189">Ara yazılım yürütme sırası, kayıt sırasına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="def88-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="def88-190">[Başlatma Işlemini etkinleştir](#enable-startup-process) bölümünde, yöntemi olarak Web Forms bir yaşam döngüsü olayı tetiklenir `Application_BeginRequest` .</span><span class="sxs-lookup"><span data-stu-id="def88-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="def88-191">Bu olay ASP.NET Core ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="def88-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="def88-192">Bu davranışı gerçekleştirmenin bir yolu, *Başlangıç. cs* dosyası örneğinde görüldüğü gibi ara yazılımı uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="def88-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="def88-193">Bu ara yazılım aynı mantığı yapar ve denetimi, ara yazılım ardışık düzeninde bir sonraki işleyiciye aktarır.</span><span class="sxs-lookup"><span data-stu-id="def88-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="def88-194">Modül ve işleyicileri geçirme hakkında daha fazla bilgi için bkz. [http işleyicilerini ve modülleri ASP.NET Core ara yazılıma geçirme](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="def88-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="def88-195">Statik dosyaları geçirme</span><span class="sxs-lookup"><span data-stu-id="def88-195">Migrate static files</span></span>

<span data-ttu-id="def88-196">Statik dosyalara (örneğin, HTML, CSS, resim ve JavaScript) sahip olmak için dosyalar, ara yazılım tarafından sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="def88-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="def88-197">Yöntemi çağırmak, `UseStaticFiles` statik dosyaların Web kök yolundan kullanılmasına izin veriyor.</span><span class="sxs-lookup"><span data-stu-id="def88-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="def88-198">Varsayılan Web kök dizini *Wwwroot*, ancak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="def88-199">`Configure`EShop sınıfının yöntemine dahil edilmiştir `Startup` :</span><span class="sxs-lookup"><span data-stu-id="def88-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="def88-200">EShop projesi, temel statik dosya erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="def88-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="def88-201">Statik dosya erişimi için kullanılabilen birçok özelleştirme vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="def88-202">Varsayılan dosyaların veya bir dosya tarayıcısının etkinleştirilmesi hakkında daha fazla bilgi için [ASP.NET Core Içindeki statik dosyalar](/aspnet/core/fundamentals/static-files)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="def88-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="def88-203">Çalışma zamanı paketleme ve küçültmeye yönelik kurulumu geçirme</span><span class="sxs-lookup"><span data-stu-id="def88-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="def88-204">Paketleme ve en iyi duruma getirme, belirli dosya türlerini almak üzere sunucu isteklerinin sayısını ve boyutunu azaltmak için performans iyileştirme tekniklerdir.</span><span class="sxs-lookup"><span data-stu-id="def88-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="def88-205">JavaScript ve CSS genellikle istemciye gönderilmeden önce bir dizi paketleme veya küçültmeye göre daha fazla gider.</span><span class="sxs-lookup"><span data-stu-id="def88-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="def88-206">ASP.NET Web Forms içinde, bu iyileştirmeler çalışma zamanında işlenir.</span><span class="sxs-lookup"><span data-stu-id="def88-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="def88-207">En iyi duruma getirme kuralları bir *App_Start/paketlemeli bir config.cs* dosyası tanımladı.</span><span class="sxs-lookup"><span data-stu-id="def88-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="def88-208">ASP.NET Core, daha açıklayıcı bir yaklaşım benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="def88-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="def88-209">Bir dosya, Mini olarak kullanılacak dosyaları ve belirli bir küçültmeye yönelik ayarları listeler.</span><span class="sxs-lookup"><span data-stu-id="def88-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="def88-210">Paketleme ve küçültmeye yönelik daha fazla bilgi için, bkz. [ASP.NET Core statik varlıkları paketleme ve](/aspnet/core/client-side/bundling-and-minification)azaltma.</span><span class="sxs-lookup"><span data-stu-id="def88-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="def88-211">ASPX sayfalarını geçirme</span><span class="sxs-lookup"><span data-stu-id="def88-211">Migrate ASPX pages</span></span>

<span data-ttu-id="def88-212">Web Forms uygulamasındaki bir sayfa *. aspx* uzantılı bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="def88-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="def88-213">Bir Web Forms sayfası, genellikle içindeki bir bileşenle eşleştirilebilir Blazor .</span><span class="sxs-lookup"><span data-stu-id="def88-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="def88-214">Bir Blazor bileşen *. Razor* uzantılı bir dosyada yazılır.</span><span class="sxs-lookup"><span data-stu-id="def88-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="def88-215">EShop projesi için beş sayfa Razor sayfasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="def88-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="def88-216">Örneğin, Ayrıntılar görünümü Web Forms projedeki üç dosya içerir: *details. aspx*, *details. aspx. cs* ve *details. aspx. Designer. cs*.</span><span class="sxs-lookup"><span data-stu-id="def88-216">For example, the details view comprises three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="def88-217">Blazor' A dönüştürme yaparken, arka plan kodu ve biçimlendirme *details. Razor* içinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="def88-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="def88-218">Razor derlemesi ( *. Designer. cs* dosyaları ile eşdeğer) *obj* dizininde depolanır ve varsayılan olarak, **Çözüm Gezgini** görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and isn't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="def88-219">Web Forms sayfası aşağıdaki biçimlendirmeden oluşur:</span><span class="sxs-lookup"><span data-stu-id="def88-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="def88-220">Önceki biçimlendirmenin arka plan kodu aşağıdaki kodu içerir:</span><span class="sxs-lookup"><span data-stu-id="def88-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="def88-221">' A dönüştürüldüğünde Blazor , Web Forms sayfası aşağıdaki koda çevirir:</span><span class="sxs-lookup"><span data-stu-id="def88-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="def88-222">Kodun ve biçimlendirmenin aynı dosyada olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="def88-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="def88-223">Gerekli hizmetlere, özniteliğiyle erişilebilir hale getirilir `@inject` .</span><span class="sxs-lookup"><span data-stu-id="def88-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="def88-224">`@page`Yönergeye göre, bu sayfaya `Catalog/Details/{id}` rotada erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="def88-225">Yolun `{id}` yer tutucusunun değeri bir tamsayı ile kısıtlanıyor.</span><span class="sxs-lookup"><span data-stu-id="def88-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="def88-226">[Yönlendirme](pages-routing-layouts.md) bölümünde açıklandığı gibi, Web Forms aksine bir Razor bileşeni, kendi yolunu ve dahil edilen tüm parametreleri açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="def88-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="def88-227">Birçok Web Forms denetimi ' de tam karşılıklarıyla eşleşmeyebilir Blazor .</span><span class="sxs-lookup"><span data-stu-id="def88-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="def88-228">Genellikle aynı amacı sunan eşdeğer bir HTML kod parçacığı vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="def88-229">Örneğin, `<asp:Label />` Denetim BIR HTML `<label>` öğesiyle değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="def88-230">İçindeki model doğrulaması Blazor</span><span class="sxs-lookup"><span data-stu-id="def88-230">Model validation in Blazor</span></span>

<span data-ttu-id="def88-231">Web Forms kodunuz doğrulamayı içeriyorsa, az sayıda değişiklik ile sahip olduğunuz kadarını aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def88-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="def88-232">İçinde çalıştırmanın bir avantajı, Blazor aynı doğrulama mantığının özel JavaScript gerekmeden çalıştırılmamasının bir avantajıdır.</span><span class="sxs-lookup"><span data-stu-id="def88-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="def88-233">Veri ek açıklamaları kolay model doğrulamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="def88-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="def88-234">Örneğin, *Create. aspx* sayfasında doğrulama içeren bir veri girişi formu vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="def88-235">Örnek parçacığı şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="def88-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="def88-236">Blazor' De, eşdeğer biçimlendirme bir *Create. Razor* dosyasında verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="def88-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="def88-237">`EditForm`Bağlam doğrulama desteğini içerir ve bir giriş etrafına sarılanabilir.</span><span class="sxs-lookup"><span data-stu-id="def88-237">The `EditForm` context includes validation support and can be wrapped around an input.</span></span> <span data-ttu-id="def88-238">Veri ek açıklamaları, doğrulama eklemenin yaygın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="def88-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="def88-239">Bu tür doğrulama desteği bileşen aracılığıyla eklenebilir `DataAnnotationsValidator` .</span><span class="sxs-lookup"><span data-stu-id="def88-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="def88-240">Bu mekanizma hakkında daha fazla bilgi için bkz. [ASP.NET Core Blazor Forms ve Validation](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="def88-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="def88-241">Yapılandırmayı geçir</span><span class="sxs-lookup"><span data-stu-id="def88-241">Migrate configuration</span></span>

<span data-ttu-id="def88-242">Web Forms projesinde, yapılandırma verileri genellikle *web.config* dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="def88-242">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="def88-243">Yapılandırma verilerine ile erişilir `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="def88-243">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="def88-244">Hizmetler genellikle nesneleri ayrıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="def88-244">Services were often required to parse objects.</span></span> <span data-ttu-id="def88-245">.NET Framework 4.7.2 ile, ile yapılandırmaya bir bileşim eklenmiştir `ConfigurationBuilders` .</span><span class="sxs-lookup"><span data-stu-id="def88-245">With .NET Framework 4.7.2, composability was added to the configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="def88-246">Bu oluşturucular, geliştiricilerin gerekli değerleri almak için çalışma zamanında oluşturulan yapılandırma için çeşitli kaynaklar eklemesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="def88-246">These builders allowed developers to add various sources for the configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="def88-247">ASP.NET Core, uygulamanız ve dağıtımınız tarafından kullanılan yapılandırma kaynağını veya kaynaklarını tanımlamanızı sağlayan esnek bir yapılandırma sistemi sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="def88-247">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="def88-248">`ConfigurationBuilder`Web Forms uygulamanızda kullandığınız altyapı, ASP.NET Core yapılandırma sisteminde kullanılan kavramlardan sonra modellenmiştir.</span><span class="sxs-lookup"><span data-stu-id="def88-248">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="def88-249">Aşağıdaki kod parçacığında Web Forms eShop projesinin yapılandırma değerlerini depolamak için *web.config* nasıl kullandığı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="def88-249">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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
</configuration>
```

<span data-ttu-id="def88-250">Veritabanı bağlantı dizeleri gibi, *web.config* içinde depolanacak gizli dizileri yaygındır. Gizli dizileri, kaynak denetimi gibi güvenli olmayan konumlarda kalıcı olarak kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="def88-250">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="def88-251">BlazorASP.NET Core ile, ÖNCEKI XML tabanlı yapılandırma AŞAĞıDAKI JSON ile değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="def88-251">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="def88-252">JSON varsayılan yapılandırma biçimidir; Ancak, ASP.NET Core XML gibi birçok diğer biçimi destekler.</span><span class="sxs-lookup"><span data-stu-id="def88-252">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="def88-253">Ayrıca, topluluk tarafından desteklenen birkaç biçim vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-253">There are also several community-supported formats.</span></span>

<span data-ttu-id="def88-254">Projenin sınıfındaki Oluşturucu, Blazor `Startup` `IConfiguration` Oluşturucu ekleme olarak bilinen bir dı tekniği aracılığıyla bir örneği kabul eder:</span><span class="sxs-lookup"><span data-stu-id="def88-254">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="def88-255">Varsayılan olarak, ortam değişkenleri, JSON dosyaları (*appsettings.js* ve *appSettings. { Environment}. JSON*) ve komut satırı seçenekleri yapılandırma nesnesinde geçerli yapılandırma kaynakları olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="def88-255">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="def88-256">Yapılandırma kaynaklarına aracılığıyla erişilebilir `Configuration[key]` .</span><span class="sxs-lookup"><span data-stu-id="def88-256">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="def88-257">Daha gelişmiş bir teknik, yapılandırma verilerini nesnelere bağlamak için seçenekler örüntüsünün kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="def88-257">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="def88-258">Yapılandırma ve seçenekler düzeniyle ilgili daha fazla bilgi için sırasıyla ASP.NET Core [ASP.NET Core](/aspnet/core/fundamentals/configuration/) ve [Seçenekler](/aspnet/core/fundamentals/configuration/options)düzeninde yapılandırma konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="def88-258">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="def88-259">Veri erişimini geçirme</span><span class="sxs-lookup"><span data-stu-id="def88-259">Migrate data access</span></span>

<span data-ttu-id="def88-260">Veri erişimi, tüm uygulamaların önemli bir yönüdür.</span><span class="sxs-lookup"><span data-stu-id="def88-260">Data access is an important aspect of any app.</span></span> <span data-ttu-id="def88-261">EShop projesi, katalog bilgilerini bir veritabanında depolar ve Entity Framework (EF) 6 ile verileri alır.</span><span class="sxs-lookup"><span data-stu-id="def88-261">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="def88-262">.NET 5,0 ' de EF 6 desteklendiğinden, proje onu kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-262">Since EF 6 is supported in .NET 5.0, the project can continue to use it.</span></span>

<span data-ttu-id="def88-263">Aşağıdaki EF ile ilgili değişiklikler eShop için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="def88-263">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="def88-264">.NET Framework, `DbContext` nesnesi *Name = ConnectionString* biçiminde bir dize kabul eder ve bağlantı dizesini `ConfigurationManager.AppSettings[ConnectionString]` bağlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="def88-264">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="def88-265">.NET Core 'da bu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="def88-265">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="def88-266">Bağlantı dizesinin sağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="def88-266">The connection string must be supplied.</span></span>
- <span data-ttu-id="def88-267">Veritabanına zaman uyumlu bir şekilde erişildi.</span><span class="sxs-lookup"><span data-stu-id="def88-267">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="def88-268">Bu işlem çalışsa da ölçeklenebilirlik düşebilir.</span><span class="sxs-lookup"><span data-stu-id="def88-268">Though this works, scalability may suffer.</span></span> <span data-ttu-id="def88-269">Bu mantık zaman uyumsuz bir modele taşınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="def88-269">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="def88-270">Veri kümesi bağlama için aynı yerel destek olmasa da, Blazor Razor sayfasında C# desteğiyle esneklik ve güç sağlar.</span><span class="sxs-lookup"><span data-stu-id="def88-270">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="def88-271">Örneğin, hesaplamalar yapabilir ve sonucu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def88-271">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="def88-272">İçindeki veri desenleri hakkında daha fazla bilgi için Blazor bkz. [veri erişimi](data.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="def88-272">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="def88-273">Mimari değişiklikler</span><span class="sxs-lookup"><span data-stu-id="def88-273">Architectural changes</span></span>

<span data-ttu-id="def88-274">Son olarak, ' a geçiş yaparken göz önünde bulundurmanız gereken bazı önemli mimari farklılıklar vardır Blazor .</span><span class="sxs-lookup"><span data-stu-id="def88-274">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="def88-275">Bu değişikliklerin çoğu, .NET Core veya ASP.NET Core temel alınarak herhangi bir şey için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="def88-275">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="def88-276">Blazor, .NET Core üzerine inşa edildiğinden, .NET Core üzerinde destek sağlamaya yönelik hususlar vardır.</span><span class="sxs-lookup"><span data-stu-id="def88-276">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="def88-277">Bazı önemli değişikliklerden bazıları aşağıdaki özelliklerin kaldırılmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="def88-277">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="def88-278">Birden çok AppDomain</span><span class="sxs-lookup"><span data-stu-id="def88-278">Multiple AppDomains</span></span>
- <span data-ttu-id="def88-279">Uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="def88-279">Remoting</span></span>
- <span data-ttu-id="def88-280">Kod Erişimi Güvenliği (CAS)</span><span class="sxs-lookup"><span data-stu-id="def88-280">Code Access Security (CAS)</span></span>
- <span data-ttu-id="def88-281">Güvenlik saydamlığı</span><span class="sxs-lookup"><span data-stu-id="def88-281">Security Transparency</span></span>

<span data-ttu-id="def88-282">.NET Core üzerinde çalışmayı desteklemek için gereken değişiklikleri belirlemek için teknikler hakkında daha fazla bilgi için bkz. [.NET Framework kodunuzun bağlantı noktası, .NET Core](../../core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="def88-282">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](../../core/porting/index.md).</span></span>

<span data-ttu-id="def88-283">ASP.NET Core, ASP.NET 'in yeniden oluşturulmuş bir sürümüdür ve başlangıçta belirgin bir şekilde görünmeyebilir bazı değişiklikler içerir.</span><span class="sxs-lookup"><span data-stu-id="def88-283">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="def88-284">Ana değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="def88-284">The main changes are:</span></span>

- <span data-ttu-id="def88-285">Hiçbir eşitleme bağlamı yoktur, bu, `HttpContext.Current` `Thread.CurrentPrincipal` veya diğer statik erişimciler anlamına gelir</span><span class="sxs-lookup"><span data-stu-id="def88-285">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="def88-286">Gölge kopyalama yok</span><span class="sxs-lookup"><span data-stu-id="def88-286">No shadow copying</span></span>
- <span data-ttu-id="def88-287">İstek kuyruğu yok</span><span class="sxs-lookup"><span data-stu-id="def88-287">No request queue</span></span>

<span data-ttu-id="def88-288">ASP.NET Core çok sayıda işlem zaman uyumsuzdur ve g/ç bağlantılı görevlerin daha kolay bir şekilde yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="def88-288">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="def88-289">`Task.Wait()` `Task.GetResult()` İş parçacığı havuzu kaynaklarını hızlıca tüketebilen veya kullanılarak hiçbir şekilde engellenmemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="def88-289">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="def88-290">Geçiş sonucu</span><span class="sxs-lookup"><span data-stu-id="def88-290">Migration conclusion</span></span>

<span data-ttu-id="def88-291">Bu noktada, bir Web Forms projesinin ne kadar sürdüğü hakkında birçok örnek gördünüz Blazor .</span><span class="sxs-lookup"><span data-stu-id="def88-291">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="def88-292">Tam bir örnek için bkz. [Eshopon Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor) projesi.</span><span class="sxs-lookup"><span data-stu-id="def88-292">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="def88-293">Önceki</span><span class="sxs-lookup"><span data-stu-id="def88-293">Previous</span></span>](security-authentication-authorization.md)
