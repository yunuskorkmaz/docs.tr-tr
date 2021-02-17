---
title: Daha fazla geçiş senaryosu
description: Bu bölümde, .NET Framework uygulamalarını .NET Core/.NET 5 ' e yükseltmeye yönelik ek geçiş senaryoları ve teknikleri açıklanmaktadır.
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: 9bae7e5c1fa5672c21401809b7d6a256459c6281
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629384"
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

ASP.NET Web API 2, [içerik anlaşmasını](https://docs.microsoft.com/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) yerel olarak destekler. Örnek uygulama, `BrandsController` SONUÇLARıNı XML veya JSON olarak listeleyerek bu desteği gösteren bir içerir. Bu, isteğin `Accept` üstbilgisine ve veya içerdiğinde değişikliklere dayalıdır `application/xml` `application/json` .

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

ASP.NET Core MVC, uygun bir [dönüş türü](https://docs.microsoft.com/aspnet/core/web-api/action-return-types) kullanıldığından, [içerik anlaşmasını yerel olarak destekler](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting). İçerik anlaşması, denetleyici Yardımcısı yöntemleri tarafından döndürülen durum koduna özgü eylem sonuçları tarafından döndürülen [ObjectResult] tarafından uygulanır. ASP.NET Core MVC 'de uygulanan ve içerik anlaşmasını kullanan önceki eylem yöntemi şöyle olacaktır:

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

Bu, varsayılan olarak JSON biçimindeki verileri döndürür. [Uygulama uygun biçimlendirici ile yapılandırıldıysa](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting), XML ve diğer biçimler de kullanılacaktır.

## <a name="references"></a>Başvurular

- [ASP.NET Web API 'SI Içerik anlaşması](https://docs.microsoft.com/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [ASP.NET Core Web API 'sindeki yanıt verilerini biçimlendirme](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
>[Önceki](example-migration-eshop.md) 
> [Sonraki](deployment-scenarios.md)
