---
title: ASP.NET MVC ve ASP.NET Core arasındaki yönlendirme farklılıkları
description: Yönlendirme nasıl tanımlanır ve ASP.NET MVC 'de çalışma zamanında nasıl çalışır? Yönlendirme ASP.NET Core uygulamalarda farklı midir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 82b657b21bbe61b47540bc0182d9674f0480951f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488950"
---
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki yönlendirme farklılıkları

Yönlendirme, gelen tarayıcı isteklerini belirli denetleyici eylemlerine (veya Razor Pages işleyicileriyle) eşleştirmekten sorumludur. Bu bölümde, yönlendirmenin ASP.NET MVC (ve Web API) ile ASP.NET Core (MVC, Razor Pages ve diğer durumlarda) arasında nasıl farklı olduğu ele alınmaktadır.

## <a name="routing-in-aspnet-mvc-and-web-api"></a>ASP.NET MVC ve Web API 'de yönlendirme

ASP.NET MVC, yönlendirmeye iki yaklaşım sunar:

1. Gelen istekleri denetleyici eylemlerle eşleştirmek için kullanılabilen yolların bir koleksiyonu olan yol tablosu.
1. Aynı işlevi gerçekleştiren, ancak genel bir yol tablosu düzenlemesi yerine eylemlerin kendileri dekorasyon olarak elde edilen öznitelik yönlendirme özniteliği.

## <a name="route-table"></a>Yol tablosu

Yol tablosu, uygulama başlatıldığında yapılandırılır. Genellikle, genel yol koleksiyonunu yapılandırmak için bir statik yöntem çağrısı kullanılır, örneğin:

```csharp
public class MvcApplication : System.Web.HttpApplication
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
        routes.MapRoute(
            name: "Default",
            url: "{controller}/{action}/{id}",
            defaults: new { controller = "Home", action = "Index", id = "" },
            constraints: new { id = "\\d+" }
        );
    }

    protected void Application_Start()
    {
        RegisterRoutes(RouteTable.Routes);
    }
}
```

Yukarıdaki kodda yol tablosu, `RouteCollection` ile yeni rotalar eklemek için kullanılan türü tarafından yönetilir `MapRoute` . Yollar, ve denetleyiciler, Eylemler, bölgeler ve diğer yer tutucular için parametreleri içerebilen bir yol dizesi içerir. Bir uygulama standart bir kuralı izliyorsa, bu kural için ek rotalar kullanılarak yapılandırılmış özel durumlarla birlikte eylemlerinin büyük bir kısmının bu tek varsayılan yol tarafından işlenebilmesini sağlayabilirsiniz.

### <a name="attribute-routing-in-aspnet-mvc"></a>ASP.NET MVC 'de öznitelik yönlendirme

Eylemleriyle tanımlanan yolların, bir dış konumda tanımlanan yolların keşfedilmesine ve nedenlerinden daha kolay bir şekilde tanımlanması daha kolay olabilir. Öznitelik yönlendirmeyi kullanarak, tek bir eylem yönteminin rotası bir öznitelikle tanımlanmış olabilir `[Route]` :

```csharp
public class ProductsController
{
    [Route("products")]
    public ActionResult Index()
    {
        return View();
    }

    [Route("products/{id}")]
    public ActionResult Details(int id)
    {
        return View();
    }
}
```

[ASP.NET MVC 5 ' teki öznitelik yönlendirme özelliği](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) , denetleyici düzeyinde eklenebilen (ve bu denetleyici içindeki tüm eylemlere uygulanan) Varsayılanları ve önekleri de destekler. Ayrıntılar için belgelere bakın.

Öznitelik yönlendirmeyi ayarlama, varsayılan yol tablosu yapılandırmasına bir satır eklenmesini gerektirir:

```csharp
routes.MapMvcAttributeRoutes();
```

Öznitelik yönlendirme, hem yerleşik hem de özel yol kısıtlamalarından yararlanabilir ve özniteliği kullanılarak adlandırılmış yollar ve alanların kullanımını destekler `[RouteArea]` . Uygulamanız alan kullanıyorsa, daha fazla satır ekleyerek rota kayıt kodunuzda bu şekilde destek yapılandırmanız gerekir:

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a>ASP.NET Web API 2 ' de öznitelik yönlendirme

[ASP.NET Web API 2 ' de öznitelik yönlendirme](https://docs.microsoft.com/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) , küçük farklılıklar Ile ASP.NET MVC 5 ' teki yönlendirmeye benzerdir. Web API 2 ' yi yapılandırma genellikle uygulama başlatma sırasında çağrılan kendi sınıfında yapılır. Öznitelik Yönlendirme yapılandırması bu sınıfta işlenir:

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        // Attribute routing.
        config.MapHttpAttributeRoutes();

        // Convention-based routing.
        config.Routes.MapHttpRoute(
            name: "DefaultApi",
            routeTemplate: "api/{controller}/{id}",
            defaults: new { id = RouteParameter.Optional }
        );
    }
}
```

Önceki kodda gösterildiği gibi, öznitelik yönlendirme Web API uygulamalarında kural tabanlı yönlendirme ile birleştirilebilir.

Öznitelik yönlendirmeye ek olarak, [ASP.NET Web API 'SI](https://docs.microsoft.com/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) http yöntemine (ÖRNEĞIN, Get veya post), `{action}` bir yoldaki yer tutucuyu (varsa) ve eylemin parametrelerini temel alarak hangi eylemin çağrılacağını seçer. Çoğu durumda, eylemin adı, ilgili HTTP yöntemiyle eşleşen "Get" veya "Post" ile eylem adının sonuna önek olarak kullanılmasından bağımsız olarak, eşleşip eşleşmediğine yardımcı olur. Alternatif olarak, eylemler gibi uygun bir HTTP yöntemi özniteliğiyle birlikte kullanılabilir ve `[HttpGet]` BIR http yöntemiyle ön eki olmayan eylem adlarının kullanılmasına izin verilir.

```csharp
public class ProductsController : ApiController
{
    // matched by name and (lack of) parameters
    public IEnumerable<Product> GetAll() { }
    
