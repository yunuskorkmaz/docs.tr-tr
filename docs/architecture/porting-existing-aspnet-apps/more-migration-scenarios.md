---
title: Daha fazla geçiş senaryosu
description: Bu bölümde, .NET Framework uygulamalarını .NET Core/.NET 5 ' e yükseltmeye yönelik ek geçiş senaryoları ve teknikleri açıklanmaktadır.
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: 672ad1da4611197e7af63d1408836c4c1a26567a
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122787"
---
# <a name="more-migration-scenarios"></a>Daha fazla geçiş senaryosu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu bölümde birçok farklı ASP.NET uygulama senaryosu açıklanmakta ve bunların her birinin çözümüne yönelik özel teknikler sunulmaktadır. Bu bölümü, uygulamanız için geçerli olan senaryoları belirlemek ve uygulamanız ve barındırma ortamı için hangi tekniklerin çalıştığını değerlendirmek için kullanabilirsiniz.

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a>ASP.NET Core MVC 'ye ASP.NET MVC 5 ve WebApi 2 geçirin

ASP.NET MVC 5 ve Web API 2 uygulamalarında yaygın bir senaryo, her iki ürünün de aynı uygulamaya yüklenmiydi. Bu, birçok ekip tarafından kullanılan desteklenen ve görece yaygın bir yaklaşımdır. ancak iki ürün farklı soyutlama kullandığından, bazı gereksiz çabaların olması gerekir. Örneğin, ASP.NET MVC için yolların ayarlanması, ve gibi yöntemleri kullanılarak yapılır `RouteCollection` `MapMvcAttributeRoutes()` `MapRoute()` . Ancak ASP.NET Web API 2 yönlendirmesi ile ve `HttpConfiguration` gibi yöntemlerle yönetilir `MapHttpAttributeRoutes()` `MapHttpRoute()` .

`eShopLegacyMVC`Uygulama hem ASP.NET MVC hem de Web API 'sini içerir ve `App_Start` her ikisinde de yolların kurulması için içindeki yöntemleri içerir. Ayrıca, yapılandırmak üzere iki benzer iş kümesi gerektiren Autofac kullanarak bağımlılık ekleme işlemini destekler:

```csharp
protected IContainer RegisterContainer()
{
    var builder = new ContainerBuilder();

    var thisAssembly = Assembly.GetExecutingAssembly();
    builder.RegisterControllers(thisAssembly);      // MVC controllers
    builder.RegisterApiControllers(thisAssembly);   // Web API controllers

    var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
    builder.RegisterModule(new ApplicationModule(mockData));

    var container = builder.Build();

    // set mvc resolver
    DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

    // set webapi resolver
    var resolver = new AutofacWebApiDependencyResolver(container);
    GlobalConfiguration.Configuration.DependencyResolver = resolver;

    return container;
}
```

Bu uygulamaları ASP.NET Core kullanacak şekilde yükseltirken, bu yinelenen çaba ve bazen eşlik eden karışıklık ortadan kalkar. ASP.NET Core MVC, yönlendirme, filtreler ve daha fazlası için tek bir kural kümesi içeren birleştirilmiş bir çerçevedir. Bağımlılık ekleme, .NET Core 'un kendisi içinde yerleşiktir. Bu `Startup.cs` , örnekteki uygulamada gösterildiği gibi ' de yapılandırılabilir `eShopPorted` .

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a>HttpResponseMessage 'ı ASP.NET Core geçirin

Bazı ASP.NET Web API uygulamaları, döndüren eylem yöntemlerine sahip olabilir `HttpResponseMessage` . Bu tür ASP.NET Core yok. `Delete` `ResponseMessage` Temel üzerinde yardımcı yöntemi kullanılarak bir eylem yönteminde kullanım örneği aşağıda verilmiştir `ApiController` :

```csharp
// DELETE api/<controller>/5
[HttpDelete]
public IHttpActionResult Delete(int id)
{
    var brandToDelete = _service.GetCatalogBrands().FirstOrDefault(x => x.Id == id);
    if (brandToDelete == null)
    {
        return ResponseMessage(new HttpResponseMessage(HttpStatusCode.NotFound));
    }

    // demo only - don't actually delete
    return ResponseMessage(new HttpResponseMessage(HttpStatusCode.OK));
}
```

ASP.NET Core MVC 'de, tüm ortak HTTP yanıt durum kodları için kullanılabilen yardımcı yöntemler bulunur, bu nedenle yukarıdaki yöntem aşağıdaki koda alınır:

```csharp
[HttpDelete("{id}")]
public IActionResult Delete(int id)
{
    var brandToDelete = _service.GetCatalogBrands().FirstOrDefault(x => x.Id == id);
    if (brandToDelete == null)
    {
        return NotFound();
    }

    // demo only - don't actually delete
    return Ok();
}
```

