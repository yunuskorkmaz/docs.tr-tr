---
title: ASP.NET Web Formlarından Blazor'a geçiş
description: Varolan bir ASP.NET web formlarını Blazor'a nasıl geçirterek nasıl yaklaşarak yaklaşacaklarınızı öğrenin.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134085"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="0efa7-103">ASP.NET Web Formlarından Blazor'a geçiş</span><span class="sxs-lookup"><span data-stu-id="0efa7-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0efa7-104">Bir kod tabanını ASP.NET Web Formlarından Blazor'a geçirmek, planlama gerektiren zaman alan bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="0efa7-105">Bu bölümde süreç özetlenir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-105">This chapter outlines the process.</span></span> <span data-ttu-id="0efa7-106">Geçişi kolaylaştırabilecek bir şey, uygulamanın N *katmanlı* bir mimariye uymasını sağlamaktır, bu durumda uygulama modeli (bu durumda Web Formları) iş mantığından ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="0efa7-107">Katmanların bu mantıksal ayrımı,.NET Core ve Blazor'a taşınması gerekenleri açıkça ortaya koyuyor.</span><span class="sxs-lookup"><span data-stu-id="0efa7-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="0efa7-108">Bu örnekte, [GitHub'da](https://github.com/dotnet-architecture/eShopOnBlazor) bulunan eShop uygulaması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="0efa7-109">eShop form girişi ve doğrulama yoluyla CRUD yetenekleri sağlayan bir katalog hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="0efa7-110">Çalışan bir uygulama neden Blazor'a geçirilmelidir?</span><span class="sxs-lookup"><span data-stu-id="0efa7-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="0efa7-111">Çoğu zaman, gerek yok.</span><span class="sxs-lookup"><span data-stu-id="0efa7-111">Many times, there's no need.</span></span> <span data-ttu-id="0efa7-112">ASP.NET Web Formları uzun yıllar desteklenmeye devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="0efa7-113">Ancak, Blazor'un sağladığı özelliklerin çoğu yalnızca geçirilen bir uygulamada desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="0efa7-114">Bu özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0efa7-114">Such features include:</span></span>