    // matched by GET and string parameter
    [HttpGet]
    public IEnumerable<Product> FindProductsByName(string name) { }
}
```

Yukarıdaki denetleyici verildiğinde, eylemle eşleşen bir HTTP GET isteği `localhost:123/products/` `GetAll` . Eylemle eşleşen bir HTTP GET isteği `localhost:123/products?name=ardalis` `FindProductsByName` .

## <a name="routing-in-aspnet-core-31"></a>ASP.NET Core 3,1 ' de yönlendirme

ASP.NET Core, yönlendirme, gelen isteklerin URL 'Leriyle eylemlere veya diğer uç noktalara eşleşen yönlendirme ara yazılımı tarafından işlenir. Denetleyici eylemleri genel olarak yönlendirildi veya Attribute-yönlendirildi olarak atanır. Geleneksel yönlendirme, ASP.NET MVC ve Web API 'sinde kullanılan yol tablosu yaklaşımına benzerdir. Geleneksel, öznitelik veya her ikisini de kullanıyorsanız, uygulamanızı yönlendirme ara yazılımını kullanacak şekilde yapılandırmanız gerekir. Ara yazılımı kullanmak için aşağıdaki kodu yönteminizin içine ekleyin `Startup.Configure` :

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a>Geleneksel yönlendirme

Geleneksel yönlendirme ile, gelen URL 'Leri uygulamadaki *uç noktalarla* eşleştirmek için kullanılacak bir veya daha fazla kural ayarlarsınız. ASP.NET Core, bu uç noktalar ASP.NET MVC veya Web API 'SI gibi denetleyici eylemleri olabilir. Uç noktalar Ayrıca Razor Pages, sistem durumu denetimleri veya SignalR hub 'ları olabilir. Bu yönlendirilebilir özelliklerin tümü uç noktalar kullanılarak benzer bir biçimde yapılandırılır:

```csharp
// in Startup.Configure()
app.UseEndpoints(endpoints =>
{
    endpoints.MapHealthChecks("/healthz").RequireAuthorization();
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

Yukarıdaki kod, `UseRouting` sistem durumu denetimleri, denetleyiciler ve Razor Pages dahil olmak üzere çeşitli uç noktaları yapılandırmak için kullanılır (Buna ek olarak). Denetleyiciler için yukarıdaki yapılandırma, `{controller}/{action}/{id?}` ASP.NET MVC 'nin ilk sürümlerinden beri önerilen oldukça standart bir model olan varsayılan bir yönlendirme kuralı belirtir.

### <a name="attribute-routing"></a>Öznitelik yönlendirme

ASP.NET Core öznitelik yönlendirme, denetleyicilerde yönlendirmeyi yapılandırmak için tercih edilen yaklaşımdır. API 'Ler oluşturuyorsanız, bu `[ApiController]` öznitelik denetleyicilerinize uygulanmalıdır. Diğer şeyler arasında bu öznitelik, bu tür denetleyici sınıflarında eylemler için öznitelik yönlendirmenin kullanılmasını gerektirir.

ASP.NET Core öznitelik yönlendirme ASP.NET MVC ve Web API 'sinde benzer şekilde davranır. Ancak, özniteliği desteklemeye ek olarak `[Route]` , yönlendirme bilgileri de http yöntemi özniteliğinin bir parçası olarak belirtilebilir:

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

Önceki sürümlerde olduğu gibi, yer tutucular içeren bir varsayılan yol belirtebilir ve bunu denetleyici sınıfı düzeyine ya da bir temel sınıfa ekleyebilirsiniz. `[Route]`Tüm bu durumlar için aynı özniteliği kullanırsınız. Örneğin, bir temel API denetleyici sınıfı şöyle görünebilir:

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

Bu özniteliği kullanarak, bu türden devralan sınıflar, denetleyici adı, eylem adı ve isteğe bağlı bir tamsayı parametresine göre URL 'Leri eylemlere yönlendirir `id` .

## <a name="references"></a>Başvurular

- [ASP.NET MVC yönlendirmeye genel bakış](https://docs.microsoft.com/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [ASP.NET MVC 5 içinde öznitelik yönlendirme](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [ASP.NET Web API 2 ' de öznitelik yönlendirme](https://docs.microsoft.com/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [ASP.NET Web API 'sinde yönlendirme ve eylem seçimi](https://docs.microsoft.com/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [ASP.NET Core yönlendirme](https://docs.microsoft.com/aspnet/core/fundamentals/routing)
- [ASP.NET Core MVC 'de denetleyici eylemlerine yönlendirme](https://docs.microsoft.com/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
>[Önceki](configuration-differences.md) 
> [Sonraki](comparing-razor-pages-aspnet-mvc.md)