Hiçbir yardımcı olmadığı için bir özel durum kodu döndürmediğiniz fark ederseniz, `return StatusCode(int statusCode)` istediğiniz herhangi bir sayısal kodu döndürmek için her zaman kullanabilirsiniz.

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a>ASP.NET Web API 'sindeki içerik anlaşmasını ASP.NET Core 'ye geçirme

ASP.NET Web API 2, [içerik anlaşmasını](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) yerel olarak destekler. Örnek uygulama, `BrandsController` SONUÇLARıNı XML veya JSON olarak listeleyerek bu desteği gösteren bir içerir. Bu, isteğin `Accept` üstbilgisine ve veya içerdiğinde değişikliklere dayalıdır `application/xml` `application/json` .

ASP.NET MVC 5 uygulamalarında yerleşik olarak bulunan içerik anlaşması desteği yoktur.

İçerik anlaşması, daha esnek olduğu ve API 'nin daha fazla sayıda istemciye uygun hale gelmesini sağlayan belirli bir kodlama türünü döndürmek tercih edilir. Şu anda belirli bir biçim döndüren eylem yöntemleriniz varsa, ASP.NET Core kod bağlantı noktası oluştururken içerik anlaşmasını destekleyen bir sonuç türü döndürecek şekilde onları değiştirmeyi göz önünde bulundurmanız gerekir.

Aşağıdaki kod, istemci üst bilgi içeriğinden bağımsız olarak JSON biçimindeki verileri döndürür `Accept` :

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

ASP.NET Core MVC, uygun bir [dönüş türü](/aspnet/core/web-api/action-return-types) kullanıldığından, [içerik anlaşmasını yerel olarak destekler](/aspnet/core/web-api/advanced/formatting). İçerik anlaşması, denetleyici Yardımcısı yöntemleri tarafından döndürülen durum koduna özgü eylem sonuçları tarafından döndürülen [ObjectResult] tarafından uygulanır. ASP.NET Core MVC 'de uygulanan ve içerik anlaşmasını kullanan önceki eylem yöntemi şöyle olacaktır:

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

Bu, varsayılan olarak JSON biçimindeki verileri döndürür. [Uygulama uygun biçimlendirici ile yapılandırıldıysa](/aspnet/core/web-api/advanced/formatting), XML ve diğer biçimler de kullanılacaktır.

## <a name="custom-model-binding"></a>Özel model bağlama

Çoğu ASP.NET MVC ve Web API uygulaması model bağlamayı kullanır. Varsayılan model bağlama söz dizimi, bu uygulamalar ve ASP.NET Core MVC arasında oldukça sorunsuz bir şekilde geçirilir. Ancak, bazı durumlarda müşteriler belirli model türlerini veya kullanım senaryolarını desteklemek için [özel model ciltleri](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) yazmıştı. ASP.NET MVC ve Web API projelerinde özel model ciltler `IModelBinder` `System.Web.Mvc` , sırasıyla ve ad alanlarında tanımlanan ayrı arabirimleri kullanır `System.Web.Http` . Her iki durumda da, özel bağlayıcı `Bind` bir denetleyiciyi veya eylem bağlamını kabul eden bir yöntemi ve bir model bağlama bağlamını bağımsız değişken olarak sunar.

Özel bağlayıcı oluşturulduktan sonra, uygulamanın uygulamayla kayıtlı olması gerekir. Bu adım, bir `ModelBinderProvider` fabrika görevi gören ve bir istek sırasında model cildi oluşturan başka bir tür oluşturulmasını gerektirir. Şu şekilde, MVC uygulamalarında ciltler eklenebilir `ApplicationStart` :

```csharp
ModelBinderProviders.BinderProviders.Insert(0, new MyCustomBinderProvider()); // MVC
```

Web API uygulamalarında özel ciltçileri öznitelikler kullanılarak başvurulabilir. `ModelBinder`Öznitelik, gösterildiği gibi eylem yöntemi parametrelerine veya parametrenin tür tanımına eklenebilir:

```csharp
// attribute on action method parameter
public HttpResponseMessage([ModelBinder(typeof(MyCustomBinder))] CustomDTO custom)
{
}

// attribute on type
[ModelBinder(typeof(MyCustomBinder))]
public class CustomDTO
{
}
```