- <span data-ttu-id="0efa7-115">gibi çerçevede performans iyileştirmeleri`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="0efa7-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="0efa7-116">WebAssembly olarak çalışma becerisi</span><span class="sxs-lookup"><span data-stu-id="0efa7-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="0efa7-117">Linux ve macOS için çapraz platform desteği</span><span class="sxs-lookup"><span data-stu-id="0efa7-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="0efa7-118">Diğer uygulamaları etkilemeden uygulama yerel dağıtımı veya paylaşılan çerçeve dağıtımı</span><span class="sxs-lookup"><span data-stu-id="0efa7-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="0efa7-119">Bu veya diğer yeni özellikler yeterince ilgi çekiciyse, uygulamayı geçirmenin bir değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="0efa7-120">Geçiş farklı şekillerde alabilir; uygulamanın tamamı veya değişiklikleri gerektiren yalnızca belirli uç noktalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="0efa7-121">Geçiş kararı sonuçta geliştirici tarafından çözülecek iş sorunlarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="0efa7-122">Sunucu tarafı ve istemci tarafı barındırma</span><span class="sxs-lookup"><span data-stu-id="0efa7-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="0efa7-123">[Barındırma modelleri](hosting-models.md) bölümünde açıklandığı gibi, bir Blazor uygulaması iki farklı şekilde barındırılabilir: sunucu tarafı ve istemci tarafı.</span><span class="sxs-lookup"><span data-stu-id="0efa7-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="0efa7-124">Sunucu tarafındaki model, sunucuda herhangi bir gerçek kodu çalıştırırken DOM güncelleştirmelerini yönetmek için ASP.NET Core SignalR bağlantılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="0efa7-125">İstemci tarafı modeli tarayıcı içinde WebAssembly olarak çalışır ve sunucu bağlantısı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0efa7-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="0efa7-126">Belirli bir uygulama için en iyi etkiyi etkileyebilecek farklılıklar vardır:</span><span class="sxs-lookup"><span data-stu-id="0efa7-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="0efa7-127">WebAssembly olarak çalışan hala geliştirme aşamasındadır ve geçerli zamanda tüm özellikleri (iş parçacığı gibi) desteklemeyebilir</span><span class="sxs-lookup"><span data-stu-id="0efa7-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="0efa7-128">İstemci ve sunucu arasındaki geveze iletişim, sunucu tarafındaki modda gecikme sorunlarına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="0efa7-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="0efa7-129">Veritabanlarına ve dahili veya korumalı hizmetlere erişim, istemci tarafı barındırma ile ayrı bir hizmet gerektirir</span><span class="sxs-lookup"><span data-stu-id="0efa7-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="0efa7-130">Yazma sırasında, sunucu tarafındaki model Web Formlarına daha yakından benzer.</span><span class="sxs-lookup"><span data-stu-id="0efa7-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="0efa7-131">Bu bölümün çoğu, üretime hazır olduğu için sunucu tarafındaki barındırma modeline odaklanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="0efa7-132">Yeni bir proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="0efa7-132">Create a new project</span></span>

<span data-ttu-id="0efa7-133">Bu ilk geçiş adımı yeni bir proje oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="0efa7-134">Bu proje türü .NET Core'un SDK tarzı projelerini temel almaktadır ve önceki proje biçimlerinde kullanılan kazan plakasının çoğunu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="0efa7-135">Daha fazla ayrıntı için lütfen [Proje Yapısı](project-structure.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="0efa7-136">Proje oluşturulduktan sonra, önceki projede kullanılan kitaplıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0efa7-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="0efa7-137">Eski Web Formları projelerinde, gerekli NuGet paketlerini listelemek için *packages.config* dosyasını kullanmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="0efa7-138">Yeni SDK tarzı projede, *packages.config* proje `<PackageReference>` dosyasındaki öğelerle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="0efa7-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="0efa7-139">Bu yaklaşımın bir yararı, tüm bağımlılıkların geçişli olarak yüklenmesidir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="0efa7-140">Yalnızca önemsediğiniz üst düzey bağımlılıkları listelersiniz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="0efa7-141">Kullanmakta olduğunuz bağımlılıkların çoğu Entity Framework 6 ve log4net dahil olmak üzere .NET Core için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="0efa7-142">.NET Core veya .NET Standard sürümü yoksa, .NET Framework sürümü genellikle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="0efa7-143">Kilometreniz değişebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-143">Your mileage may vary.</span></span> <span data-ttu-id="0efa7-144">.NET Core'da bulunmayan herhangi bir API çalışma zamanı hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0efa7-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="0efa7-145">Visual Studio bu tür paketleri size ileter.</span><span class="sxs-lookup"><span data-stu-id="0efa7-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="0efa7-146">**Çözüm**Gezgini'nde projenin **Başvuru düğümünde** sarı bir simge görünür.</span><span class="sxs-lookup"><span data-stu-id="0efa7-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="0efa7-147">Blazor tabanlı eShop projesinde, yüklenen paketleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="0efa7-148">Daha *önce, packages.config* dosyası projede kullanılan her paketi listeleyerek neredeyse 50 satır uzunluğunda bir dosyayla sonuçlanıyor.</span><span class="sxs-lookup"><span data-stu-id="0efa7-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="0efa7-149">*Paketler.config* bir snippet olduğunu:</span><span class="sxs-lookup"><span data-stu-id="0efa7-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="0efa7-150">Öğe `<packages>` gerekli tüm bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="0efa7-151">Bu paketlerden hangisinin dahil olduğunu belirlemek zordur, çünkü bunlara gereksinim duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="0efa7-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="0efa7-152">Bazı `<package>` öğeler yalnızca gereksinim duyduğunuz bağımlılıkların gereksinimlerini karşılamak için listelenir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="0efa7-153">Blazor projesi, proje dosyasındaki bir `<ItemGroup>` öğe içinde gereksinim duyduğunuz bağımlılıkları listeler:</span><span class="sxs-lookup"><span data-stu-id="0efa7-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="0efa7-154">Web Formları geliştiricilerin ömrünü kolaylaştıran bir NuGet paketi [Windows Uyumluluk Paketidir.](../../core/porting/windows-compat-pack.md)</span><span class="sxs-lookup"><span data-stu-id="0efa7-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="0efa7-155">.NET Core çapraz platform olmasına rağmen, bazı özellikler yalnızca Windows'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="0efa7-156">Uyumluluk paketini yükleyerek Windows'a özgü özellikler kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="0efa7-157">Bu tür özelliklere örnek olarak Kayıt Defteri, WMI ve Dizin Hizmetleri verilebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="0efa7-158">Paket yaklaşık 20.000 API ekler ve zaten tanıdık olabileceğiniz birçok hizmeti etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="0efa7-159">eShop projesi uyumluluk paketi gerektirmez; ancak projeleriniz Windows'a özgü özellikler kullanıyorsa, paket geçiş çabalarını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="0efa7-160">Başlatma işlemini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0efa7-160">Enable startup process</span></span>

<span data-ttu-id="0efa7-161">Blazor için başlangıç işlemi Web Formlar'dan değiştirildi ve diğer ASP.NET Core hizmetleri için benzer bir kurulum izler.</span><span class="sxs-lookup"><span data-stu-id="0efa7-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="0efa7-162">Sunucu tarafından barındırıldığında, Blazor bileşenleri normal bir ASP.NET Core uygulamasının bir parçası olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="0efa7-163">WebAssembly ile tarayıcıda barındırıldığında, Blazor bileşenleri benzer bir barındırma modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="0efa7-164">Fark bileşenleri arka uç işlemlerinin herhangi birinden ayrı bir hizmet olarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="0efa7-165">Her iki şekilde de, başlangıç benzer.</span><span class="sxs-lookup"><span data-stu-id="0efa7-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="0efa7-166">*Global.asax.cs* dosyası, Web Formları projeleri için varsayılan başlangıç sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="0efa7-167">eShop projesinde, bu dosya Denetimin Ters Çevrilmesi (IoC) kapsayıcısını yapılandırır ve uygulamanın veya isteğin çeşitli yaşam döngüsü olaylarını işler.</span><span class="sxs-lookup"><span data-stu-id="0efa7-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="0efa7-168">Bu olaylardan bazıları ara yazılımla `Application_BeginRequest`işlenir (örneğin).</span><span class="sxs-lookup"><span data-stu-id="0efa7-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="0efa7-169">Diğer olaylar bağımlılık enjeksiyonu (DI) yoluyla belirli hizmetlerin geçersiz kılınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="0efa7-170">Örnek olarak, eShop için *Global.asax.cs* dosyası, aşağıdaki kodu içerir:</span><span class="sxs-lookup"><span data-stu-id="0efa7-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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

<span data-ttu-id="0efa7-171">Önceki dosya sunucu `Startup` tarafı Blazor sınıf olur:</span><span class="sxs-lookup"><span data-stu-id="0efa7-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="0efa7-172">Web Formlar'dan fark edebilirsiniz önemli bir değişiklik DI önem olduğunu.</span><span class="sxs-lookup"><span data-stu-id="0efa7-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="0efa7-173">DI ASP.NET Core tasarımında yol gösterici bir ilke olmuştur.</span><span class="sxs-lookup"><span data-stu-id="0efa7-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="0efa7-174">ASP.NET Core çerçevesinin hemen hemen tüm yönlerinin özelleştirilmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="0efa7-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="0efa7-175">Hatta birçok senaryo için kullanılabilecek yerleşik bir hizmet sağlayıcısı vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="0efa7-176">Daha fazla özelleştirme gerekiyorsa, birçok topluluk projesi tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="0efa7-177">Örneğin, üçüncü taraf DI kitaplığı yatırımınızı ileriye taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="0efa7-178">Orijinal eShop uygulamasında, oturum yönetimi için bazı yapılandırmalar vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="0efa7-179">Sunucu tarafı Blazor iletişim için ASP.NET Core SignalR kullandığından, bağlantılar bir HTTP bağlamından bağımsız olarak oluşabileceğinden oturum durumu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0efa7-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="0efa7-180">Oturum durumunu kullanan bir uygulama, Blazor uygulaması olarak çalıştırmadan önce yeniden yeniden tasarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="0efa7-181">Uygulama başlatma hakkında daha fazla bilgi için [Uygulama başlangıç](app-startup.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="0efa7-182">HTTP modüllerini ve işleyicilerini ara yazılıma geçirin</span><span class="sxs-lookup"><span data-stu-id="0efa7-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="0efa7-183">HTTP modülleri ve işleyicileri, HTTP istek ardışık düzenini denetlemek için Web Formları'nda yaygın desenlerdir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="0efa7-184">Gelen istekleri `IHttpModule` `IHttpHandler` uygulayan veya kaydedilebilen sınıflar.</span><span class="sxs-lookup"><span data-stu-id="0efa7-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="0efa7-185">Web *Forms, web.config* dosyasındaki modülleri ve işleyicileri yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="0efa7-186">Web Formları da ağır uygulama yaşam döngüsü olay işleme dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="0efa7-187">ASP.NET Core bunun yerine ara yazılım kullanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="0efa7-188">Middleware sınıfın yönteminde `Configure` `Startup` kayıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="0efa7-189">Middleware yürütme emri kayıt emri ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="0efa7-190">Başlatma [işlemini etkinleştir](#enable-startup-process) bölümünde, `Application_BeginRequest` yöntem olarak Web Forms tarafından bir yaşam döngüsü olayı yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="0efa7-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="0efa7-191">Bu etkinlik ASP.NET Core'da kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="0efa7-192">Bu davranışı elde etmenin bir yolu, *Startup.cs* dosyası örneğinde görüldüğü gibi ara yazılım uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="0efa7-193">Bu ara yazılım aynı mantığı yapar ve sonra denetimi ara yazılım ardışık ardışık ardışık ardışık bir sonraki işleyiciye aktarır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="0efa7-194">Geçiş modülleri ve işleyicileri hakkında daha fazla bilgi için, [Core ara yazılımASP.NET için http işleyicileri ve modülleri geçirin](/aspnet/core/migration/http-modules)bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="0efa7-195">Statik dosyaları geçir</span><span class="sxs-lookup"><span data-stu-id="0efa7-195">Migrate static files</span></span>

<span data-ttu-id="0efa7-196">Statik dosyalara (örneğin, HTML, CSS, resimler ve JavaScript) hizmet vermek için, dosyaların ara yazılımtarafından açıkta kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="0efa7-197">`UseStaticFiles` Yöntemi çağırmak, statik dosyaların web kök yolundan sunulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0efa7-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="0efa7-198">Varsayılan web kök dizini *wwwroot,* ancak özelleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="0efa7-199">eShop'un `Startup` `Configure` sınıfının yöntemine dahil edildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="0efa7-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="0efa7-200">eShop projesi temel statik dosya erişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0efa7-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="0efa7-201">Statik dosya erişimi için birçok özelleştirme vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="0efa7-202">Varsayılan dosyaları veya dosya tarayıcısını etkinleştirme hakkında bilgi için [ASP.NET Core'daki Statik dosyalara](/aspnet/core/fundamentals/static-files)bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="0efa7-203">Çalışma zamanı birleştirme ve minification kurulum geçiş</span><span class="sxs-lookup"><span data-stu-id="0efa7-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="0efa7-204">Birleştirme ve azaltma, belirli dosya türlerini almak için sunucu isteklerinin sayısını ve boyutunu azaltmak için performans optimizasyonu teknikleridir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="0efa7-205">JavaScript ve CSS genellikle istemciye gönderilmeden önce birleştirme veya minification çeşit tabi.</span><span class="sxs-lookup"><span data-stu-id="0efa7-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="0efa7-206">Web Formlar ASP.NET bu optimizasyonlar çalışma zamanında işlenir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="0efa7-207">Optimizasyon kuralları bir *App_Start/BundleConfig.cs* dosyası olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="0efa7-208">ASP.NET Core'da daha açıklayıcı bir yaklaşım benimsenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="0efa7-209">Bir dosya, belirli minification ayarları ile birlikte minified edilecek dosyaları listeler.</span><span class="sxs-lookup"><span data-stu-id="0efa7-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="0efa7-210">Donma ve kıyma hakkında daha fazla bilgi için, [ASP.NET Core'daki Bundle ve minify statik varlıkları](/aspnet/core/client-side/bundling-and-minification)görün.</span><span class="sxs-lookup"><span data-stu-id="0efa7-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="0efa7-211">ASPX sayfalarını geçir</span><span class="sxs-lookup"><span data-stu-id="0efa7-211">Migrate ASPX pages</span></span>

<span data-ttu-id="0efa7-212">Web Forms uygulamasındaki bir sayfa *.aspx* uzantılı bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="0efa7-213">Web Formları sayfası genellikle Blazor'daki bir bileşenle eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="0efa7-214">Blazor bileşeni *.razor* uzantılı bir dosyada yazılır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="0efa7-215">eShop projesi için beş sayfa Jilet sayfasına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="0efa7-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="0efa7-216">Örneğin, ayrıntı görünümü Web Formları projesinde üç dosyadan oluşur: *Details.aspx*, *Details.aspx.cs*ve *Details.aspx.designer.cs.*</span><span class="sxs-lookup"><span data-stu-id="0efa7-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="0efa7-217">Blazor'a dönüştürürken, kod arkası ve biçimlendirme *Details.razor*olarak birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="0efa7-218">Jilet derlemesi *(.designer.cs* dosyalarındakine eşdeğer) *obj* dizininde depolanır ve varsayılan olarak **Solution Explorer'da**görüntülenebilir değildir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="0efa7-219">Web Formları sayfası aşağıdaki biçimlendirmeden oluşur:</span><span class="sxs-lookup"><span data-stu-id="0efa7-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="0efa7-220">Önceki biçimlendirmenin kod arkası aşağıdaki kodu içerir:</span><span class="sxs-lookup"><span data-stu-id="0efa7-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="0efa7-221">Blazor'a dönüştürüldüğünde, Web Formları sayfası aşağıdaki koda çevirir:</span><span class="sxs-lookup"><span data-stu-id="0efa7-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="0efa7-222">Kod ve biçimlendirmenin aynı dosyada olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0efa7-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="0efa7-223">Gerekli tüm hizmetler öznitelik `@inject` ile erişilebilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="0efa7-224">Yönerge `@page` ye göre, bu sayfaya `Catalog/Details/{id}` rotadan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="0efa7-225">Rotanın `{id}` yer tutucunun değeri bir sonal ile sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="0efa7-226">[Yönlendirme](pages-routing-layouts.md) bölümünde açıklandığı gibi, Web Formlarından farklı olarak, bir Razor bileşeni rotasını ve dahil olan parametreleri açıkça belirtir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="0efa7-227">Birçok Web Forms denetimiblazor tam muadilleri olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="0efa7-228">Genellikle aynı amaca hizmet edecek eşdeğer bir HTML snippet var.</span><span class="sxs-lookup"><span data-stu-id="0efa7-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="0efa7-229">Örneğin, `<asp:Label />` denetim bir HTML `<label>` öğesi ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="0efa7-230">Blazor'da model doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0efa7-230">Model validation in Blazor</span></span>

<span data-ttu-id="0efa7-231">Web Formları kodunuz doğrulama içeriyorsa, sahip olduğunuz değişikliklerin çoğunu az-hiç değişiklikle aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="0efa7-232">Blazor çalışan bir yararı, aynı doğrulama mantığı özel JavaScript gerek kalmadan çalıştırılabilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="0efa7-233">Veri ek açıklamaları kolay model doğrulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="0efa7-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="0efa7-234">Örneğin, *Create.aspx* sayfasında doğrulama içeren bir veri giriş formu vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="0efa7-235">Örnek bir snippet şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="0efa7-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="0efa7-236">Blazor'da eşdeğer biçimlendirme *Create.razor* dosyasında sağlanır:</span><span class="sxs-lookup"><span data-stu-id="0efa7-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="0efa7-237">Bağlam `EditForm` doğrulama desteği içerir ve giriş etrafında sarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="0efa7-238">Veri ek açıklamaları doğrulama eklemek için yaygın bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="0efa7-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="0efa7-239">Bu tür doğrulama desteği `DataAnnotationsValidator` bileşen üzerinden eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="0efa7-240">Bu mekanizma hakkında daha fazla bilgi [için, ASP.NET Core Blazor formları ve doğrulama](/aspnet/core/blazor/forms-validation)bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="0efa7-241">Yerleşik Web Formları denetimlerini geçirin</span><span class="sxs-lookup"><span data-stu-id="0efa7-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="0efa7-242">*Bu içerik yakında geliyor.*</span><span class="sxs-lookup"><span data-stu-id="0efa7-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="0efa7-243">Yapılandırmayı geçir</span><span class="sxs-lookup"><span data-stu-id="0efa7-243">Migrate configuration</span></span>

<span data-ttu-id="0efa7-244">Bir Web Forms projesinde, yapılandırma verileri en sık *web.config* dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="0efa7-245">Yapılandırma verilerine . `ConfigurationManager`</span><span class="sxs-lookup"><span data-stu-id="0efa7-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="0efa7-246">Nesneleri ayrıştırmak için genellikle hizmetler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-246">Services were often required to parse objects.</span></span> <span data-ttu-id="0efa7-247">.NET Framework 4.7.2 ile yapılandırmaya .composability ile `ConfigurationBuilders`eklendi.</span><span class="sxs-lookup"><span data-stu-id="0efa7-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="0efa7-248">Bu oluşturucular, geliştiricilerin gerekli değerleri almak için çalışma zamanında oluşturulan yapılandırma için çeşitli kaynaklar eklemelerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="0efa7-249">ASP.NET Core, uygulamanız ve dağıtımınız tarafından kullanılan yapılandırma kaynağını veya kaynakları tanımlamanızı sağlayan esnek bir yapılandırma sistemi tanıttı.</span><span class="sxs-lookup"><span data-stu-id="0efa7-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="0efa7-250">Web `ConfigurationBuilder` Formları uygulamanızda kullanıyor olabileceğiniz altyapı, ASP.NET Core yapılandırma sisteminde kullanılan kavramlardan sonra modellenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="0efa7-251">Aşağıdaki parçacık, Web Forms eShop projesinin yapılandırma değerlerini depolamak için *web.config'i* nasıl kullandığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="0efa7-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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

<span data-ttu-id="0efa7-252">Veritabanı bağlantı dizeleri gibi sırların *web.config*içinde depolanması yaygındır. Sırlar kaçınılmaz olarak kaynak denetimi gibi güvenli olmayan konumlarda devam edilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="0efa7-253">Blazor ASP.NET Core ile, önceki XML tabanlı yapılandırma aşağıdaki JSON ile değiştirilir:</span><span class="sxs-lookup"><span data-stu-id="0efa7-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="0efa7-254">JSON varsayılan yapılandırma biçimidir; ancak, ASP.NET Core XML de dahil olmak üzere birçok diğer biçimleri destekler.</span><span class="sxs-lookup"><span data-stu-id="0efa7-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="0efa7-255">Topluluk destekli çeşitli biçimler de vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="0efa7-256">Blazor projesinin `Startup` sınıfındaki oluşturucu, yapıcı `IConfiguration` enjeksiyon olarak bilinen bir DI tekniği ile bir örneği kabul eder:</span><span class="sxs-lookup"><span data-stu-id="0efa7-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="0efa7-257">Varsayılan olarak, ortam değişkenleri, JSON dosyaları *(appsettings.json* ve *appsettings.{ Environment}.json*), ve komut satırı seçenekleri yapılandırma nesnesinde geçerli yapılandırma kaynakları olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="0efa7-258">Yapılandırma kaynaklarına `Configuration[key]`.</span><span class="sxs-lookup"><span data-stu-id="0efa7-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="0efa7-259">Daha gelişmiş bir teknik, seçenekler deseni kullanarak yapılandırma verilerini nesnelere bağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="0efa7-260">Yapılandırma ve seçenekler deseni hakkında daha fazla bilgi için sırasıyla ASP.NET [Core'daki ASP.NET Çekirdek](/aspnet/core/fundamentals/configuration/) ve [Seçenekler desenindeki Yapılandırma'ya](/aspnet/core/fundamentals/configuration/options)bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="0efa7-261">Veri erişimini geçirin</span><span class="sxs-lookup"><span data-stu-id="0efa7-261">Migrate data access</span></span>

<span data-ttu-id="0efa7-262">Veri erişimi herhangi bir uygulamanın önemli bir yönüdür.</span><span class="sxs-lookup"><span data-stu-id="0efa7-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="0efa7-263">eShop projesi katalog bilgilerini bir veritabanında saklar ve verileri Entity Framework (EF) 6 ile alır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="0efa7-264">EF 6 .NET Core 3.0'da desteklendirilebildiği için proje kullanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="0efa7-265">EShop için ef ile ilgili aşağıdaki değişiklikler gerekliydi:</span><span class="sxs-lookup"><span data-stu-id="0efa7-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="0efa7-266">.NET Framework'de `DbContext` nesne form *adı=ConnectionString* dizesini kabul eder `ConfigurationManager.AppSettings[ConnectionString]` ve bağlanmak için bağlantı dizesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="0efa7-267">.NET Core'da bu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0efa7-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="0efa7-268">Bağlantı dizesi sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="0efa7-269">Veritabanına eşzamanlı bir şekilde erişildi.</span><span class="sxs-lookup"><span data-stu-id="0efa7-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="0efa7-270">Bu işe yarasa da, ölçeklenebilirlik zarar görebilir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="0efa7-271">Bu mantık bir eşzamanlı desen taşınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="0efa7-272">Veri kümesi bağlama için aynı yerel destek olmamasına rağmen, Blazor bir Razor sayfasında C# desteği ile esneklik ve güç sağlar.</span><span class="sxs-lookup"><span data-stu-id="0efa7-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="0efa7-273">Örneğin, hesaplamalar yapabilir ve sonucu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="0efa7-274">Blazor'daki veri desenleri hakkında daha fazla bilgi için [Veri erişim](data.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="0efa7-275">Mimari değişiklikler</span><span class="sxs-lookup"><span data-stu-id="0efa7-275">Architectural changes</span></span>

<span data-ttu-id="0efa7-276">Son olarak, Blazor'a göç ederken göz önünde bulundurulması gereken bazı önemli mimari farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="0efa7-277">Bu değişikliklerin çoğu .NET Core veya ASP.NET Core tabanlı her şey için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="0efa7-278">Blazor .NET Core üzerine kurulduğundan, .NET Core'da destek sağlamada dikkat edilmesi gereken hususlar vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="0efa7-279">Önemli değişikliklerden bazıları aşağıdaki özelliklerin kaldırılmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="0efa7-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="0efa7-280">Birden Fazla AppDomains</span><span class="sxs-lookup"><span data-stu-id="0efa7-280">Multiple AppDomains</span></span>
- <span data-ttu-id="0efa7-281">Remoting</span><span class="sxs-lookup"><span data-stu-id="0efa7-281">Remoting</span></span>
- <span data-ttu-id="0efa7-282">Kod Erişimi Güvenliği (CAS)</span><span class="sxs-lookup"><span data-stu-id="0efa7-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="0efa7-283">Güvenlik Şeffaflığı</span><span class="sxs-lookup"><span data-stu-id="0efa7-283">Security Transparency</span></span>

<span data-ttu-id="0efa7-284">.NET Core'da çalıştırmayı desteklemek için gerekli değişiklikleri belirlemek için teknikler hakkında daha fazla bilgi için [kodunuzu .NET Framework'den .NET Core'a](/dotnet/core/porting)kadar port'a bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="0efa7-285">ASP.NET Core ASP.NET yeniden tasarlanmış bir sürümüdür ve başlangıçta açık görünmeyebilir bazı değişiklikler vardır.</span><span class="sxs-lookup"><span data-stu-id="0efa7-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="0efa7-286">Ana değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0efa7-286">The main changes are:</span></span>

- <span data-ttu-id="0efa7-287">Senkronizasyon bağlamı yok, bu da `HttpContext.Current` `Thread.CurrentPrincipal`başka statik erişimci olmadığı anlamına gelir</span><span class="sxs-lookup"><span data-stu-id="0efa7-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="0efa7-288">Gölge kopyalama yok</span><span class="sxs-lookup"><span data-stu-id="0efa7-288">No shadow copying</span></span>
- <span data-ttu-id="0efa7-289">İstek sırası yok</span><span class="sxs-lookup"><span data-stu-id="0efa7-289">No request queue</span></span>

<span data-ttu-id="0efa7-290">ASP.NET Core'daki birçok işlem, G/Ç'ye bağlı görevlerin daha kolay yüklenmesine olanak tanıyan eşzamanlı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="0efa7-291">İş parçacığı havuzu kaynaklarını hızlı `Task.Wait()` `Task.GetResult()`bir şekilde tüketebilen kullanarak veya engelleyerek asla engellememek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0efa7-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="0efa7-292">Göç sonucu</span><span class="sxs-lookup"><span data-stu-id="0efa7-292">Migration conclusion</span></span>

<span data-ttu-id="0efa7-293">Bu noktada, bir Web Forms projesini Blazor'a taşımak için gerekenlere pek çok örnek gördünüz.</span><span class="sxs-lookup"><span data-stu-id="0efa7-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="0efa7-294">Tam bir örnek için, [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) projesine bakın.</span><span class="sxs-lookup"><span data-stu-id="0efa7-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="0efa7-295">Önceki</span><span class="sxs-lookup"><span data-stu-id="0efa7-295">Previous</span></span>](security-authentication-authorization.md)
