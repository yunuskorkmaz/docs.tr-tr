---
title: ASP.NET Web Forms 'den geçiş Blazor
description: Var olan bir ASP.NET Web Forms uygulamasını ' ye geçirmeye nasıl yaklaşımınızı öğrenin Blazor .
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: 853358fbf534ee7501412259c61efe054b4757a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161210"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a>ASP.NET Web Forms 'den geçiş Blazor

Bir kod tabanının ASP.NET Web Forms ' den geçirilmesi Blazor , planlama gerektiren zaman alan bir görevdir. Bu bölümde işlem özetlenmektedir. Geçişi kolaylaştırmaya yönelik bir şey, uygulamanın, uygulama modelinde (Bu durumda Web Forms) iş mantığındaki bir *N katmanlı* mimariye uyduğundan emin olunması olabilir. Katmanlara yönelik bu mantıksal ayrım, .NET Core 'a ve ne kadar taşınabilmesini temizler Blazor .

Bu örnekte, [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) 'Da bulunan eShop uygulaması kullanılır. eShop, form girişi ve doğrulaması aracılığıyla CRUD özellikleri sağlayan bir katalog hizmetidir.

Çalışma uygulaması neden geçirilecek Blazor ? Birçok kez ihtiyacınız yoktur. ASP.NET Web Forms, birçok yıl boyunca desteklenmeye devam edecektir. Ancak, tarafından sağlanan özelliklerin birçoğu Blazor yalnızca geçirilmiş bir uygulamada desteklenir. Bu tür özellikler şunlardır:

- Çerçevede performans iyileştirmeleri `Span<T>`
- Farklı Çalıştır WebAssembly
- Linux ve macOS için platformlar arası destek
- Diğer uygulamaları etkilemeden uygulama yerel dağıtımı veya paylaşılan çerçeve dağıtımı

Bu veya diğer yeni özellikler yeterince etkileyici ise, uygulamayı geçirmede bir değer olabilir. Geçiş farklı şekiller alabilir; Bu, tüm uygulama veya yalnızca değişiklik gerektiren belirli uç noktalar olabilir. Geçiş kararı, sonuçta geliştirici tarafından çözülmesi gereken iş sorunlarına göre belirlenir.

## <a name="server-side-versus-client-side-hosting"></a>Sunucu tarafı ve istemci tarafı barındırma

[Barındırma modelleri](hosting-models.md) bölümünde açıklandığı gibi, bir Blazor uygulama iki farklı şekilde barındırılabilir: sunucu tarafı ve istemci tarafı. Sunucu tarafı modeli, sunucuda herhangi bir gerçek kod çalıştırırken DOM güncelleştirmelerini yönetmek için ASP.NET Core SignalR bağlantılarını kullanır. İstemci tarafı modeli WebAssembly bir tarayıcı içinde olarak çalışır ve sunucu bağlantısı gerektirmez. Belirli bir uygulama için en iyi sonucu etkileyebilecek birçok fark vardır:

- Farklı çalıştırma WebAssembly hala geliştirme aşamasındadır ve geçerli zamanda tüm özellikleri (iş parçacığı oluşturma gibi) desteklemeyebilir
- İstemci ile sunucu arasındaki geveze iletişimi, sunucu tarafı modunda gecikme sorunlarına neden olabilir
- Veritabanlarına ve iç veya korumalı hizmetlere erişim, istemci tarafı barındırma ile ayrı bir hizmet gerektirir

Yazma sırasında, sunucu tarafı modeli Web Forms daha yakından benzerdir. Bu bölümün çoğu, üretime hazırsa da sunucu tarafı barındırma modeline odaklanır.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

Bu ilk geçiş adımı yeni bir proje oluşturmaktır. Bu proje türü, .NET Core SDK stili projelerine dayalıdır ve önceki proje biçimlerinde kullanılan ortak alanının çoğunu basitleştirir. Daha fazla ayrıntı için lütfen [Proje yapısındaki](project-structure.md)bölüme bakın.

Proje oluşturulduktan sonra, önceki projede kullanılan kitaplıkları yükler. Daha eski Web Forms projelerinde, gerekli NuGet paketlerini listelemek için *packages.config* dosyasını kullanmış olabilirsiniz. Yeni SDK stili projesinde *packages.config* `<PackageReference>` Proje dosyasındaki öğelerle değiştirilmiştir. Bu yaklaşımın bir avantajı, tüm bağımlılıkların geçişli olarak yüklenmesini sağlar. Yalnızca ilgilendiğiniz en üst düzey bağımlılıkları listeleyin.