Model cildi ASP.NET Web API 'sinde küresel olarak kaydetmek için, uygulamanın başlatılması sırasında sağlayıcının eklenmesi gerekir:

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        var provider = new CustomModelBinderProvider(
            typeof(CustomDTO), new CustomModelBinder());
        config.Services.Insert(typeof(ModelBinderProvider), 0, provider);

        // ...
    }
}
```

[Özel model sağlayıcılarını ASP.NET Core 'e](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)geçirirken, Web API 'si MODELI ASP.NET MVC 5 ' ten ASP.NET Core yaklaşımına daha yakın olur. ASP.NET Core `IModelBinder` arabirimi ve Web API 'si arasındaki temel farklılıklar, ASP.NET Core yönteminin zaman uyumsuz ( `BindModelAsync` ) ve yalnızca `BindingModelContext` Web API 'sinin sürümü gereken iki parametre yerine yalnızca tek bir parametre gerektirmesidir. ASP.NET Core, `[ModelBinder]` tek tek eylem yöntemi parametrelerinde veya bunlarla ilişkili türlerde bir özniteliği kullanabilirsiniz. Ayrıca `ModelBinderProvider` , uygun yerlerde uygulama içinde genel olarak kullanılacak bir de oluşturabilirsiniz. Böyle bir sağlayıcıyı yapılandırmak için içine kod ekleyin `Startup` `ConfigureServices` :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.ModelBinderProviders.Insert(0, new CustomModelBinderProvider());
    });
}
```

## <a name="media-formatters"></a>Medya biçimleri

ASP.NET Web API 'SI, birden çok medya biçimini destekler ve özel medya formatlayıcıları kullanılarak genişletilebilir. Docs, verileri virgülle ayrılmış değer biçiminde göndermek için kullanılabilecek [Örnek BIR CSV medya biçimlendirici](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) tanımlıyor. Web API uygulamanız özel medya biçimleri kullanıyorsa, bunları [özel biçim ASP.NET Core](/aspnet/core/web-api/advanced/custom-formatters)dönüştürmeniz gerekir.

Web API 2 ' de özel bir biçimlendirici oluşturmak için uygun bir temel sınıftan devralmış ve sonra nesneyi kullanarak biçimlendirici Web API işlem hattına eklemiş olursunuz `HttpConfiguration` :

```csharp
public static void ConfigureApis(HttpConfiguration config)
{
    config.Formatters.Add(new ProductCsvFormatter()); 
}
```

