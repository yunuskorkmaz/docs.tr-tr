---
title: Uygulama başlatma
description: Uygulamanız için başlangıç mantığını tanımlama hakkında bilgi edinin.
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: ea2ea458011d8351a834aa12db02e5d2bac2dc65
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267704"
---
# <a name="app-startup"></a><span data-ttu-id="c6c0a-103">Uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="c6c0a-103">App startup</span></span>

<span data-ttu-id="c6c0a-104">ASP.NET için yazılan uygulamalar genellikle, `global.asax.cs` `Application_Start` hangi hizmetlerin yapılandırıldığını ve hem HTML işleme hem de .net işlemesi için kullanılabilir hale getirildiğini denetleyen olayı tanımlayan bir dosya olur.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="c6c0a-105">Bu bölümde, ASP.NET Core ve Blazor Server ile ilgili işlerin nasıl biraz farklı olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="c6c0a-106">Application_Start ve Web Forms</span><span class="sxs-lookup"><span data-stu-id="c6c0a-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="c6c0a-107">Varsayılan Web formları `Application_Start` yöntemi, birçok yapılandırma görevini işlemek için yıllarca bir amaç artmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="c6c0a-108">Visual Studio 2019 ' de varsayılan şablona sahip yeni bir Web Forms projesi artık aşağıdaki yapılandırma mantığını içerir:</span><span class="sxs-lookup"><span data-stu-id="c6c0a-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="c6c0a-109">`RouteConfig` -Uygulama URL 'SI yönlendirme</span><span class="sxs-lookup"><span data-stu-id="c6c0a-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="c6c0a-110">`BundleConfig` -CSS ve JavaScript paketleme ve küçültmeye yönelik</span><span class="sxs-lookup"><span data-stu-id="c6c0a-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="c6c0a-111">Bu dosyaların her biri `App_Start` klasöründe bulunur ve uygulamamız başlangıcında yalnızca bir kez çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-111">Each of these individual files reside in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="c6c0a-112">`RouteConfig` Varsayılan proje şablonunda, `FriendlyUrlSettings` Uygulama URL 'lerinin dosya uzantısını yok saymasını sağlamak için Web formları için ' i ekler `.ASPX` .</span><span class="sxs-lookup"><span data-stu-id="c6c0a-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="c6c0a-113">Varsayılan şablon Ayrıca, `.ASPX` uzantıları açan dosya adı ile kolay URL 'ye sayfalar için kalıcı http yeniden yönlendirme durum kodları (HTTP 301) sağlayan bir yönerge içerir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="c6c0a-114">ASP.NET Core ve Blazor ile bu yöntemler `Startup` basitleşilir ve sınıfla birleştirilir ya da ortak web teknolojilerinin yararına ortadan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="c6c0a-115">Blazor sunucusu başlangıç yapısı</span><span class="sxs-lookup"><span data-stu-id="c6c0a-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="c6c0a-116">Blazor Server uygulamaları ASP.NET Core 3,0 veya üzeri bir uygulamanın üstünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later application.</span></span>  <span data-ttu-id="c6c0a-117">ASP.NET Core Web uygulamaları, `Startup.cs` uygulamanın kök klasöründeki sınıfında bir çift yöntem aracılığıyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="c6c0a-118">Başlangıç sınıfının varsayılan içeriği aşağıda listelenmiştir</span><span class="sxs-lookup"><span data-stu-id="c6c0a-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="c6c0a-119">ASP.NET Core geri kalanı gibi, başlangıç sınıfı bağımlılık ekleme ilkeleri ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="c6c0a-120">, `IConfiguration` Oluşturucuya sağlanır ve yapılandırma sırasında daha sonra erişmek üzere ortak bir özellikte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="c6c0a-121">`ConfigureServices`ASP.NET Core tanıtılan Yöntem, Framework 'ün yerleşik bağımlılık ekleme kapsayıcısı için çeşitli ASP.NET Core Framework hizmetlerinin yapılandırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="c6c0a-122">Çeşitli `services.Add*` Yöntemler, kimlik doğrulaması, Razor sayfaları, MVC denetleyici yönlendirmesi, SignalR ve Blazor Server etkileşimleri gibi özellikleri çok sayıda diğerleri arasında etkinleştiren hizmetler ekler.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="c6c0a-123">Bu yöntem, Web formlarında gerekli değildir, çünkü ASPX, ASCX, ASHX ve ASMX dosyalarını ayrıştırma ve işleme, web.config yapılandırma dosyasında ASP.NET başvuruda bulunarak tanımlanmıştı.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files was defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="c6c0a-124">ASP.NET Core bağımlılık ekleme hakkında daha fazla bilgi [Çevrimiçi belgelerde](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="c6c0a-125">`Configure`Yöntemi, ASP.NET Core IÇIN http işlem hattı kavramını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="c6c0a-126">Bu yöntemde, uygulamamıza gönderilen her isteği işleyecek olan [ara yazılımı](middleware.md) yukarıdan aşağıya doğru bildiririz.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="c6c0a-127">Varsayılan yapılandırmada bu özelliklerin çoğu, Web Forms yapılandırma dosyaları genelinde dağınık ve artık başvuru kolaylığı için tek bir yerde.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="c6c0a-128">Artık bir dosyaya yerleştirilen özel hata sayfasının yapılandırması değildir `web.config` , ancak artık uygulama ortamı etiketlenmezse her zaman gösterilecek şekilde yapılandırılmıştır `Development` .</span><span class="sxs-lookup"><span data-stu-id="c6c0a-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="c6c0a-129">Ayrıca, ASP.NET Core uygulamalar artık varsayılan olarak, yöntem çağrısıyla TLS ile güvenli sayfalar sunacak şekilde yapılandırılmıştır `UseHttpsRedirection` .</span><span class="sxs-lookup"><span data-stu-id="c6c0a-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="c6c0a-130">Ardından, beklenmeyen bir yapılandırma yöntemi olarak listelenir `UseStaticFiles` .</span><span class="sxs-lookup"><span data-stu-id="c6c0a-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="c6c0a-131">ASP.NET Core, statik dosyalar için (JavaScript, CSS ve resim dosyaları gibi) isteklerin desteğinin açıkça etkinleştirilmesi ve yalnızca uygulamanın *Wwwroot* klasöründeki dosyaların varsayılan olarak genel olarak adreslenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="c6c0a-132">Sonraki satır, web formlarından yapılandırma seçeneklerinden birini çoğaltan birincsahiptir: `UseRouting` .</span><span class="sxs-lookup"><span data-stu-id="c6c0a-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="c6c0a-133">Bu yöntem ASP.NET Core yönlendiricisini işlem hattına ekler ve burada ya da yönlendirmeyi düşünebileceğiniz tek dosyalarda yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="c6c0a-134">Yönlendirme yapılandırması hakkında daha fazla bilgi [Yönlendirme bölümünde](pages-routing-layouts.md)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="c6c0a-135">Bu yöntemdeki final ifadesinde ASP.NET Core dinlediği uç noktalar tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="c6c0a-136">Bunlar, Web sunucusuna erişebileceğiniz ve .NET tarafından işlenmiş ve size döndürülen Web 'de erişilebilir konumlardır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-136">These are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="c6c0a-137">İlk giriş, `MapBlazorHub` Blazor bileşenlerinin durumunun ve işlemenin işlendiği sunucuya gerçek zamanlı ve kalıcı bağlantı sağlamak için bir SignalR hub 'ı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="c6c0a-138">`MapFallbackToPage`Yöntem çağrısı, Blazor uygulamasını Başlatan sayfanın Web tarafından erişilebilen konumunu gösterir ve ayrıca uygulamayı istemci tarafı derin bağlama isteklerini işleyecek şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="c6c0a-139">Bir tarayıcı açarsanız ve varsayılan proje şablonunda olduğu gibi, uygulamanızda doğrudan Blazor işlenmiş yola gittiğinizde bu özelliği çalışır durumda görürsünüz `/counter` .</span><span class="sxs-lookup"><span data-stu-id="c6c0a-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="c6c0a-140">İstek, daha sonra Blazor yönlendiricisini çalıştıran ve sayaç sayfasını işleyen *_Host. cshtml* geri dönüş sayfası tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="c6c0a-141">Paketleme Liconfig Işlemini yükseltme</span><span class="sxs-lookup"><span data-stu-id="c6c0a-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="c6c0a-142">CSS stil sayfaları ve JavaScript dosyaları gibi varlıkları Paketleme Teknolojileri, bu kaynakları yönetmeye yönelik hızlı bir şekilde gelişen araçlar ve teknikler sağlayan diğer teknolojilerle önemli ölçüde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="c6c0a-143">Bu uçta, statik varlıklarınızı paketlemek için Gryeniden oluşturma/Gulp/WebPack gibi bir düğüm komut satırı aracı kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="c6c0a-144">Gryeniden bağlama, Gulp ve WebPack komut satırı araçları ve bunlarla ilişkili yapılandırma işlemleri uygulamanıza eklenebilir ve ASP.NET Core uygulama oluşturma işlemi sırasında bu dosyaları sessizce yoksayar.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="c6c0a-145">`Target`Bir Gulp betiğini ve `min` Bu betiğin içindeki hedefi tetikleyecek aşağıdakine benzer bir sözdizimi ile proje dosyanızın içine bir ekleyerek, görevlerini çalıştırmak için bir çağrı ekleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="c6c0a-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="c6c0a-146">CSS ve JavaScript dosyalarınızı yönetmek için her iki strateji hakkında daha fazla ayrıntı için, [ASP.NET Core belgelerinde bulunan statik varlıkları paket halinde ve daha az](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) bir şekilde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6c0a-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c6c0a-147">[Önceki](project-structure.md) 
> [Sonraki](components.md)</span><span class="sxs-lookup"><span data-stu-id="c6c0a-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
