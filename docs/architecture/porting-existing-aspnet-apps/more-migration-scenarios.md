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
# <a name="more-migration-scenarios"></a><span data-ttu-id="4c032-103">Daha fazla geçiş senaryosu</span><span class="sxs-lookup"><span data-stu-id="4c032-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="4c032-104">Bu bölümde birçok farklı ASP.NET uygulama senaryosu açıklanmakta ve bunların her birinin çözümüne yönelik özel teknikler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c032-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="4c032-105">Bu bölümü, uygulamanız için geçerli olan senaryoları belirlemek ve uygulamanız ve barındırma ortamı için hangi tekniklerin çalıştığını değerlendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c032-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="4c032-106">ASP.NET Core MVC 'ye ASP.NET MVC 5 ve WebApi 2 geçirin</span><span class="sxs-lookup"><span data-stu-id="4c032-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="4c032-107">ASP.NET MVC 5 ve Web API 2 uygulamalarında yaygın bir senaryo, her iki ürünün de aynı uygulamaya yüklenmiydi.</span><span class="sxs-lookup"><span data-stu-id="4c032-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="4c032-108">Bu, birçok ekip tarafından kullanılan desteklenen ve görece yaygın bir yaklaşımdır. ancak iki ürün farklı soyutlama kullandığından, bazı gereksiz çabaların olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c032-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="4c032-109">Örneğin, ASP.NET MVC için yolların ayarlanması, ve gibi yöntemleri kullanılarak yapılır `RouteCollection` `MapMvcAttributeRoutes()` `MapRoute()` .</span><span class="sxs-lookup"><span data-stu-id="4c032-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="4c032-110">Ancak ASP.NET Web API 2 yönlendirmesi ile ve `HttpConfiguration` gibi yöntemlerle yönetilir `MapHttpAttributeRoutes()` `MapHttpRoute()` .</span><span class="sxs-lookup"><span data-stu-id="4c032-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="4c032-111">`eShopLegacyMVC`Uygulama hem ASP.NET MVC hem de Web API 'sini içerir ve `App_Start` her ikisinde de yolların kurulması için içindeki yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4c032-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="4c032-112">Ayrıca, yapılandırmak üzere iki benzer iş kümesi gerektiren Autofac kullanarak bağımlılık ekleme işlemini destekler:</span><span class="sxs-lookup"><span data-stu-id="4c032-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="4c032-113">Bu uygulamaları ASP.NET Core kullanacak şekilde yükseltirken, bu yinelenen çaba ve bazen eşlik eden karışıklık ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="4c032-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="4c032-114">ASP.NET Core MVC, yönlendirme, filtreler ve daha fazlası için tek bir kural kümesi içeren birleştirilmiş bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="4c032-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="4c032-115">Bağımlılık ekleme, .NET Core 'un kendisi içinde yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="4c032-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="4c032-116">Bu `Startup.cs` , örnekteki uygulamada gösterildiği gibi ' de yapılandırılabilir `eShopPorted` .</span><span class="sxs-lookup"><span data-stu-id="4c032-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="4c032-117">HttpResponseMessage 'ı ASP.NET Core geçirin</span><span class="sxs-lookup"><span data-stu-id="4c032-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="4c032-118">Bazı ASP.NET Web API uygulamaları, döndüren eylem yöntemlerine sahip olabilir `HttpResponseMessage` .</span><span class="sxs-lookup"><span data-stu-id="4c032-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="4c032-119">Bu tür ASP.NET Core yok.</span><span class="sxs-lookup"><span data-stu-id="4c032-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="4c032-120">`Delete` `ResponseMessage` Temel üzerinde yardımcı yöntemi kullanılarak bir eylem yönteminde kullanım örneği aşağıda verilmiştir `ApiController` :</span><span class="sxs-lookup"><span data-stu-id="4c032-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="4c032-121">ASP.NET Core MVC 'de, tüm ortak HTTP yanıt durum kodları için kullanılabilen yardımcı yöntemler bulunur, bu nedenle yukarıdaki yöntem aşağıdaki koda alınır:</span><span class="sxs-lookup"><span data-stu-id="4c032-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="4c032-122">Hiçbir yardımcı olmadığı için bir özel durum kodu döndürmediğiniz fark ederseniz, `return StatusCode(int statusCode)` istediğiniz herhangi bir sayısal kodu döndürmek için her zaman kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c032-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="4c032-123">ASP.NET Web API 'sindeki içerik anlaşmasını ASP.NET Core 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="4c032-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="4c032-124">ASP.NET Web API 2, [içerik anlaşmasını](https://docs.microsoft.com/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) yerel olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="4c032-124">ASP.NET Web API 2 supports [content negotiation](https://docs.microsoft.com/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="4c032-125">Örnek uygulama, `BrandsController` SONUÇLARıNı XML veya JSON olarak listeleyerek bu desteği gösteren bir içerir.</span><span class="sxs-lookup"><span data-stu-id="4c032-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="4c032-126">Bu, isteğin `Accept` üstbilgisine ve veya içerdiğinde değişikliklere dayalıdır `application/xml` `application/json` .</span><span class="sxs-lookup"><span data-stu-id="4c032-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="4c032-127">ASP.NET MVC 5 uygulamalarında yerleşik olarak bulunan içerik anlaşması desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="4c032-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="4c032-128">İçerik anlaşması, daha esnek olduğu ve API 'nin daha fazla sayıda istemciye uygun hale gelmesini sağlayan belirli bir kodlama türünü döndürmek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="4c032-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="4c032-129">Şu anda belirli bir biçim döndüren eylem yöntemleriniz varsa, ASP.NET Core kod bağlantı noktası oluştururken içerik anlaşmasını destekleyen bir sonuç türü döndürecek şekilde onları değiştirmeyi göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c032-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="4c032-130">Aşağıdaki kod, istemci üst bilgi içeriğinden bağımsız olarak JSON biçimindeki verileri döndürür `Accept` :</span><span class="sxs-lookup"><span data-stu-id="4c032-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="4c032-131">ASP.NET Core MVC, uygun bir [dönüş türü](https://docs.microsoft.com/aspnet/core/web-api/action-return-types) kullanıldığından, [içerik anlaşmasını yerel olarak destekler](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting).</span><span class="sxs-lookup"><span data-stu-id="4c032-131">[ASP.NET Core MVC supports content negotiation natively](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](https://docs.microsoft.com/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="4c032-132">İçerik anlaşması, denetleyici Yardımcısı yöntemleri tarafından döndürülen durum koduna özgü eylem sonuçları tarafından döndürülen [ObjectResult] tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4c032-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="4c032-133">ASP.NET Core MVC 'de uygulanan ve içerik anlaşmasını kullanan önceki eylem yöntemi şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="4c032-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="4c032-134">Bu, varsayılan olarak JSON biçimindeki verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c032-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="4c032-135">[Uygulama uygun biçimlendirici ile yapılandırıldıysa](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting), XML ve diğer biçimler de kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="4c032-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="references"></a><span data-ttu-id="4c032-136">Başvurular</span><span class="sxs-lookup"><span data-stu-id="4c032-136">References</span></span>

- [<span data-ttu-id="4c032-137">ASP.NET Web API 'SI Içerik anlaşması</span><span class="sxs-lookup"><span data-stu-id="4c032-137">ASP.NET Web API Content Negotiation</span></span>](https://docs.microsoft.com/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="4c032-138">ASP.NET Core Web API 'sindeki yanıt verilerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="4c032-138">Format response data in ASP.NET Core Web API</span></span>](https://docs.microsoft.com/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
><span data-ttu-id="4c032-139">[Önceki](example-migration-eshop.md) 
> [Sonraki](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="4c032-139">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