ASP.NET Core, işlem benzerdir. ASP.NET Core hem giriş biçimlerini (model bağlama tarafından kullanılır) hem de çıkış formatlarını destekler (yanıtları biçimlendirmek için kullanılır). Belirli bir şekilde çıkış yanıtlarına özel bir biçimlendirici eklemek, uygun bir taban sınıftan devralmayı ve içindeki bir biçimlendirici öğesini ' deki MVC 'ye eklemeyi içerir `Startup` :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.InputFormatters.Insert(0, new CustomInputFormatter());
        options.OutputFormatters.Insert(0, new CustomOutputFormatter());
    });
}
```

[Microsoft. AspNetCore. Mvc. Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) ad alanındaki temel sınıfların tamamen bir listesini bulacaksınız.

Bir Web API biçimlendirici 'dan ASP.NET Core MVC biçimlendirici 'e geçiş adımları şunlardır:

1. Yeni biçimlendirici için uygun bir temel sınıf belirler.
1. Temel sınıfın yeni bir örneğini oluşturun ve gerekli yöntemleri uygulayın.
1. Web API biçimlendirici içindeki işlevselliği yeni uygulamaya kopyalayın.
1. `ConfigureServices`Yeni biçimlendirici kullanmak için ASP.NET Core uygulamanın YÖNTEMINDE MVC 'yi yapılandırın.

## <a name="custom-filters"></a>Özel filtreler

Filtreler, istek işleme ardışık düzeninde belirli aşamaların önce ve/veya sonrasında kodu yürütmek için ASP.NET Core uygulamalarında kullanılır. ASP.NET MVC ve Web API 'SI de aynı şekilde filtreler kullanır, ancak ayrıntılar farklılık gösterir. Örneğin, [ASP.NET MVC dört tür filtreyi destekler](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters). ASP.NET Web API 2 benzer filtreleri destekler ve [filtreleri geçersiz kılmak](/dotnet/api/system.web.mvc.filters.ioverridefilter)IÇIN hem MVC hem de Web API 'si dahil öznitelikleri içerir.

ASP.NET MVC ve Web API uygulamalarında kullanılan en yaygın filtre, bir [IActionFilter arabirimi](/dotnet/api/system.web.mvc.iactionfilter)tarafından tanımlanan eylem filtresidir. Bu arabirim `OnActionExecuting` `OnActionExecuted` , her yöntemde belirtildiği gibi bir eylem yürütmeden önce ve/veya sonrasında kodu yürütmek için kullanılan () ve After () için yöntemler sağlar.

ASP.NET Core filtreleri desteklemeye devam eder ve MVC ve Web API 'sinin birleşme sürümü, uygulamalarına yalnızca bir yaklaşım olduğu anlamına gelir. Docs, ASP.NET Core MVC ' de yerleşik olarak bulunan [ve beş (5) tür filtrelerin ayrıntılı kapsamını içerir](/aspnet/core/mvc/controllers/filters#filter-types). ASP.NET MVC ve ASP.NET Web API 'sinde desteklenen tüm filtre türevleri ASP.NET Core ilişkili sürümlere sahiptir, bu nedenle geçiş genellikle uygun arabirimi ve/veya temel sınıfı tanımlamayı ve kodun üzerine geçirilmesini bir şekilde yapılır.

Zaman uyumlu arayüzlere ek olarak ASP.NET Core, ayrıca `IAsyncActionFilter` , kodu gösterildiği gibi, eylemden önce ve sonra çalıştırılacak şekilde kullanılabilecek tek bir zaman uyumsuz yöntem sağlayan zaman uyumsuz arabirimler de sağlar.

```csharp
public class SampleAsyncActionFilter : IAsyncActionFilter
{
    public async Task OnActionExecutionAsync(
        ActionExecutingContext context,
        ActionExecutionDelegate next)
    {
        // Do something before the action executes.

        // next() calls the action method.
        var resultContext = await next();
        // resultContext.Result is set.
        // Do something after the action executes.
    }
}
```

Zaman uyumsuz kodu (veya zaman uyumsuz olması gereken kodu) geçirirken takımlar, bu amaçla sağlanmış olan yerleşik zaman uyumsuz türleri kullanmayı göz önünde bulundurmalıdır.

Çoğu ASP.NET MVC ve Web API uygulaması çok sayıda özel filtre kullanmaz. ASP.NET Core MVC 'deki filtrelere yönelik yaklaşım, ASP.NET MVC ve Web API 'SI filtreleriyle yakından hizalandığından, özel filtrelerin geçirilmesi genellikle oldukça basittir. ASP.NET Core docs ' deki filtrelerle ilgili ayrıntılı belgeleri okuduğunuzdan emin olun ve bunları iyi bir şekilde öğrendiğinizden emin olduktan sonra, eski sistemden yeni sistem filtrelerine yönelik mantığı bağlantı noktası alın.

## <a name="route-constraints"></a>Yol kısıtlamaları

ASP.NET Core, isteklerin bir isteği yönlendirmek için düzgün yönlendirildiğinden emin olmak için yol kısıtlamalarını kullanır. [ASP.NET Core bu amaç için çok sayıda farklı yol kısıtlaması destekler]/ASPNET/Core/temelde Mentals/Routing # Route-Constraint-Reference). Yol kısıtlamaları yol tablosuna uygulanabilir, ancak ASP.NET MVC 5 ve/veya [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) ile oluşturulan çoğu uygulama, öznitelik yollarına uygulanan satır içi yol kısıtlamalarını kullanır. Satır içi yol kısıtlamaları şöyle bir biçim kullanır:

```csharp
[Route("/customer/{id:int}")]
```

`:int` `id` Route parametresinden sonra değeri, türü ile eşleşecek şekilde kısıtlar `int` . Yol kısıtlamalarını kullanmanın bir avantajı, parametrelerin yalnızca kendi türlerine göre farklılık gösterdiği iki farklı yolun mevcut olmasına izin vermelerinin olmasıdır. Bu, yalnızca parametre türüne dayalı yolların [yöntem aşırı](/dotnet/standard/design-guidelines/member-overloading) yüklenmesine izin verir.

Yol kısıtlamaları kümesi, söz dizimi ve kullanımları, üç yaklaşım arasında çok benzerdir. Özel yol kısıtlamaları müşteri uygulamalarında oldukça nadir bir durumdur. Uygulamanız özel bir yol kısıtlaması kullanıyorsa ve ASP.NET Core bağlantı noktası olması gerekiyorsa docs, [ASP.NET Core içinde özel yol kısıtlamaları oluşturmayı](/aspnet/core/fundamentals/routing#custom-route-constraints)gösteren örnekler içerir. Temel olarak tüm gerekli olan `IRouteConstraint` ve `Match` yöntemi uygulamak ve ardından uygulama için yönlendirmeyi yapılandırırken özel kısıtlamayı eklemektir:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers();

    services.AddRouting(options =>
    {
        options.ConstraintMap.Add("customName", typeof(MyCustomConstraint));
    });
}
```