Kullandığınız bağımlılıkların birçoğu .NET Core için Entity Framework 6 ve Log4net dahil olmak üzere kullanılabilir. .NET Core veya .NET Standard sürümü yoksa, .NET Framework sürüm genellikle kullanılabilir. Mesafe, farklılık gösterebilir. .NET Core 'da kullanılamayan API 'leri, çalışma zamanı hatasına neden olur. Visual Studio bu tür paketleri size bildirir. Projenin **Başvurular** düğümünde **Çözüm Gezgini**sarı bir simge görünür.

BlazorTabanlı eShop projesinde, yüklü olan paketleri görebilirsiniz. Daha önce, projede kullanılan her pakette listelenen *packages.config* dosyası, neredeyse 50 satır uzunluğuna neden olur. *packages.config* bir kod parçacığı:

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

`<packages>`Öğesi tüm gerekli bağımlılıkları içerir. İhtiyaç duyduğunuz bu paketlerin hangisinin dahil edileceğini belirlemek zordur. Bazı `<package>` öğeler yalnızca ihtiyaç duyduğunuz bağımlılıkların ihtiyaçlarını karşılamak için listelenir.

BlazorProje, proje dosyasındaki bir öğe içinde gerekli olan bağımlılıkları listeler `<ItemGroup>` :

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Web Forms geliştiricilerin ömrünü basitleştiren bir NuGet paketi [Windows Uyumluluk paketidir](../../core/porting/windows-compat-pack.md). .NET Core platformlar arası olsa da bazı özellikler yalnızca Windows 'da kullanılabilir. Windows 'a özgü özellikler, uyumluluk paketi yüklenerek kullanılabilir hale getirilir. Bu özelliklere örnek olarak kayıt defteri, WMI ve dizin hizmetleri dahildir. Paket, 20.000 API etrafında ekleme yapar ve çok daha bildiğiniz hizmetleri etkinleştirir. EShop projesi, uyumluluk paketi gerektirmez; Ancak projeleriniz Windows 'a özgü özellikler kullanıyorsa, paket geçiş çalışmalarını kolaylaştırır.

## <a name="enable-startup-process"></a>Başlatma işlemini etkinleştir

İçin başlatma işlemi Blazor Web Forms ' dan değişmiştir ve diğer ASP.NET Core Hizmetleri için benzer bir kuruluma uyar. Sunucu tarafında barındırılan Blazor Bileşenler, normal ASP.NET Core uygulamasının bir parçası olarak çalıştırılır. Tarayıcıda barındırıldığında WebAssembly , Blazor Bileşenler benzer bir barındırma modeli kullanır. Bunun farkı, bileşenlerin arka uç işlemlerinden herhangi birinden ayrı bir hizmet olarak çalıştırılmaktır. Her iki durumda da başlatma benzerdir.

*Global.asax.cs* dosyası Web Forms projeler için varsayılan başlangıç sayfasıdır. EShop projesinde, bu dosya denetim (IOC) kapsayıcısının Inversion öğesini yapılandırır ve uygulamanın veya isteğin çeşitli yaşam döngüsü olaylarını işler. Bu olaylardan bazıları ara yazılım (gibi) ile işlenir `Application_BeginRequest` . Diğer olaylar, bağımlılık ekleme (dı) aracılığıyla belirli Hizmetleri geçersiz kılmayı gerektirir.

Örnek olarak, eShop için *Global.asax.cs* dosyası aşağıdaki kodu içerir:

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

Yukarıdaki dosya, `Startup` sunucu tarafında sınıfı olur Blazor :

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

Web Forms fark ettiğiniz önemli bir değişiklik, dı 'nin göze çarkadır. DI, ASP.NET Core tasarımında bir temel prensibi ilkesidir. ASP.NET Core çerçevesinin neredeyse tüm yönlerini özelleştirmeyi destekler. Birçok senaryo için kullanılabilen yerleşik bir hizmet sağlayıcısı da vardır. Daha fazla özelleştirme gerekliyse, bu, çok sayıda topluluk projesi tarafından desteklenebilir. Örneğin, üçüncü taraf dı kitaplığı yatırımınızdan ileri taşıyabilirsiniz.

Özgün eShop uygulamasında, oturum yönetimi için bir yapılandırma vardır. Sunucu tarafı Blazor iletişim için ASP.NET Core SignalR kullandığından, bağlantılar BIR http bağlamından bağımsız olarak gerçekleşemediğinden oturum durumu desteklenmez. Oturum durumunu kullanan bir uygulama, uygulama olarak çalışmadan önce yeniden mimari gerektirir Blazor .

