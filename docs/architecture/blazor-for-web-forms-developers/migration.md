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
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>ASP.NET Web Formlarından Blazor'a geçiş

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bir kod tabanını ASP.NET Web Formlarından Blazor'a geçirmek, planlama gerektiren zaman alan bir görevdir. Bu bölümde süreç özetlenir. Geçişi kolaylaştırabilecek bir şey, uygulamanın N *katmanlı* bir mimariye uymasını sağlamaktır, bu durumda uygulama modeli (bu durumda Web Formları) iş mantığından ayrıdır. Katmanların bu mantıksal ayrımı,.NET Core ve Blazor'a taşınması gerekenleri açıkça ortaya koyuyor.

Bu örnekte, [GitHub'da](https://github.com/dotnet-architecture/eShopOnBlazor) bulunan eShop uygulaması kullanılır. eShop form girişi ve doğrulama yoluyla CRUD yetenekleri sağlayan bir katalog hizmetidir.

Çalışan bir uygulama neden Blazor'a geçirilmelidir? Çoğu zaman, gerek yok. ASP.NET Web Formları uzun yıllar desteklenmeye devam edecektir. Ancak, Blazor'un sağladığı özelliklerin çoğu yalnızca geçirilen bir uygulamada desteklenir. Bu özellikler şunlardır:

- gibi çerçevede performans iyileştirmeleri`Span<T>`
- WebAssembly olarak çalışma becerisi
- Linux ve macOS için çapraz platform desteği
- Diğer uygulamaları etkilemeden uygulama yerel dağıtımı veya paylaşılan çerçeve dağıtımı

Bu veya diğer yeni özellikler yeterince ilgi çekiciyse, uygulamayı geçirmenin bir değeri olabilir. Geçiş farklı şekillerde alabilir; uygulamanın tamamı veya değişiklikleri gerektiren yalnızca belirli uç noktalar olabilir. Geçiş kararı sonuçta geliştirici tarafından çözülecek iş sorunlarına dayanır.

## <a name="server-side-versus-client-side-hosting"></a>Sunucu tarafı ve istemci tarafı barındırma

[Barındırma modelleri](hosting-models.md) bölümünde açıklandığı gibi, bir Blazor uygulaması iki farklı şekilde barındırılabilir: sunucu tarafı ve istemci tarafı. Sunucu tarafındaki model, sunucuda herhangi bir gerçek kodu çalıştırırken DOM güncelleştirmelerini yönetmek için ASP.NET Core SignalR bağlantılarını kullanır. İstemci tarafı modeli tarayıcı içinde WebAssembly olarak çalışır ve sunucu bağlantısı gerektirmez. Belirli bir uygulama için en iyi etkiyi etkileyebilecek farklılıklar vardır:

- WebAssembly olarak çalışan hala geliştirme aşamasındadır ve geçerli zamanda tüm özellikleri (iş parçacığı gibi) desteklemeyebilir
- İstemci ve sunucu arasındaki geveze iletişim, sunucu tarafındaki modda gecikme sorunlarına neden olabilir
- Veritabanlarına ve dahili veya korumalı hizmetlere erişim, istemci tarafı barındırma ile ayrı bir hizmet gerektirir

Yazma sırasında, sunucu tarafındaki model Web Formlarına daha yakından benzer. Bu bölümün çoğu, üretime hazır olduğu için sunucu tarafındaki barındırma modeline odaklanır.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

Bu ilk geçiş adımı yeni bir proje oluşturmaktır. Bu proje türü .NET Core'un SDK tarzı projelerini temel almaktadır ve önceki proje biçimlerinde kullanılan kazan plakasının çoğunu basitleştirir. Daha fazla ayrıntı için lütfen [Proje Yapısı](project-structure.md)bölümüne bakın.

Proje oluşturulduktan sonra, önceki projede kullanılan kitaplıkları yükleyin. Eski Web Formları projelerinde, gerekli NuGet paketlerini listelemek için *packages.config* dosyasını kullanmış olabilirsiniz. Yeni SDK tarzı projede, *packages.config* proje `<PackageReference>` dosyasındaki öğelerle değiştirildi. Bu yaklaşımın bir yararı, tüm bağımlılıkların geçişli olarak yüklenmesidir. Yalnızca önemsediğiniz üst düzey bağımlılıkları listelersiniz.

Kullanmakta olduğunuz bağımlılıkların çoğu Entity Framework 6 ve log4net dahil olmak üzere .NET Core için kullanılabilir. .NET Core veya .NET Standard sürümü yoksa, .NET Framework sürümü genellikle kullanılabilir. Kilometreniz değişebilir. .NET Core'da bulunmayan herhangi bir API çalışma zamanı hatasına neden olur. Visual Studio bu tür paketleri size ileter. **Çözüm**Gezgini'nde projenin **Başvuru düğümünde** sarı bir simge görünür.

Blazor tabanlı eShop projesinde, yüklenen paketleri görebilirsiniz. Daha *önce, packages.config* dosyası projede kullanılan her paketi listeleyerek neredeyse 50 satır uzunluğunda bir dosyayla sonuçlanıyor. *Paketler.config* bir snippet olduğunu:

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

Öğe `<packages>` gerekli tüm bağımlılıkları içerir. Bu paketlerden hangisinin dahil olduğunu belirlemek zordur, çünkü bunlara gereksinim duyarsınız. Bazı `<package>` öğeler yalnızca gereksinim duyduğunuz bağımlılıkların gereksinimlerini karşılamak için listelenir.

Blazor projesi, proje dosyasındaki bir `<ItemGroup>` öğe içinde gereksinim duyduğunuz bağımlılıkları listeler:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Web Formları geliştiricilerin ömrünü kolaylaştıran bir NuGet paketi [Windows Uyumluluk Paketidir.](../../core/porting/windows-compat-pack.md) .NET Core çapraz platform olmasına rağmen, bazı özellikler yalnızca Windows'da kullanılabilir. Uyumluluk paketini yükleyerek Windows'a özgü özellikler kullanılabilir hale getirilir. Bu tür özelliklere örnek olarak Kayıt Defteri, WMI ve Dizin Hizmetleri verilebilir. Paket yaklaşık 20.000 API ekler ve zaten tanıdık olabileceğiniz birçok hizmeti etkinleştirir. eShop projesi uyumluluk paketi gerektirmez; ancak projeleriniz Windows'a özgü özellikler kullanıyorsa, paket geçiş çabalarını kolaylaştırır.

## <a name="enable-startup-process"></a>Başlatma işlemini etkinleştirme

Blazor için başlangıç işlemi Web Formlar'dan değiştirildi ve diğer ASP.NET Core hizmetleri için benzer bir kurulum izler. Sunucu tarafından barındırıldığında, Blazor bileşenleri normal bir ASP.NET Core uygulamasının bir parçası olarak çalıştırılır. WebAssembly ile tarayıcıda barındırıldığında, Blazor bileşenleri benzer bir barındırma modeli kullanır. Fark bileşenleri arka uç işlemlerinin herhangi birinden ayrı bir hizmet olarak çalıştırılır. Her iki şekilde de, başlangıç benzer.

*Global.asax.cs* dosyası, Web Formları projeleri için varsayılan başlangıç sayfasıdır. eShop projesinde, bu dosya Denetimin Ters Çevrilmesi (IoC) kapsayıcısını yapılandırır ve uygulamanın veya isteğin çeşitli yaşam döngüsü olaylarını işler. Bu olaylardan bazıları ara yazılımla `Application_BeginRequest`işlenir (örneğin). Diğer olaylar bağımlılık enjeksiyonu (DI) yoluyla belirli hizmetlerin geçersiz kılınması gerekir.

Örnek olarak, eShop için *Global.asax.cs* dosyası, aşağıdaki kodu içerir:

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

Önceki dosya sunucu `Startup` tarafı Blazor sınıf olur:

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

Web Formlar'dan fark edebilirsiniz önemli bir değişiklik DI önem olduğunu. DI ASP.NET Core tasarımında yol gösterici bir ilke olmuştur. ASP.NET Core çerçevesinin hemen hemen tüm yönlerinin özelleştirilmesini destekler. Hatta birçok senaryo için kullanılabilecek yerleşik bir hizmet sağlayıcısı vardır. Daha fazla özelleştirme gerekiyorsa, birçok topluluk projesi tarafından desteklenebilir. Örneğin, üçüncü taraf DI kitaplığı yatırımınızı ileriye taşıyabilirsiniz.

Orijinal eShop uygulamasında, oturum yönetimi için bazı yapılandırmalar vardır. Sunucu tarafı Blazor iletişim için ASP.NET Core SignalR kullandığından, bağlantılar bir HTTP bağlamından bağımsız olarak oluşabileceğinden oturum durumu desteklenmez. Oturum durumunu kullanan bir uygulama, Blazor uygulaması olarak çalıştırmadan önce yeniden yeniden tasarlanması gerekir.

Uygulama başlatma hakkında daha fazla bilgi için [Uygulama başlangıç](app-startup.md)bilgisine bakın.

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>HTTP modüllerini ve işleyicilerini ara yazılıma geçirin

HTTP modülleri ve işleyicileri, HTTP istek ardışık düzenini denetlemek için Web Formları'nda yaygın desenlerdir. Gelen istekleri `IHttpModule` `IHttpHandler` uygulayan veya kaydedilebilen sınıflar. Web *Forms, web.config* dosyasındaki modülleri ve işleyicileri yapılandırır. Web Formları da ağır uygulama yaşam döngüsü olay işleme dayanmaktadır. ASP.NET Core bunun yerine ara yazılım kullanır. Middleware sınıfın yönteminde `Configure` `Startup` kayıtlıdır. Middleware yürütme emri kayıt emri ile belirlenir.

Başlatma [işlemini etkinleştir](#enable-startup-process) bölümünde, `Application_BeginRequest` yöntem olarak Web Forms tarafından bir yaşam döngüsü olayı yükseltildi. Bu etkinlik ASP.NET Core'da kullanılamaz. Bu davranışı elde etmenin bir yolu, *Startup.cs* dosyası örneğinde görüldüğü gibi ara yazılım uygulamaktır. Bu ara yazılım aynı mantığı yapar ve sonra denetimi ara yazılım ardışık ardışık ardışık ardışık bir sonraki işleyiciye aktarır.

Geçiş modülleri ve işleyicileri hakkında daha fazla bilgi için, [Core ara yazılımASP.NET için http işleyicileri ve modülleri geçirin](/aspnet/core/migration/http-modules)bakın.

## <a name="migrate-static-files"></a>Statik dosyaları geçir

Statik dosyalara (örneğin, HTML, CSS, resimler ve JavaScript) hizmet vermek için, dosyaların ara yazılımtarafından açıkta kalması gerekir. `UseStaticFiles` Yöntemi çağırmak, statik dosyaların web kök yolundan sunulmasını sağlar. Varsayılan web kök dizini *wwwroot,* ancak özelleştirilebilir. eShop'un `Startup` `Configure` sınıfının yöntemine dahil edildiği gibi:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

eShop projesi temel statik dosya erişimini sağlar. Statik dosya erişimi için birçok özelleştirme vardır. Varsayılan dosyaları veya dosya tarayıcısını etkinleştirme hakkında bilgi için [ASP.NET Core'daki Statik dosyalara](/aspnet/core/fundamentals/static-files)bakın.

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Çalışma zamanı birleştirme ve minification kurulum geçiş

Birleştirme ve azaltma, belirli dosya türlerini almak için sunucu isteklerinin sayısını ve boyutunu azaltmak için performans optimizasyonu teknikleridir. JavaScript ve CSS genellikle istemciye gönderilmeden önce birleştirme veya minification çeşit tabi. Web Formlar ASP.NET bu optimizasyonlar çalışma zamanında işlenir. Optimizasyon kuralları bir *App_Start/BundleConfig.cs* dosyası olarak tanımlanır. ASP.NET Core'da daha açıklayıcı bir yaklaşım benimsenmiştir. Bir dosya, belirli minification ayarları ile birlikte minified edilecek dosyaları listeler.

Donma ve kıyma hakkında daha fazla bilgi için, [ASP.NET Core'daki Bundle ve minify statik varlıkları](/aspnet/core/client-side/bundling-and-minification)görün.

## <a name="migrate-aspx-pages"></a>ASPX sayfalarını geçir

Web Forms uygulamasındaki bir sayfa *.aspx* uzantılı bir dosyadır. Web Formları sayfası genellikle Blazor'daki bir bileşenle eşlenebilir. Blazor bileşeni *.razor* uzantılı bir dosyada yazılır. eShop projesi için beş sayfa Jilet sayfasına dönüştürülür.

Örneğin, ayrıntı görünümü Web Formları projesinde üç dosyadan oluşur: *Details.aspx*, *Details.aspx.cs*ve *Details.aspx.designer.cs.* Blazor'a dönüştürürken, kod arkası ve biçimlendirme *Details.razor*olarak birleştirilir. Jilet derlemesi *(.designer.cs* dosyalarındakine eşdeğer) *obj* dizininde depolanır ve varsayılan olarak **Solution Explorer'da**görüntülenebilir değildir. Web Formları sayfası aşağıdaki biçimlendirmeden oluşur:

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

Önceki biçimlendirmenin kod arkası aşağıdaki kodu içerir:

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

Blazor'a dönüştürüldüğünde, Web Formları sayfası aşağıdaki koda çevirir:

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

Kod ve biçimlendirmenin aynı dosyada olduğuna dikkat edin. Gerekli tüm hizmetler öznitelik `@inject` ile erişilebilir hale getirilir. Yönerge `@page` ye göre, bu sayfaya `Catalog/Details/{id}` rotadan erişilebilir. Rotanın `{id}` yer tutucunun değeri bir sonal ile sınırlandırılmıştır. [Yönlendirme](pages-routing-layouts.md) bölümünde açıklandığı gibi, Web Formlarından farklı olarak, bir Razor bileşeni rotasını ve dahil olan parametreleri açıkça belirtir. Birçok Web Forms denetimiblazor tam muadilleri olmayabilir. Genellikle aynı amaca hizmet edecek eşdeğer bir HTML snippet var. Örneğin, `<asp:Label />` denetim bir HTML `<label>` öğesi ile değiştirilebilir.

### <a name="model-validation-in-blazor"></a>Blazor'da model doğrulaması

Web Formları kodunuz doğrulama içeriyorsa, sahip olduğunuz değişikliklerin çoğunu az-hiç değişiklikle aktarabilirsiniz. Blazor çalışan bir yararı, aynı doğrulama mantığı özel JavaScript gerek kalmadan çalıştırılabilir olmasıdır. Veri ek açıklamaları kolay model doğrulama sağlar.

Örneğin, *Create.aspx* sayfasında doğrulama içeren bir veri giriş formu vardır. Örnek bir snippet şuna benzer:

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

Blazor'da eşdeğer biçimlendirme *Create.razor* dosyasında sağlanır:

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

Bağlam `EditForm` doğrulama desteği içerir ve giriş etrafında sarılmış olabilir. Veri ek açıklamaları doğrulama eklemek için yaygın bir yoldur. Bu tür doğrulama desteği `DataAnnotationsValidator` bileşen üzerinden eklenebilir. Bu mekanizma hakkında daha fazla bilgi [için, ASP.NET Core Blazor formları ve doğrulama](/aspnet/core/blazor/forms-validation)bakın.

## <a name="migrate-built-in-web-forms-controls"></a>Yerleşik Web Formları denetimlerini geçirin

*Bu içerik yakında geliyor.*

## <a name="migrate-configuration"></a>Yapılandırmayı geçir

Bir Web Forms projesinde, yapılandırma verileri en sık *web.config* dosyasında depolanır. Yapılandırma verilerine . `ConfigurationManager` Nesneleri ayrıştırmak için genellikle hizmetler gereklidir. .NET Framework 4.7.2 ile yapılandırmaya .composability ile `ConfigurationBuilders`eklendi. Bu oluşturucular, geliştiricilerin gerekli değerleri almak için çalışma zamanında oluşturulan yapılandırma için çeşitli kaynaklar eklemelerine olanak tanır.

ASP.NET Core, uygulamanız ve dağıtımınız tarafından kullanılan yapılandırma kaynağını veya kaynakları tanımlamanızı sağlayan esnek bir yapılandırma sistemi tanıttı. Web `ConfigurationBuilder` Formları uygulamanızda kullanıyor olabileceğiniz altyapı, ASP.NET Core yapılandırma sisteminde kullanılan kavramlardan sonra modellenmiştir.

Aşağıdaki parçacık, Web Forms eShop projesinin yapılandırma değerlerini depolamak için *web.config'i* nasıl kullandığını gösterir:

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

Veritabanı bağlantı dizeleri gibi sırların *web.config*içinde depolanması yaygındır. Sırlar kaçınılmaz olarak kaynak denetimi gibi güvenli olmayan konumlarda devam edilir. Blazor ASP.NET Core ile, önceki XML tabanlı yapılandırma aşağıdaki JSON ile değiştirilir:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON varsayılan yapılandırma biçimidir; ancak, ASP.NET Core XML de dahil olmak üzere birçok diğer biçimleri destekler. Topluluk destekli çeşitli biçimler de vardır.

Blazor projesinin `Startup` sınıfındaki oluşturucu, yapıcı `IConfiguration` enjeksiyon olarak bilinen bir DI tekniği ile bir örneği kabul eder:

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

Varsayılan olarak, ortam değişkenleri, JSON dosyaları *(appsettings.json* ve *appsettings.{ Environment}.json*), ve komut satırı seçenekleri yapılandırma nesnesinde geçerli yapılandırma kaynakları olarak kaydedilir. Yapılandırma kaynaklarına `Configuration[key]`. Daha gelişmiş bir teknik, seçenekler deseni kullanarak yapılandırma verilerini nesnelere bağlamaktır. Yapılandırma ve seçenekler deseni hakkında daha fazla bilgi için sırasıyla ASP.NET [Core'daki ASP.NET Çekirdek](/aspnet/core/fundamentals/configuration/) ve [Seçenekler desenindeki Yapılandırma'ya](/aspnet/core/fundamentals/configuration/options)bakın.

## <a name="migrate-data-access"></a>Veri erişimini geçirin

Veri erişimi herhangi bir uygulamanın önemli bir yönüdür. eShop projesi katalog bilgilerini bir veritabanında saklar ve verileri Entity Framework (EF) 6 ile alır. EF 6 .NET Core 3.0'da desteklendirilebildiği için proje kullanmaya devam edebilir.

EShop için ef ile ilgili aşağıdaki değişiklikler gerekliydi:

- .NET Framework'de `DbContext` nesne form *adı=ConnectionString* dizesini kabul eder `ConfigurationManager.AppSettings[ConnectionString]` ve bağlanmak için bağlantı dizesini kullanır. .NET Core'da bu desteklenmez. Bağlantı dizesi sağlanmalıdır.
- Veritabanına eşzamanlı bir şekilde erişildi. Bu işe yarasa da, ölçeklenebilirlik zarar görebilir. Bu mantık bir eşzamanlı desen taşınmalıdır.

Veri kümesi bağlama için aynı yerel destek olmamasına rağmen, Blazor bir Razor sayfasında C# desteği ile esneklik ve güç sağlar. Örneğin, hesaplamalar yapabilir ve sonucu görüntüleyebilirsiniz. Blazor'daki veri desenleri hakkında daha fazla bilgi için [Veri erişim](data.md) bölümüne bakın.

## <a name="architectural-changes"></a>Mimari değişiklikler

Son olarak, Blazor'a göç ederken göz önünde bulundurulması gereken bazı önemli mimari farklılıklar vardır. Bu değişikliklerin çoğu .NET Core veya ASP.NET Core tabanlı her şey için geçerlidir.

Blazor .NET Core üzerine kurulduğundan, .NET Core'da destek sağlamada dikkat edilmesi gereken hususlar vardır. Önemli değişikliklerden bazıları aşağıdaki özelliklerin kaldırılmasını içerir:

- Birden Fazla AppDomains
- Remoting
- Kod Erişimi Güvenliği (CAS)
- Güvenlik Şeffaflığı

.NET Core'da çalıştırmayı desteklemek için gerekli değişiklikleri belirlemek için teknikler hakkında daha fazla bilgi için [kodunuzu .NET Framework'den .NET Core'a](/dotnet/core/porting)kadar port'a bakın.

ASP.NET Core ASP.NET yeniden tasarlanmış bir sürümüdür ve başlangıçta açık görünmeyebilir bazı değişiklikler vardır. Ana değişiklikler şunlardır:

- Senkronizasyon bağlamı yok, bu da `HttpContext.Current` `Thread.CurrentPrincipal`başka statik erişimci olmadığı anlamına gelir
- Gölge kopyalama yok
- İstek sırası yok

ASP.NET Core'daki birçok işlem, G/Ç'ye bağlı görevlerin daha kolay yüklenmesine olanak tanıyan eşzamanlı işlemlerdir. İş parçacığı havuzu kaynaklarını hızlı `Task.Wait()` `Task.GetResult()`bir şekilde tüketebilen kullanarak veya engelleyerek asla engellememek önemlidir.

## <a name="migration-conclusion"></a>Göç sonucu

Bu noktada, bir Web Forms projesini Blazor'a taşımak için gerekenlere pek çok örnek gördünüz. Tam bir örnek için, [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) projesine bakın.

>[!div class="step-by-step"]
>[Önceki](security-authentication-authorization.md)