Bu, özel kısıtlamaların ASP.NET Web API 'sinde kullanılanlara çok benzer ve bu, `IHttpRouteConstraint` bir çözümleyici ve için bir çağrı kullanarak onu kullanır ve yapılandırır `HttpConfiguration.MapHttpAttributeRoutes` :

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        var constraintResolver = new DefaultInlineConstraintResolver();
        constraintResolver.ConstraintMap.Add("nonzero", typeof(CustomConstraint));

        config.MapHttpAttributeRoutes(constraintResolver);
    }
}
```

ASP.NET MVC 5, `IRouteConstraint` arabirim adı için kullanarak ve yol yapılandırmasının bir parçası olarak kısıtlamayı yapılandırarak çok benzer bir yaklaşım izler:

```csharp
public class RouteConfig
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
 
        var constraintsResolver = new DefaultInlineConstraintResolver();
        constraintsResolver.ConstraintMap.Add("values", typeof(ValuesConstraint));
        routes.MapMvcAttributeRoutes(constraintsResolver);
    }
}
```

Yol kısıtlama kullanımının ve ASP.NET Core özel yol kısıtlamalarının geçirilmesi genellikle çok basittir.

## <a name="custom-route-handlers"></a>Özel yol işleyicileri

ASP.NET MVC 5 ' in başka bir oldukça gelişmiş özelliği yol işleyicileridir. Özel yol işleyicileri `IRouteHandler` , `IHttpHandler` bir verme isteği için döndüren tek bir yöntemi içeren uygular. , `IHttpHandler` Sırasıyla bir `IsReusable` özelliği ve tek bir `ProcessRequest` yöntemi sunar. ASP.NET MVC 5 ' te, özel işleyicinizi kullanmak için yol tablosunda belirli bir yolu yapılandırabilirsiniz:

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
 
    routes.Add(new Route("custom", new CustomRouteHandler()));
}
```

Özel yol işleyicilerini ASP.NET MVC 5 ' ten ASP.NET Core geçirmek için bir filtre (eylem filtresi gibi) veya özel bir filtre kullanabilirsiniz [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter) . Filtre yaklaşımı nispeten basittir ve `ConfigureServices` *Başlangıç. cs*' ye MVC eklendiğinde genel bir filtre olarak eklenebilir.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(CustomActionFilter));
    });
}
```

`IRouter`Seçeneği, arabirimin ve yöntemlerinin uygulanması gerekir `RouteAsync` `GetVirtualPath` . Özel yönlendirici, `Configure` *Başlangıç. cs* içindeki yönteminde istek ardışık düzenine eklenir.

```csharp
public void Configure(IApplicationBuilder app)
{
    // ...
    app.UseMvc(routes =>
    {
        routes.Routes.Add(new CustomRouter(routes.DefaultHandler));
    });
}
```

ASP.NET Web API 'sinde, Bu işleyiciler *yol işleyicileri* yerine [özel ileti işleyicileri](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)olarak adlandırılır. İleti işleyicileri öğesinden türetilmelidir `DelegatingHandler` ve metodunu geçersiz kılmalıdır `SendAsync` . İleti işleyicileri, ASP.NET Core ara yazılım ve istek işlem hattına çok benzeyen bir şekilde işlem hattı oluşturmak için birlikte zincirlenebilir.

ASP.NET Core `DelegatingHandler` tür veya ayrı ileti işleyici işlem hattı yok. Bunun yerine, bu tür işleyiciler genel filtreler, özel `IRouter` örnekler (yukarıya bakın) veya özel ara yazılım kullanılarak geçirilmelidir. ASP.NET Core MVC filtreleri ve `IRouter` türleri, denetleyiciler ve eylemler gıbı MVC yapılarına yerleşik erişim sahibi olmanın avantajlarından yararlanır. ara yazılım, MVC 'ye yönelik bir özellikleri olmayan daha düşük bir yaklaşımda bulunur. Bu da daha esnek hale gelir, ancak MVC bileşenlerine erişmeniz gerekiyorsa daha fazla çaba gerektirir.

## <a name="cors-support"></a>CORS desteği

CORS veya çıkış noktaları arası kaynak paylaşımı, sunucuların, sundukları yanıtlardan kaynaklanmayan istekleri kabul etmesine olanak tanıyan bir W3C standardıdır. ASP.NET MVC 5 ve ASP.NET Web API 2, CORS 'yi farklı yollarla destekler. ASP.NET MVC 5 ' te CORS desteğini etkinleştirmenin en kolay yolu aşağıdakine benzer bir eylem filtresine sahiptir:

```csharp
public class AllowCrossSiteAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext filterContext)
    {
        filterContext.RequestContext.HttpContext.Response.AddHeader(
            "Access-Control-Allow-Origin", "example.com");
        base.OnActionExecuting(filterContext);
    }
}
```

ASP.NET Web API 'SI de bu tür bir filtre kullanabilir, ancak [CORS 'yi etkinleştirmek için yerleşik desteğe](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) sahiptir:

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        config.EnableCors();
        // ...
    }
}
```