Uygulama başlatma hakkında daha fazla bilgi için bkz. [uygulama başlatma](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>HTTP modüllerini ve işleyicileri ara yazılıma geçirme

Http modülleri ve işleyicileri, HTTP isteği ardışık düzenini denetlemek için Web Forms içindeki yaygın desenlerdir. `IHttpModule`Veya `IHttpHandler` ' i uygulayan veya gelen istekleri işleyecek sınıflar. Web Forms, *web.config* dosyasındaki modülleri ve işleyicileri yapılandırır. Web Forms Ayrıca uygulama yaşam döngüsü olay işlemeye bağlıdır. ASP.NET Core bunun yerine ara yazılım kullanır. Ara yazılım, `Configure` sınıfının yöntemine kaydedilir `Startup` . Ara yazılım yürütme sırası, kayıt sırasına göre belirlenir.

[Başlatma Işlemini etkinleştir](#enable-startup-process) bölümünde, yöntemi olarak Web Forms bir yaşam döngüsü olayı tetiklenir `Application_BeginRequest` . Bu olay ASP.NET Core ' de kullanılamaz. Bu davranışı gerçekleştirmenin bir yolu, ara yazılımı *Startup.cs* File örneğinde görüldüğü gibi uygulamaktır. Bu ara yazılım aynı mantığı yapar ve denetimi, ara yazılım ardışık düzeninde bir sonraki işleyiciye aktarır.

Modül ve işleyicileri geçirme hakkında daha fazla bilgi için bkz. [http işleyicilerini ve modülleri ASP.NET Core ara yazılıma geçirme](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Statik dosyaları geçirme

Statik dosyalara (örneğin, HTML, CSS, resim ve JavaScript) sahip olmak için dosyalar, ara yazılım tarafından sunulmalıdır. Yöntemi çağırmak, `UseStaticFiles` statik dosyaların Web kök yolundan kullanılmasına izin veriyor. Varsayılan Web kök dizini *Wwwroot*, ancak özelleştirilebilir. `Configure`EShop sınıfının yöntemine dahil edilmiştir `Startup` :

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

EShop projesi, temel statik dosya erişimine izin vermez. Statik dosya erişimi için kullanılabilen birçok özelleştirme vardır. Varsayılan dosyaların veya bir dosya tarayıcısının etkinleştirilmesi hakkında daha fazla bilgi için [ASP.NET Core Içindeki statik dosyalar](/aspnet/core/fundamentals/static-files)bölümüne bakın.

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Çalışma zamanı paketleme ve küçültmeye yönelik kurulumu geçirme

Paketleme ve en iyi duruma getirme, belirli dosya türlerini almak üzere sunucu isteklerinin sayısını ve boyutunu azaltmak için performans iyileştirme tekniklerdir. JavaScript ve CSS genellikle istemciye gönderilmeden önce bir dizi paketleme veya küçültmeye göre daha fazla gider. ASP.NET Web Forms içinde, bu iyileştirmeler çalışma zamanında işlenir. En iyi duruma getirme kuralları bir *App_Start/paketlemeli bir config.cs* dosyası tanımladı. ASP.NET Core, daha açıklayıcı bir yaklaşım benimsemiştir. Bir dosya, Mini olarak kullanılacak dosyaları ve belirli bir küçültmeye yönelik ayarları listeler.

Paketleme ve küçültmeye yönelik daha fazla bilgi için, bkz. [ASP.NET Core statik varlıkları paketleme ve](/aspnet/core/client-side/bundling-and-minification)azaltma.

## <a name="migrate-aspx-pages"></a>ASPX sayfalarını geçirme

Web Forms uygulamasındaki bir sayfa *. aspx* uzantılı bir dosyadır. Bir Web Forms sayfası, genellikle içindeki bir bileşenle eşleştirilebilir Blazor . Bir Blazor bileşen *. Razor* uzantılı bir dosyada yazılır. EShop projesi için beş sayfa Razor sayfasına dönüştürülür.

Örneğin, Ayrıntılar görünümü Web Forms projesindeki üç dosya içerir: *details. aspx*, *details.aspx.cs*ve *details.aspx.Designer.cs*. Blazor' A dönüştürme yaparken, arka plan kodu ve biçimlendirme *details. Razor*içinde birleştirilir. Razor derlemesi ( *. Designer.cs* dosyaları için eşdeğer) *obj* dizininde depolanır ve varsayılan olarak **Çözüm Gezgini**görüntülenebilir. Web Forms sayfası aşağıdaki biçimlendirmeden oluşur:

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

Önceki biçimlendirmenin arka plan kodu aşağıdaki kodu içerir:

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

' A dönüştürüldüğünde Blazor , Web Forms sayfası aşağıdaki koda çevirir:

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

Kodun ve biçimlendirmenin aynı dosyada olduğuna dikkat edin. Gerekli hizmetlere, özniteliğiyle erişilebilir hale getirilir `@inject` . `@page`Yönergeye göre, bu sayfaya `Catalog/Details/{id}` rotada erişilebilir. Yolun `{id}` yer tutucusunun değeri bir tamsayı ile kısıtlanıyor. [Yönlendirme](pages-routing-layouts.md) bölümünde açıklandığı gibi, Web Forms aksine bir Razor bileşeni, kendi yolunu ve dahil edilen tüm parametreleri açıkça belirtir. Birçok Web Forms denetimi ' de tam karşılıklarıyla eşleşmeyebilir Blazor . Genellikle aynı amacı sunan eşdeğer bir HTML kod parçacığı vardır. Örneğin, `<asp:Label />` Denetim BIR HTML `<label>` öğesiyle değiştirilebilir.

### <a name="model-validation-in-no-locblazor"></a>İçindeki model doğrulaması Blazor

Web Forms kodunuz doğrulamayı içeriyorsa, az sayıda değişiklik ile sahip olduğunuz kadarını aktarabilirsiniz. İçinde çalıştırmanın bir avantajı, Blazor aynı doğrulama mantığının özel JavaScript gerekmeden çalıştırılmamasının bir avantajıdır. Veri ek açıklamaları kolay model doğrulamayı etkinleştirir.

Örneğin, *Create. aspx* sayfasında doğrulama içeren bir veri girişi formu vardır. Örnek parçacığı şöyle görünür:

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

Blazor' De, eşdeğer biçimlendirme bir *Create. Razor* dosyasında verilmiştir:

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

`EditForm`Bağlam doğrulama desteğini içerir ve girişin etrafında sarmalanabilir. Veri ek açıklamaları, doğrulama eklemenin yaygın bir yoludur. Bu tür doğrulama desteği bileşen aracılığıyla eklenebilir `DataAnnotationsValidator` . Bu mekanizma hakkında daha fazla bilgi için bkz. [ASP.NET Core Blazor Forms ve Validation](/aspnet/core/blazor/forms-validation).

## <a name="migrate-configuration"></a>Yapılandırmayı geçir

Web Forms projesinde, yapılandırma verileri genellikle *web.config* dosyasında depolanır. Yapılandırma verilerine ile erişilir `ConfigurationManager` . Hizmetler genellikle nesneleri ayrıştırmak için gereklidir. .NET Framework 4.7.2 ile, ile yapılandırma için bileşim eklenmiştir `ConfigurationBuilders` . Bu oluşturucular, geliştiricilerin gerekli değerleri almak için çalışma zamanında oluşturulan yapılandırma için çeşitli kaynaklar eklemesine izin verilir.

ASP.NET Core, uygulamanız ve dağıtımınız tarafından kullanılan yapılandırma kaynağını veya kaynaklarını tanımlamanızı sağlayan esnek bir yapılandırma sistemi sunmuştur. `ConfigurationBuilder`Web Forms uygulamanızda kullandığınız altyapı, ASP.NET Core yapılandırma sisteminde kullanılan kavramlardan sonra modellenmiştir.

Aşağıdaki kod parçacığında Web Forms eShop projesinin yapılandırma değerlerini depolamak için *web.config* nasıl kullandığı gösterilmektedir:

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

Veritabanı bağlantı dizeleri gibi, *web.config*içinde depolanacak gizli dizileri yaygındır. Gizli dizileri, kaynak denetimi gibi güvenli olmayan konumlarda kalıcı olarak kalıcı hale getirilir. BlazorASP.NET Core ile, ÖNCEKI XML tabanlı yapılandırma AŞAĞıDAKI JSON ile değiştirilmiştir:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON varsayılan yapılandırma biçimidir; Ancak, ASP.NET Core XML gibi birçok diğer biçimi destekler. Ayrıca, topluluk tarafından desteklenen birkaç biçim vardır.

Projenin sınıfındaki Oluşturucu, Blazor `Startup` `IConfiguration` Oluşturucu ekleme olarak bilinen bir dı tekniği aracılığıyla bir örneği kabul eder:

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

Varsayılan olarak, ortam değişkenleri, JSON dosyaları (*appsettings.js* ve *appSettings. { Environment}. JSON*) ve komut satırı seçenekleri yapılandırma nesnesinde geçerli yapılandırma kaynakları olarak kaydedilir. Yapılandırma kaynaklarına aracılığıyla erişilebilir `Configuration[key]` . Daha gelişmiş bir teknik, yapılandırma verilerini nesnelere bağlamak için seçenekler örüntüsünün kullanılmasını sağlar. Yapılandırma ve seçenekler düzeniyle ilgili daha fazla bilgi için sırasıyla ASP.NET Core [ASP.NET Core](/aspnet/core/fundamentals/configuration/) ve [Seçenekler](/aspnet/core/fundamentals/configuration/options)düzeninde yapılandırma konusuna bakın.

## <a name="migrate-data-access"></a>Veri erişimini geçirme

Veri erişimi, tüm uygulamaların önemli bir yönüdür. EShop projesi, katalog bilgilerini bir veritabanında depolar ve Entity Framework (EF) 6 ile verileri alır. .NET Core 3,0 ' de EF 6 desteklendiğinden, proje onu kullanmaya devam edebilir.

Aşağıdaki EF ile ilgili değişiklikler eShop için gereklidir:

- .NET Framework, `DbContext` nesnesi *Name = ConnectionString* biçiminde bir dize kabul eder ve bağlantı dizesini `ConfigurationManager.AppSettings[ConnectionString]` bağlamak için kullanır. .NET Core 'da bu desteklenmez. Bağlantı dizesinin sağlanması gerekir.
- Veritabanına zaman uyumlu bir şekilde erişildi. Bu işlem çalışsa da ölçeklenebilirlik düşebilir. Bu mantık zaman uyumsuz bir modele taşınmalıdır.

Veri kümesi bağlama için aynı yerel destek olmasa da, Blazor Razor sayfasında C# desteğiyle esneklik ve güç sağlar. Örneğin, hesaplamalar yapabilir ve sonucu görüntüleyebilirsiniz. İçindeki veri desenleri hakkında daha fazla bilgi için Blazor bkz. [veri erişimi](data.md) bölümü.

## <a name="architectural-changes"></a>Mimari değişiklikler

Son olarak, ' a geçiş yaparken göz önünde bulundurmanız gereken bazı önemli mimari farklılıklar vardır Blazor . Bu değişikliklerin çoğu, .NET Core veya ASP.NET Core temel alınarak herhangi bir şey için geçerlidir.

Blazor, .NET Core üzerine inşa edildiğinden, .NET Core üzerinde destek sağlamaya yönelik hususlar vardır. Bazı önemli değişikliklerden bazıları aşağıdaki özelliklerin kaldırılmasını içerir:

- Birden çok AppDomain
- Uzaktan iletişim
- Kod Erişimi Güvenliği (CAS)
- Güvenlik saydamlığı

.NET Core üzerinde çalışmayı desteklemek için gereken değişiklikleri belirlemek için teknikler hakkında daha fazla bilgi için bkz. [.NET Framework kodunuzun bağlantı noktası, .NET Core](../../core/porting/index.md).

ASP.NET Core, ASP.NET 'in yeniden oluşturulmuş bir sürümüdür ve başlangıçta belirgin bir şekilde görünmeyebilir bazı değişiklikler içerir. Ana değişiklikler şunlardır:

- Hiçbir eşitleme bağlamı yoktur, bu, `HttpContext.Current` `Thread.CurrentPrincipal` veya diğer statik erişimciler anlamına gelir
- Gölge kopyalama yok
- İstek kuyruğu yok

ASP.NET Core çok sayıda işlem zaman uyumsuzdur ve g/ç bağlantılı görevlerin daha kolay bir şekilde yüklenmesini sağlar. `Task.Wait()` `Task.GetResult()` İş parçacığı havuzu kaynaklarını hızlıca tüketebilen veya kullanılarak hiçbir şekilde engellenmemek önemlidir.

## <a name="migration-conclusion"></a>Geçiş sonucu

Bu noktada, bir Web Forms projesinin ne kadar sürdüğü hakkında birçok örnek gördünüz Blazor . Tam bir örnek için bkz. [Eshopon Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor) projesi.

>[!div class="step-by-step"]
>[Önceki](security-authentication-authorization.md)