Bu eklendikten sonra özniteliği kullanarak izin verilen kaynakları, üstbilgileri ve yöntemleri `EnableCors` aşağıdaki gibi yapılandırabilirsiniz:

```csharp
[EnableCors(origins: "https://dot.net", headers: "*", methods: "*")]
public class TestController : ApiController
{
    // Controller methods not shown...
}
```

CORS uygulamanızı ASP.NET MVC 5 veya ASP.NET Web API 2 ' den geçirmeden önce [CORS 'nin nasıl çalıştığını](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) gözden geçirdiğinizden emin olun ve CORS 'nin geçerli sisteminizde beklendiği gibi çalıştığını gösteren bazı otomatikleştirilmiş testler oluşturun.

ASP.NET Core, CORS 'yi etkinleştirmek için üç yerleşik yol vardır:

- İçinde [ilke aracılığıyla yapılandırılır](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware)`ConfigureServices`
- [Uç nokta yönlendirme](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing) ile etkinleştirildi
- [ `EnableCors` Özniteliği](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes) ile etkinleştirildi

Bu yaklaşımlardan her biri, yukarıdaki seçeneklerden bağlantılı olan docs 'ta ayrıntılı olarak ele alınmıştır. Seçtiğiniz bu, büyük ölçüde mevcut uygulamanızın CORS 'yi nasıl desteklediğine bağlıdır. Uygulama öznitelikleri kullanıyorsa, muhtemelen özniteliğini en kolay şekilde kullanmaya geçiş yapabilirsiniz `EnableCors` . Uygulamanız filtreler kullanıyorsa, bu yaklaşımı kullanmaya devam edebilirsiniz (ASP.NET Core) veya bu yaklaşım için kullanılan tipik yaklaşım olmasa da, öznitelikleri veya ilkeleri kullanmak için geçiş yapabilirsiniz. Uç nokta yönlendirme, ASP.NET Core 3 ile sunulan görece yeni bir özelliktir ve bu nedenle ASP.NET MVC 5 veya ASP.NET Web API 2 uygulamalarında kapalı bir analog yoktur.

## <a name="custom-areas"></a>Özel bölgeler

Birçok ASP.NET MVC uygulaması, projeyi düzenlemek için alan kullanır. Bölgeler genellikle bir *bölgeler* klasöründeki projenin kökünde bulunur ve uygulama başladığında, genellikle içinde bir kayıt olmalıdır `Application_Start()` .

```csharp
AreaRegistration.RegisterAllAreas();
```

Başlangıçtaki tüm alanları kaydetmenin alternatifi, `RouteArea` tek tek denetleyicilerde özniteliğini kullanmaktır:

```csharp
[RouteArea("Admin")]
public class SomeController : Controller
```

Alan kullanırken, farklı alanlardaki eylemlere bağlantılar oluşturmak için ek bağımsız değişkenler HTML yardımcı yöntemlerine geçirilir:

```cshtml
@Html.ActionLink("News", "Index", "News", new { area = "News" }, null)
```

ASP.NET Web API 'SI uygulamaları, denetleyicileri projedeki herhangi bir klasöre yerleştirilediklerinden, genellikle alanları açık bir şekilde kullanmaz. Takımlar, API denetleyicilerini düzenlemek gibi herhangi bir klasör yapısını kullanabilir.

ASP.NET Core MVC 'de [alan](/aspnet/core/mvc/controllers/areas) desteklenir. Kullanılan yaklaşım, ASP.NET MVC 5 içindeki alanların kullanımıyla neredeyse aynıdır. Alan kullanarak kod geçişi yapan geliştiriciler aşağıdaki farklılıkları göz önünde bulundurmanız gerekir:

- `AreaRegistration.RegisterAllAreas` ASP.NET Core MVC 'de kullanılmaz
- Bölgeler, özniteliği kullanılarak uygulanır `[Area("name")]` ( `RouteArea` ASP.NET MVC 5 içinde değil)
- İsterseniz, yol tablosu şablonlarına (veya öznitelik yönlendirme kullanabilirler) alan eklenebilir.

ASP.NET Core MVC 'de yol tablosuna alan desteği eklemek için, `Configure` *Başlangıç. cs*' ye şunu ekleyin:

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "MyArea",
        pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");

    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Alanları, yol tanımındaki anahtar sözcüğü kullanılarak öznitelik yönlendirme ile de kullanılabilir `{area}` (yol şablonlarıyla kullanılabilecek birkaç [ayrılmış yönlendirme adlarından](/aspnet/core/mvc/controllers/routing#reserved-routing-names) biridir).

Etiket Yardımcıları `asp-area` , Razor görünümlerinde ve sayfalarında bağlantı oluşturmak için kullanılabilecek özniteliği olan bölgeleri destekler:

```razor
<ul>
    <li>
        <a asp-area="Products" asp-controller="Home" asp-action="About">
            Products/Home/About
        </a>
    </li>
    <li>
        <a asp-area="Services" asp-controller="Home" asp-action="About">
            Services About
        </a>
    </li>
    <li>
        <a asp-area="" asp-controller="Home" asp-action="About">
            /Home/About
        </a>
    </li>
</ul>
```

Razor Pages geçiş yapıyorsanız, *Sayfalar* klasörünüzde bir *alan* klasörü kullanmanız gerekir. Daha fazla bilgi için bkz. [Razor Pages alanlara](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages)bakın.

Yukarıdaki kılavuza ek olarak takımlar ASP.NET Core içindeki yönlendirmenin, geçiş planlama sürecinin bir parçası olarak [alanlarla nasıl çalıştığını](/aspnet/core/mvc/controllers/routing#areas) incelemelidir.

## <a name="integration-tests-for-aspnet-mvc-and-aspnet-web-api"></a>ASP.NET MVC ve ASP.NET Web API 'SI için tümleştirme testleri

Tümleştirme testleri, bir uygulamanın çeşitli farklı bölümlerinin doğru şekilde çalıştığını doğrulayan otomatikleştirilmiş testlerdir. Genellikle uygulamayı bir yerel IIS veya IIS Express gibi gerçek bir Web sunucusuna dağıtmaya dahil olan ASP.NET MVC ve ASP.NET Web API 'SI için tümleştirme testleri yazma ve ardından HTTP istemcisi kullanarak bu barındırılan uygulamaya istek yapma. Bu testlerin bazıları [Selenium](https://www.selenium.dev/)gibi tarayıcı otomasyon araçları kullanılarak istemci tarafı Kullanıcı arabirimiyle etkileşime geçebilir, ancak bunlar genellikle tümleştirme testleri yerine *UI testleri* olarak adlandırılır.

Geçirilen uygulamanız orijinal sürümü ile aynı davranışı paylaşıyorsa, takımın tümleştirme testlerini gerçekleştirmek için kullandığı mevcut teknolojiden (ve UI testlerinde), daha önce olduğu gibi çalışmaya devam etmesi gerekir. Bu testler genellikle test ettikleri uygulamayı barındırmak için kullanılan temel teknolojiden farklıdır ve yalnızca HTTP istekleri aracılığıyla etkileşime geçer. Her şeyin daha zor olduğu durumlarda, testlerin her testten önce bilinen iyi bir duruma getirmek için uygulamayla etkileşime girmesine neden olur. Yapılandırma ve başlatma ASP.NET Core ASP.NET MVC veya ASP.NET Web API 'siyle karşılaştırıldığında önemli ölçüde farklı olduğundan, bu durum biraz geçiş çabasında bulunabilir.

Ekipler, [ASP.NET Core yerleşik tümleştirme test](/aspnet/core/test/integration-tests) desteğini kullanmak üzere tümleştirme testlerini geçirmeyi kesinlikle düşünmelidir. ASP.NET Core, uygulamalar, kullanılarak yapılandırılan bir öğesine dağıtarak test edilebilir `TestHost` `WebApplicationFactory` . Uygulamayı test etmek için barındırmak için gereken çok sayıda kurulum vardır, ancak bu durumda, bireysel tümleştirme testlerinin oluşturulması çok basittir.

ASP.NET Core tümleştirme testi desteğinin en iyi özelliklerinden biri, uygulamanın bellekte barındırılmasından biridir. Uygulamayı barındırmak için gerçek bir Web sunucusu yapılandırmaya gerek yoktur. Tarayıcı Otomasyonu aracı kullanmanız gerekmez (yalnızca ASP.NET Core test ediyorsanız, istemci tarafı davranışını test eteceğiz). Güvenlik Duvarı sorunları veya işlem başlatma/durdurma sorunları gibi otomatikleştirilmiş tümleştirme testleri için gerçek bir Web sunucusu kullanılmaya çalışırken karşılaşılabilecek birçok sorun, bu yaklaşımla ortadan kaldırılır. İsteklerin tümü ağ gereksinimi olmadan bellekte yapıldığından, testler aynı zamanda ayrı bir Web sunucusu ayarlaması ve ağ üzerinden iletişim kurması gereken testlerden çok daha hızlı çalışır (aynı makine üzerinde çalışıyor olsa bile).

Aşağıda bir örnek ASP.NET Core tümleştirme testi (bazen alt düzey tümleştirme sınamalarından ayırt etmek için *işlevsel testler* olarak adlandırılır) [Eshoponweb Reference uygulamasından](https://github.com/dotnet-architecture/eShopOnWeb)görebilirsiniz:

```csharp
public class GetByIdEndpoint : IClassFixture<ApiTestFixture>
{
    JsonSerializerOptions _jsonOptions = new JsonSerializerOptions { PropertyNameCaseInsensitive = true };

    public GetByIdEndpoint(ApiTestFixture factory)
    {
        Client = factory.CreateClient();
    }

    public HttpClient Client { get; }

    [Fact]
    public async Task ReturnsItemGivenValidId()
    {
        var response = await Client.GetAsync("api/catalog-items/5");
        response.EnsureSuccessStatusCode();
        var stringResponse = await response.Content.ReadAsStringAsync();
        var model = stringResponse.FromJson<GetByIdCatalogItemResponse>();

        Assert.Equal(5, model.CatalogItem.Id);
        Assert.Equal("Roslyn Red Sheet", model.CatalogItem.Name);
    }
}
```

Geçirilmekte olan uygulamanın tümleştirme testi yoksa, geçiş işlemi bir miktar eklemek için harika bir fırsat olabilir. Bu testler, geçirilen uygulamanın takım tarafından beklediği şekilde davrandığını doğrulayabilirler. Bu tür testler bir geçişin başlarında olduğunda, daha sonra geçiş çabalarının uygulamanın daha önce geçirilmiş bölümlerini bozmadığından emin olabilirler. ASP.NET Core ' de tümleştirme testlerini ayarlamaya ve çalıştırmaya ne kadar kolay bir şekilde, bu tür testlerin ayarlanması için harcanan yatırımın dönüşü genellikle oldukça yüksektir.

## <a name="wcf-client-configuration"></a>WCF istemci yapılandırması

Uygulamanız Şu anda bir istemci olarak WCF hizmetlerini kullanıyorsa, bu senaryo desteklenir. Ancak, yeni *appsettings.js* dosyasını kullanmak için *web.config* [yapılandırmanızı geçirmeniz](/aspnet/core/migration/configuration) gerekecektir. Diğer bir seçenek de, siz oluşturduğunuz zaman, istemcilerinize programlı olarak gerekli yapılandırma eklemektir. Örnek:

```csharp
var wcfClient = new OrderServiceClient(
    new BasicHttpBinding(BasicHttpSecurityMode.None),
    new EndpointAddress("http://localhost:5050/OrderService.svc"));
```

Kuruluşunuzun, uygulamanızın kullandığı WCF kullanılarak oluşturulmuş kapsamlı hizmetleri varsa, bunları gRPC kullanmaya geçirmeyi göz önünde bulundurun. GRPC hakkında daha fazla bilgi için, neden geçiş yapmak isteyebileceğiniz ve ayrıntılı bir geçiş kılavuzu için bkz. [WCF geliştiricileri Için GRPC](/dotnet/architecture/grpc-for-wcf-developers/) eKitap.

## <a name="references"></a>Başvurular

- [ASP.NET Web API 'SI Içerik anlaşması](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [ASP.NET Core Web API 'sindeki yanıt verilerini biçimlendirme](/aspnet/core/web-api/advanced/formatting)
- [ASP.NET Web API 'sinde özel model ciltleri](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)
- [ASP.NET Core özel model ciltleri](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)
- [ASP.NET Web API 2 ' de medya biçimleri](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)\
- [ASP.NET Core Web API 'sindeki özel formatıcılar](/aspnet/core/web-api/advanced/custom-formatters)
- [ASP.NET Core filtreler](/aspnet/core/mvc/controllers/filters)
- [ASP.NET Web API 2 ' de yol kısıtlamaları](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints)
- [ASP.NET MVC 5 ' teki yol kısıtlamaları](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/#route-constraints)
- [ASP.NET Core Route kısıtlama başvurusu](/aspnet/core/fundamentals/routing#route-constraint-reference)
- [ASP.NET Web API 2 ' de özel ileti işleyicileri](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)
- [MVC 5 ve Web API 2 ' de basit CORS denetimi](https://stackoverflow.com/questions/6290053/setting-access-control-allow-origin-in-asp-net-mvc-simplest-possible-method)
- [Web API 'de çapraz kaynak Isteklerini etkinleştirme](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)
- [ASP.NET Core 'de çıkış noktaları arası Istekleri (CORS) etkinleştirme](/aspnet/core/security/cors)
- [ASP.NET Core bölgeler](/aspnet/core/mvc/controllers/areas)
- [ASP.NET Core tümleştirme testleri](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
>[Önceki](example-migration-eshop.md) 
> [Sonraki](deployment-scenarios.md)
