---
title: Daha fazla geçiş senaryosu
description: Bu bölümde, .NET Framework uygulamalarını .NET Core/.NET 5 ' e yükseltmeye yönelik ek geçiş senaryoları ve teknikleri açıklanmaktadır.
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: c819fd42cd02da9b643873cda5f2ecf8bc21e559
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231173"
---
# <a name="more-migration-scenarios"></a><span data-ttu-id="3e474-103">Daha fazla geçiş senaryosu</span><span class="sxs-lookup"><span data-stu-id="3e474-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3e474-104">Bu bölümde birçok farklı ASP.NET uygulama senaryosu açıklanmakta ve bunların her birinin çözümüne yönelik özel teknikler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e474-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="3e474-105">Bu bölümü, uygulamanız için geçerli olan senaryoları belirlemek ve uygulamanız ve barındırma ortamı için hangi tekniklerin çalıştığını değerlendirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="3e474-106">ASP.NET Core MVC 'ye ASP.NET MVC 5 ve WebApi 2 geçirin</span><span class="sxs-lookup"><span data-stu-id="3e474-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="3e474-107">ASP.NET MVC 5 ve Web API 2 uygulamalarında yaygın bir senaryo, her iki ürünün de aynı uygulamaya yüklenmiydi.</span><span class="sxs-lookup"><span data-stu-id="3e474-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="3e474-108">Bu, birçok ekip tarafından kullanılan desteklenen ve görece yaygın bir yaklaşımdır. ancak iki ürün farklı soyutlama kullandığından, bazı gereksiz çabaların olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="3e474-109">Örneğin, ASP.NET MVC için yolların ayarlanması, ve gibi yöntemleri kullanılarak yapılır `RouteCollection` `MapMvcAttributeRoutes()` `MapRoute()` .</span><span class="sxs-lookup"><span data-stu-id="3e474-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="3e474-110">Ancak ASP.NET Web API 2 yönlendirmesi ile ve `HttpConfiguration` gibi yöntemlerle yönetilir `MapHttpAttributeRoutes()` `MapHttpRoute()` .</span><span class="sxs-lookup"><span data-stu-id="3e474-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="3e474-111">`eShopLegacyMVC`Uygulama hem ASP.NET MVC hem de Web API 'sini içerir ve `App_Start` her ikisinde de yolların kurulması için içindeki yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e474-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="3e474-112">Ayrıca, yapılandırmak üzere iki benzer iş kümesi gerektiren Autofac kullanarak bağımlılık ekleme işlemini destekler:</span><span class="sxs-lookup"><span data-stu-id="3e474-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="3e474-113">Bu uygulamaları ASP.NET Core kullanacak şekilde yükseltirken, bu yinelenen çaba ve bazen eşlik eden karışıklık ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="3e474-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="3e474-114">ASP.NET Core MVC, yönlendirme, filtreler ve daha fazlası için tek bir kural kümesi içeren birleştirilmiş bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="3e474-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="3e474-115">Bağımlılık ekleme, .NET Core 'un kendisi içinde yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="3e474-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="3e474-116">Bu `Startup.cs` , örnekteki uygulamada gösterildiği gibi ' de yapılandırılabilir `eShopPorted` .</span><span class="sxs-lookup"><span data-stu-id="3e474-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="3e474-117">HttpResponseMessage 'ı ASP.NET Core geçirin</span><span class="sxs-lookup"><span data-stu-id="3e474-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="3e474-118">Bazı ASP.NET Web API uygulamaları, döndüren eylem yöntemlerine sahip olabilir `HttpResponseMessage` .</span><span class="sxs-lookup"><span data-stu-id="3e474-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="3e474-119">Bu tür ASP.NET Core yok.</span><span class="sxs-lookup"><span data-stu-id="3e474-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="3e474-120">`Delete` `ResponseMessage` Temel üzerinde yardımcı yöntemi kullanılarak bir eylem yönteminde kullanım örneği aşağıda verilmiştir `ApiController` :</span><span class="sxs-lookup"><span data-stu-id="3e474-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="3e474-121">ASP.NET Core MVC 'de, tüm ortak HTTP yanıt durum kodları için kullanılabilen yardımcı yöntemler bulunur, bu nedenle yukarıdaki yöntem aşağıdaki koda alınır:</span><span class="sxs-lookup"><span data-stu-id="3e474-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="3e474-122">Hiçbir yardımcı olmadığı için bir özel durum kodu döndürmediğiniz fark ederseniz, `return StatusCode(int statusCode)` istediğiniz herhangi bir sayısal kodu döndürmek için her zaman kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="3e474-123">ASP.NET Web API 'sindeki içerik anlaşmasını ASP.NET Core 'ye geçirme</span><span class="sxs-lookup"><span data-stu-id="3e474-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="3e474-124">ASP.NET Web API 2, [içerik anlaşmasını](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) yerel olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="3e474-124">ASP.NET Web API 2 supports [content negotiation](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="3e474-125">Örnek uygulama, `BrandsController` SONUÇLARıNı XML veya JSON olarak listeleyerek bu desteği gösteren bir içerir.</span><span class="sxs-lookup"><span data-stu-id="3e474-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="3e474-126">Bu, isteğin `Accept` üstbilgisine ve veya içerdiğinde değişikliklere dayalıdır `application/xml` `application/json` .</span><span class="sxs-lookup"><span data-stu-id="3e474-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="3e474-127">ASP.NET MVC 5 uygulamalarında yerleşik olarak bulunan içerik anlaşması desteği yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e474-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="3e474-128">İçerik anlaşması, daha esnek olduğu ve API 'nin daha fazla sayıda istemciye uygun hale gelmesini sağlayan belirli bir kodlama türünü döndürmek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="3e474-129">Şu anda belirli bir biçim döndüren eylem yöntemleriniz varsa, ASP.NET Core kod bağlantı noktası oluştururken içerik anlaşmasını destekleyen bir sonuç türü döndürecek şekilde onları değiştirmeyi göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="3e474-130">Aşağıdaki kod, istemci üst bilgi içeriğinden bağımsız olarak JSON biçimindeki verileri döndürür `Accept` :</span><span class="sxs-lookup"><span data-stu-id="3e474-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="3e474-131">ASP.NET Core MVC, uygun bir [dönüş türü](/aspnet/core/web-api/action-return-types) kullanıldığından, [içerik anlaşmasını yerel olarak destekler](/aspnet/core/web-api/advanced/formatting).</span><span class="sxs-lookup"><span data-stu-id="3e474-131">[ASP.NET Core MVC supports content negotiation natively](/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="3e474-132">İçerik anlaşması, denetleyici Yardımcısı yöntemleri tarafından döndürülen durum koduna özgü eylem sonuçları tarafından döndürülen [ObjectResult] tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="3e474-133">ASP.NET Core MVC 'de uygulanan ve içerik anlaşmasını kullanan önceki eylem yöntemi şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="3e474-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="3e474-134">Bu, varsayılan olarak JSON biçimindeki verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e474-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="3e474-135">[Uygulama uygun biçimlendirici ile yapılandırıldıysa](/aspnet/core/web-api/advanced/formatting), XML ve diğer biçimler de kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="3e474-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="custom-model-binding"></a><span data-ttu-id="3e474-136">Özel model bağlama</span><span class="sxs-lookup"><span data-stu-id="3e474-136">Custom model binding</span></span>

<span data-ttu-id="3e474-137">Çoğu ASP.NET MVC ve Web API uygulaması model bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-137">Most ASP.NET MVC and Web API apps make use of model binding.</span></span> <span data-ttu-id="3e474-138">Varsayılan model bağlama söz dizimi, bu uygulamalar ve ASP.NET Core MVC arasında oldukça sorunsuz bir şekilde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-138">The default model binding syntax migrates fairly seamlessly between these apps and ASP.NET Core MVC.</span></span> <span data-ttu-id="3e474-139">Ancak, bazı durumlarda müşteriler belirli model türlerini veya kullanım senaryolarını desteklemek için [özel model ciltleri](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) yazmıştı.</span><span class="sxs-lookup"><span data-stu-id="3e474-139">However, in some cases customers have written [custom model binders](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) to support specific model types or usage scenarios.</span></span> <span data-ttu-id="3e474-140">ASP.NET MVC ve Web API projelerinde özel model ciltler `IModelBinder` `System.Web.Mvc` , sırasıyla ve ad alanlarında tanımlanan ayrı arabirimleri kullanır `System.Web.Http` .</span><span class="sxs-lookup"><span data-stu-id="3e474-140">Custom model binders in ASP.NET MVC and Web API projects use separate `IModelBinder` interfaces defined in `System.Web.Mvc` and `System.Web.Http` namespaces, respectively.</span></span> <span data-ttu-id="3e474-141">Her iki durumda da, özel bağlayıcı `Bind` bir denetleyiciyi veya eylem bağlamını kabul eden bir yöntemi ve bir model bağlama bağlamını bağımsız değişken olarak sunar.</span><span class="sxs-lookup"><span data-stu-id="3e474-141">In both cases, the custom binder exposes a `Bind` method that accepts a controller or action context and a model binding context as arguments.</span></span>

<span data-ttu-id="3e474-142">Özel bağlayıcı oluşturulduktan sonra, uygulamanın uygulamayla kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-142">Once the custom binder is created, it must be registered with the app.</span></span> <span data-ttu-id="3e474-143">Bu adım, bir `ModelBinderProvider` fabrika görevi gören ve bir istek sırasında model cildi oluşturan başka bir tür oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-143">This step requires creating another type, a `ModelBinderProvider`, which acts as a factory and creates the model binder during a request.</span></span> <span data-ttu-id="3e474-144">Şu şekilde, MVC uygulamalarında ciltler eklenebilir `ApplicationStart` :</span><span class="sxs-lookup"><span data-stu-id="3e474-144">Binders can be added during `ApplicationStart` in MVC apps as shown:</span></span>

```csharp
ModelBinderProviders.BinderProviders.Insert(0, new MyCustomBinderProvider()); // MVC
```

<span data-ttu-id="3e474-145">Web API uygulamalarında özel ciltçileri öznitelikler kullanılarak başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-145">In Web API apps, custom binders can be referenced using attributes.</span></span> <span data-ttu-id="3e474-146">`ModelBinder`Öznitelik, gösterildiği gibi eylem yöntemi parametrelerine veya parametrenin tür tanımına eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="3e474-146">The `ModelBinder` attribute can be added to action method parameters or to the parameter's type definition, as shown:</span></span>

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

<span data-ttu-id="3e474-147">Model cildi ASP.NET Web API 'sinde küresel olarak kaydetmek için, uygulamanın başlatılması sırasında sağlayıcının eklenmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="3e474-147">To register a model binder globally in ASP.NET Web API, its provider must be added during app startup:</span></span>

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

<span data-ttu-id="3e474-148">[Özel model sağlayıcılarını ASP.NET Core 'e](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)geçirirken, Web API 'si MODELI ASP.NET MVC 5 ' ten ASP.NET Core yaklaşımına daha yakın olur.</span><span class="sxs-lookup"><span data-stu-id="3e474-148">When migrating [custom model providers to ASP.NET Core](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample), the Web API pattern is closer to the ASP.NET Core approach than the ASP.NET MVC 5.</span></span> <span data-ttu-id="3e474-149">ASP.NET Core `IModelBinder` arabirimi ve Web API 'si arasındaki temel farklılıklar, ASP.NET Core yönteminin zaman uyumsuz ( `BindModelAsync` ) ve yalnızca `BindingModelContext` Web API 'sinin sürümü gereken iki parametre yerine yalnızca tek bir parametre gerektirmesidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-149">The main differences between ASP.NET Core's `IModelBinder` interface and Web API's is that the ASP.NET Core method is async (`BindModelAsync`) and it only requires a single `BindingModelContext` parameter instead of two parameters like Web API's version required.</span></span> <span data-ttu-id="3e474-150">ASP.NET Core, `[ModelBinder]` tek tek eylem yöntemi parametrelerinde veya bunlarla ilişkili türlerde bir özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-150">In ASP.NET Core, you can use a `[ModelBinder]` attribute on individual action method parameters or their associated types.</span></span> <span data-ttu-id="3e474-151">Ayrıca `ModelBinderProvider` , uygun yerlerde uygulama içinde genel olarak kullanılacak bir de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-151">You can also create a `ModelBinderProvider` that will be used globally within the app where appropriate.</span></span> <span data-ttu-id="3e474-152">Böyle bir sağlayıcıyı yapılandırmak için içine kod ekleyin `Startup` `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="3e474-152">To configure such a provider, you would add code to `Startup` in `ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.ModelBinderProviders.Insert(0, new CustomModelBinderProvider());
    });
}
```

## <a name="media-formatters"></a><span data-ttu-id="3e474-153">Medya biçimleri</span><span class="sxs-lookup"><span data-stu-id="3e474-153">Media formatters</span></span>

<span data-ttu-id="3e474-154">ASP.NET Web API 'SI, birden çok medya biçimini destekler ve özel medya formatlayıcıları kullanılarak genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-154">ASP.NET Web API supports multiple media formats and can be extended by using custom media formatters.</span></span> <span data-ttu-id="3e474-155">Docs, verileri virgülle ayrılmış değer biçiminde göndermek için kullanılabilecek [Örnek BIR CSV medya biçimlendirici](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) tanımlıyor.</span><span class="sxs-lookup"><span data-stu-id="3e474-155">The docs describe an [example CSV Media Formatter](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) that can be used to send data in a comma-separated value format.</span></span> <span data-ttu-id="3e474-156">Web API uygulamanız özel medya biçimleri kullanıyorsa, bunları [özel biçim ASP.NET Core](/aspnet/core/web-api/advanced/custom-formatters)dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-156">If your Web API app uses custom media formatters, you'll need to convert them to [ASP.NET Core custom formatters](/aspnet/core/web-api/advanced/custom-formatters).</span></span>

<span data-ttu-id="3e474-157">Web API 2 ' de özel bir biçimlendirici oluşturmak için uygun bir temel sınıftan devralmış ve sonra nesneyi kullanarak biçimlendirici Web API işlem hattına eklemiş olursunuz `HttpConfiguration` :</span><span class="sxs-lookup"><span data-stu-id="3e474-157">To create a custom formatter in Web API 2, you inherited from an appropriate base class and then added the formatter to the Web API pipeline using the `HttpConfiguration` object:</span></span>

```csharp
public static void ConfigureApis(HttpConfiguration config)
{
    config.Formatters.Add(new ProductCsvFormatter());
}
```

<span data-ttu-id="3e474-158">ASP.NET Core, işlem benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3e474-158">In ASP.NET Core, the process is similar.</span></span> <span data-ttu-id="3e474-159">ASP.NET Core hem giriş biçimlerini (model bağlama tarafından kullanılır) hem de çıkış formatlarını destekler (yanıtları biçimlendirmek için kullanılır).</span><span class="sxs-lookup"><span data-stu-id="3e474-159">ASP.NET Core supports both input formatters (used by model binding) and output formatters (used to format responses).</span></span> <span data-ttu-id="3e474-160">Belirli bir şekilde çıkış yanıtlarına özel bir biçimlendirici eklemek, uygun bir taban sınıftan devralmayı ve içindeki bir biçimlendirici öğesini ' deki MVC 'ye eklemeyi içerir `Startup` :</span><span class="sxs-lookup"><span data-stu-id="3e474-160">Adding a custom formatter to output responses in a specific way involves inheriting from an appropriate base class and adding the formatter to MVC in `Startup`:</span></span>

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

<span data-ttu-id="3e474-161">[Microsoft. AspNetCore. Mvc. Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) ad alanındaki temel sınıfların tamamen bir listesini bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="3e474-161">You'll find a complete list of base classes in the [Microsoft.AspNetCore.Mvc.Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) namespace.</span></span>

<span data-ttu-id="3e474-162">Bir Web API biçimlendirici 'dan ASP.NET Core MVC biçimlendirici 'e geçiş adımları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3e474-162">The steps to migrate from a Web API formatter to an ASP.NET Core MVC formatter are:</span></span>

1. <span data-ttu-id="3e474-163">Yeni biçimlendirici için uygun bir temel sınıf belirler.</span><span class="sxs-lookup"><span data-stu-id="3e474-163">Identify an appropriate base class for the new formatter.</span></span>
1. <span data-ttu-id="3e474-164">Temel sınıfın yeni bir örneğini oluşturun ve gerekli yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3e474-164">Create a new instance of the base class and implement its required methods.</span></span>
1. <span data-ttu-id="3e474-165">Web API biçimlendirici içindeki işlevselliği yeni uygulamaya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e474-165">Copy over the functionality from the Web API formatter to the new implementation.</span></span>
1. <span data-ttu-id="3e474-166">`ConfigureServices`Yeni biçimlendirici kullanmak için ASP.NET Core uygulamanın YÖNTEMINDE MVC 'yi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="3e474-166">Configure MVC in the ASP.NET Core App's `ConfigureServices` method to use the new formatter.</span></span>

## <a name="custom-filters"></a><span data-ttu-id="3e474-167">Özel filtreler</span><span class="sxs-lookup"><span data-stu-id="3e474-167">Custom filters</span></span>

<span data-ttu-id="3e474-168">Filtreler, istek işleme ardışık düzeninde belirli aşamaların önce ve/veya sonrasında kodu yürütmek için ASP.NET Core uygulamalarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-168">Filters are used in ASP.NET Core apps to execute code before and/or after certain stages in the request processing pipeline.</span></span> <span data-ttu-id="3e474-169">ASP.NET MVC ve Web API 'SI de aynı şekilde filtreler kullanır, ancak ayrıntılar farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e474-169">ASP.NET MVC and Web API also use filters in much the same way, but the details vary.</span></span> <span data-ttu-id="3e474-170">Örneğin, [ASP.NET MVC dört tür filtreyi destekler](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters).</span><span class="sxs-lookup"><span data-stu-id="3e474-170">For instance, [ASP.NET MVC supports four kinds of filters](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters).</span></span> <span data-ttu-id="3e474-171">ASP.NET Web API 2 benzer filtreleri destekler ve [filtreleri geçersiz kılmak](/dotnet/api/system.web.mvc.filters.ioverridefilter)IÇIN hem MVC hem de Web API 'si dahil öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e474-171">ASP.NET Web API 2 supports similar filters, and both MVC and Web API included attributes to [override filters](/dotnet/api/system.web.mvc.filters.ioverridefilter).</span></span>

<span data-ttu-id="3e474-172">ASP.NET MVC ve Web API uygulamalarında kullanılan en yaygın filtre, bir [IActionFilter arabirimi](/dotnet/api/system.web.mvc.iactionfilter)tarafından tanımlanan eylem filtresidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-172">The most common filter used in ASP.NET MVC and Web API apps is the action filter, which is defined by an [IActionFilter interface](/dotnet/api/system.web.mvc.iactionfilter).</span></span> <span data-ttu-id="3e474-173">Bu arabirim `OnActionExecuting` `OnActionExecuted` , her yöntemde belirtildiği gibi bir eylem yürütmeden önce ve/veya sonrasında kodu yürütmek için kullanılan () ve After () için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-173">This interface provides methods for before (`OnActionExecuting`) and after (`OnActionExecuted`) which can be used to execute code before and/or after an action executes, as noted for each method.</span></span>

<span data-ttu-id="3e474-174">ASP.NET Core filtreleri desteklemeye devam eder ve MVC ve Web API 'sinin birleşme sürümü, uygulamalarına yalnızca bir yaklaşım olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3e474-174">ASP.NET Core continues to support filters, and its unification of MVC and Web API means there is only one approach to their implementation.</span></span> <span data-ttu-id="3e474-175">Docs, ASP.NET Core MVC ' de yerleşik olarak bulunan [ve beş (5) tür filtrelerin ayrıntılı kapsamını içerir](/aspnet/core/mvc/controllers/filters#filter-types).</span><span class="sxs-lookup"><span data-stu-id="3e474-175">The [docs include detailed coverage of the five (5) kinds of filters built into ASP.NET Core MVC](/aspnet/core/mvc/controllers/filters#filter-types).</span></span> <span data-ttu-id="3e474-176">ASP.NET MVC ve ASP.NET Web API 'sinde desteklenen tüm filtre türevleri ASP.NET Core ilişkili sürümlere sahiptir, bu nedenle geçiş genellikle uygun arabirimi ve/veya temel sınıfı tanımlamayı ve kodun üzerine geçirilmesini bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-176">All of the filter variants supported in ASP.NET MVC and ASP.NET Web API have associated versions in ASP.NET Core, so migration is generally just a matter of identifying the appropriate interface and/or base class and migrating the code over.</span></span>

<span data-ttu-id="3e474-177">Zaman uyumlu arayüzlere ek olarak ASP.NET Core, ayrıca `IAsyncActionFilter` , kodu gösterildiği gibi, eylemden önce ve sonra çalıştırılacak şekilde kullanılabilecek tek bir zaman uyumsuz yöntem sağlayan zaman uyumsuz arabirimler de sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e474-177">In addition to the synchronous interfaces, ASP.NET Core also provides async interfaces like `IAsyncActionFilter` which provide a single async method that can be used to incorporate code to run both before and after the action, as shown:</span></span>

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

<span data-ttu-id="3e474-178">Zaman uyumsuz kodu (veya zaman uyumsuz olması gereken kodu) geçirirken takımlar, bu amaçla sağlanmış olan yerleşik zaman uyumsuz türleri kullanmayı göz önünde bulundurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-178">When migrating async code (or code that should be async), teams should consider leveraging the built in async types that are provided for this purpose.</span></span>

<span data-ttu-id="3e474-179">Çoğu ASP.NET MVC ve Web API uygulaması çok sayıda özel filtre kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="3e474-179">Most ASP.NET MVC and Web API apps do not use a large number of custom filters.</span></span> <span data-ttu-id="3e474-180">ASP.NET Core MVC 'deki filtrelere yönelik yaklaşım, ASP.NET MVC ve Web API 'SI filtreleriyle yakından hizalandığından, özel filtrelerin geçirilmesi genellikle oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="3e474-180">Since the approach to filters in ASP.NET Core MVC is closely aligned with filters in ASP.NET MVC and Web API, the migration of custom filters is generally fairly straightforward.</span></span> <span data-ttu-id="3e474-181">ASP.NET Core docs ' deki filtrelerle ilgili ayrıntılı belgeleri okuduğunuzdan emin olun ve bunları iyi bir şekilde öğrendiğinizden emin olduktan sonra, eski sistemden yeni sistem filtrelerine yönelik mantığı bağlantı noktası alın.</span><span class="sxs-lookup"><span data-stu-id="3e474-181">Be sure to read the detailed documentation on filters in ASP.NET Core's docs, and once you're sure you have a good understanding of them, port the logic from the old system to the new system's filters.</span></span>

## <a name="route-constraints"></a><span data-ttu-id="3e474-182">Yol kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3e474-182">Route constraints</span></span>

<span data-ttu-id="3e474-183">ASP.NET Core, isteklerin bir isteği yönlendirmek için düzgün yönlendirildiğinden emin olmak için yol kısıtlamalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-183">ASP.NET Core uses route constraints to help ensure requests are routed properly to route a request.</span></span> <span data-ttu-id="3e474-184">[ASP.NET Core bu amaç için çok sayıda farklı yol kısıtlaması destekler]/ASPNET/Core/temelde Mentals/Routing # Route-Constraint-Reference).</span><span class="sxs-lookup"><span data-stu-id="3e474-184">[ASP.NET Core supports a large number of different route constraints for this purpose]/aspnet/core/fundamentals/routing#route-constraint-reference).</span></span> <span data-ttu-id="3e474-185">Yol kısıtlamaları yol tablosuna uygulanabilir, ancak ASP.NET MVC 5 ve/veya [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) ile oluşturulan çoğu uygulama, öznitelik yollarına uygulanan satır içi yol kısıtlamalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-185">Route constraints can be applied in the route table, but most apps built with ASP.NET MVC 5 and/or [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) use inline route constraints applied to attribute routes.</span></span> <span data-ttu-id="3e474-186">Satır içi yol kısıtlamaları şöyle bir biçim kullanır:</span><span class="sxs-lookup"><span data-stu-id="3e474-186">Inline route constraints use a format like this one:</span></span>

```csharp
[Route("/customer/{id:int}")]
```

<span data-ttu-id="3e474-187">`:int` `id` Route parametresinden sonra değeri, türü ile eşleşecek şekilde kısıtlar `int` .</span><span class="sxs-lookup"><span data-stu-id="3e474-187">The `:int` after the `id` route parameter constrains the value to match the the `int` type.</span></span> <span data-ttu-id="3e474-188">Yol kısıtlamalarını kullanmanın bir avantajı, parametrelerin yalnızca kendi türlerine göre farklılık gösterdiği iki farklı yolun mevcut olmasına izin vermelerinin olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-188">One benefit of using route constraints is that they allow for two otherwise-identical routes to exist where the parameters differ only by their type.</span></span> <span data-ttu-id="3e474-189">Bu, yalnızca parametre türüne dayalı yolların [yöntem aşırı](/dotnet/standard/design-guidelines/member-overloading) yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="3e474-189">This allows for the equivalent of [method overloading](/dotnet/standard/design-guidelines/member-overloading) of routes based solely on parameter type.</span></span>

<span data-ttu-id="3e474-190">Yol kısıtlamaları kümesi, söz dizimi ve kullanımları, üç yaklaşım arasında çok benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3e474-190">The set of route constraints, their syntax, and usage is very similar between all three approaches.</span></span> <span data-ttu-id="3e474-191">Özel yol kısıtlamaları müşteri uygulamalarında oldukça nadir bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="3e474-191">Custom route constraints are fairly rare in customer applications.</span></span> <span data-ttu-id="3e474-192">Uygulamanız özel bir yol kısıtlaması kullanıyorsa ve ASP.NET Core bağlantı noktası olması gerekiyorsa docs, [ASP.NET Core içinde özel yol kısıtlamaları oluşturmayı](/aspnet/core/fundamentals/routing#custom-route-constraints)gösteren örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="3e474-192">If your app uses a custom route constraint and needs to port to ASP.NET Core, the docs include examples showing [how to create custom route constraints in ASP.NET Core](/aspnet/core/fundamentals/routing#custom-route-constraints).</span></span> <span data-ttu-id="3e474-193">Temel olarak tüm gerekli olan `IRouteConstraint` ve `Match` yöntemi uygulamak ve ardından uygulama için yönlendirmeyi yapılandırırken özel kısıtlamayı eklemektir:</span><span class="sxs-lookup"><span data-stu-id="3e474-193">Essentially all that's required is to implement `IRouteConstraint` and its `Match` method, and then add the custom constraint when configuring routing for the app:</span></span>

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

<span data-ttu-id="3e474-194">Bu, özel kısıtlamaların ASP.NET Web API 'sinde kullanılanlara çok benzer ve bu, `IHttpRouteConstraint` bir çözümleyici ve için bir çağrı kullanarak onu kullanır ve yapılandırır `HttpConfiguration.MapHttpAttributeRoutes` :</span><span class="sxs-lookup"><span data-stu-id="3e474-194">This is very similar to how custom constraints are used in ASP.NET Web API, which uses `IHttpRouteConstraint` and configures it using a resolver and a call to `HttpConfiguration.MapHttpAttributeRoutes`:</span></span>

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

<span data-ttu-id="3e474-195">ASP.NET MVC 5, `IRouteConstraint` arabirim adı için kullanarak ve yol yapılandırmasının bir parçası olarak kısıtlamayı yapılandırarak çok benzer bir yaklaşım izler:</span><span class="sxs-lookup"><span data-stu-id="3e474-195">ASP.NET MVC 5 follows a very similar approach, using `IRouteConstraint` for its interface name and configuring the constraint as part of route configuration:</span></span>

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

<span data-ttu-id="3e474-196">Yol kısıtlama kullanımının ve ASP.NET Core özel yol kısıtlamalarının geçirilmesi genellikle çok basittir.</span><span class="sxs-lookup"><span data-stu-id="3e474-196">Migrating route constraint usage as well as custom route constraints to ASP.NET Core is typically very straightforward.</span></span>

## <a name="custom-route-handlers"></a><span data-ttu-id="3e474-197">Özel yol işleyicileri</span><span class="sxs-lookup"><span data-stu-id="3e474-197">Custom route handlers</span></span>

<span data-ttu-id="3e474-198">ASP.NET MVC 5 ' in başka bir oldukça gelişmiş özelliği yol işleyicileridir.</span><span class="sxs-lookup"><span data-stu-id="3e474-198">Another fairly advanced feature of ASP.NET MVC 5 is route handlers.</span></span> <span data-ttu-id="3e474-199">Özel yol işleyicileri `IRouteHandler` , `IHttpHandler` bir verme isteği için döndüren tek bir yöntemi içeren uygular.</span><span class="sxs-lookup"><span data-stu-id="3e474-199">Custom route handlers implement `IRouteHandler`, which includes a single method that returns an `IHttpHandler` for a give request.</span></span> <span data-ttu-id="3e474-200">, `IHttpHandler` Sırasıyla bir `IsReusable` özelliği ve tek bir `ProcessRequest` yöntemi sunar.</span><span class="sxs-lookup"><span data-stu-id="3e474-200">The `IHttpHandler`, in turn, exposes an `IsReusable` property and a single `ProcessRequest` method.</span></span> <span data-ttu-id="3e474-201">ASP.NET MVC 5 ' te, özel işleyicinizi kullanmak için yol tablosunda belirli bir yolu yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e474-201">In ASP.NET MVC 5, you can configure a particular route in the route table to use your custom handler:</span></span>

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.Add(new Route("custom", new CustomRouteHandler()));
}
```

<span data-ttu-id="3e474-202">Özel yol işleyicilerini ASP.NET MVC 5 ' ten ASP.NET Core geçirmek için bir filtre (eylem filtresi gibi) veya özel bir filtre kullanabilirsiniz [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter) .</span><span class="sxs-lookup"><span data-stu-id="3e474-202">To migrate custom route handlers from ASP.NET MVC 5 to ASP.NET Core, you can either use a filter (such as an action filter) or a custom [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter).</span></span> <span data-ttu-id="3e474-203">Filtre yaklaşımı nispeten basittir ve `ConfigureServices` *Başlangıç. cs*' ye MVC eklendiğinde genel bir filtre olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-203">The filter approach is relatively straightforward, and can be added as a global filter when MVC is added to `ConfigureServices` in *Startup.cs*.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(CustomActionFilter));
    });
}
```

<span data-ttu-id="3e474-204">`IRouter`Seçeneği, arabirimin ve yöntemlerinin uygulanması gerekir `RouteAsync` `GetVirtualPath` .</span><span class="sxs-lookup"><span data-stu-id="3e474-204">The `IRouter` option requires implementing the interface's `RouteAsync` and `GetVirtualPath` methods.</span></span> <span data-ttu-id="3e474-205">Özel yönlendirici, `Configure` *Başlangıç. cs* içindeki yönteminde istek ardışık düzenine eklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-205">The custom router is added to the request pipeline in the `Configure` method in *Startup.cs*.</span></span>

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

<span data-ttu-id="3e474-206">ASP.NET Web API 'sinde, Bu işleyiciler *yol işleyicileri* yerine [özel ileti işleyicileri](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-206">In ASP.NET Web API, these handlers are referred to as [custom message handlers](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers), rather than *route handlers*.</span></span> <span data-ttu-id="3e474-207">İleti işleyicileri öğesinden türetilmelidir `DelegatingHandler` ve metodunu geçersiz kılmalıdır `SendAsync` .</span><span class="sxs-lookup"><span data-stu-id="3e474-207">Message handlers must derive from `DelegatingHandler` and override its `SendAsync` method.</span></span> <span data-ttu-id="3e474-208">İleti işleyicileri, ASP.NET Core ara yazılım ve istek işlem hattına çok benzeyen bir şekilde işlem hattı oluşturmak için birlikte zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-208">Message handlers can be chained together to form a pipeline in a fashion that is very similar to ASP.NET Core middleware and its request pipeline.</span></span>

<span data-ttu-id="3e474-209">ASP.NET Core `DelegatingHandler` tür veya ayrı ileti işleyici işlem hattı yok.</span><span class="sxs-lookup"><span data-stu-id="3e474-209">ASP.NET Core has no `DelegatingHandler` type or separate message handler pipeline.</span></span> <span data-ttu-id="3e474-210">Bunun yerine, bu tür işleyiciler genel filtreler, özel `IRouter` örnekler (yukarıya bakın) veya özel ara yazılım kullanılarak geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-210">Instead, such handlers should be migrated using global filters, custom `IRouter` instances (see above), or custom middleware.</span></span> <span data-ttu-id="3e474-211">ASP.NET Core MVC filtreleri ve `IRouter` türleri, denetleyiciler ve eylemler gıbı MVC yapılarına yerleşik erişim sahibi olmanın avantajlarından yararlanır. ara yazılım, MVC 'ye yönelik bir özellikleri olmayan daha düşük bir yaklaşımda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e474-211">ASP.NET Core MVC filters and `IRouter` types have the advantage of having built-in access to MVC constructs like controllers and actions, while middleware is a lower level approach that has no ties to MVC.</span></span> <span data-ttu-id="3e474-212">Bu da daha esnek hale gelir, ancak MVC bileşenlerine erişmeniz gerekiyorsa daha fazla çaba gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3e474-212">This makes it more flexible but also requires more effort if you need to access MVC components.</span></span>

## <a name="cors-support"></a><span data-ttu-id="3e474-213">CORS desteği</span><span class="sxs-lookup"><span data-stu-id="3e474-213">CORS support</span></span>

<span data-ttu-id="3e474-214">CORS veya çıkış noktaları arası kaynak paylaşımı, sunucuların, sundukları yanıtlardan kaynaklanmayan istekleri kabul etmesine olanak tanıyan bir W3C standardıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-214">CORS, or Cross-Origin Resource Sharing, is a W3C standard that allows servers to accept requests that don't originate from responses they've served.</span></span> <span data-ttu-id="3e474-215">ASP.NET MVC 5 ve ASP.NET Web API 2, CORS 'yi farklı yollarla destekler.</span><span class="sxs-lookup"><span data-stu-id="3e474-215">ASP.NET MVC 5 and ASP.NET Web API 2 support CORS in different ways.</span></span> <span data-ttu-id="3e474-216">ASP.NET MVC 5 ' te CORS desteğini etkinleştirmenin en kolay yolu aşağıdakine benzer bir eylem filtresine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3e474-216">The simplest way to enable CORS support in ASP.NET MVC 5 is with an action filter like this one:</span></span>

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

<span data-ttu-id="3e474-217">ASP.NET Web API 'SI de bu tür bir filtre kullanabilir, ancak [CORS 'yi etkinleştirmek için yerleşik desteğe](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3e474-217">ASP.NET Web API can also use such a filter, but it has [built-in support for enabling CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) as well:</span></span>

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

<span data-ttu-id="3e474-218">Bu eklendikten sonra özniteliği kullanarak izin verilen kaynakları, üstbilgileri ve yöntemleri `EnableCors` aşağıdaki gibi yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e474-218">Once this is added, you can configure allowed origins, headers, and methods using the `EnableCors` attribute, like so:</span></span>

```csharp
[EnableCors(origins: "https://dot.net", headers: "*", methods: "*")]
public class TestController : ApiController
{
    // Controller methods not shown...
}
```

<span data-ttu-id="3e474-219">CORS uygulamanızı ASP.NET MVC 5 veya ASP.NET Web API 2 ' den geçirmeden önce [CORS 'nin nasıl çalıştığını](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) gözden geçirdiğinizden emin olun ve CORS 'nin geçerli sisteminizde beklendiği gibi çalıştığını gösteren bazı otomatikleştirilmiş testler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e474-219">Before migrating your CORS implementation from ASP.NET MVC 5 or ASP.NET Web API 2, be sure to review [how CORS works](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) and create some automated tests that demonstrate CORS is working as expected in your current system.</span></span>

<span data-ttu-id="3e474-220">ASP.NET Core, CORS 'yi etkinleştirmek için üç yerleşik yol vardır:</span><span class="sxs-lookup"><span data-stu-id="3e474-220">In ASP.NET Core, there are three built-in ways to enable CORS:</span></span>

- <span data-ttu-id="3e474-221">İçinde [ilke aracılığıyla yapılandırılır](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware)`ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="3e474-221">[Configured via policy](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware) in `ConfigureServices`</span></span>
- <span data-ttu-id="3e474-222">[Uç nokta yönlendirme](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing) ile etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="3e474-222">Enabled with [endpoint routing](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)</span></span>
- <span data-ttu-id="3e474-223">[ `EnableCors` Özniteliği](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes) ile etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="3e474-223">Enabled with the [`EnableCors` attribute](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)</span></span>

<span data-ttu-id="3e474-224">Bu yaklaşımlardan her biri, yukarıdaki seçeneklerden bağlantılı olan docs 'ta ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e474-224">Each of these approaches is covered in detail in the docs, which are linked from the above options.</span></span> <span data-ttu-id="3e474-225">Seçtiğiniz bu, büyük ölçüde mevcut uygulamanızın CORS 'yi nasıl desteklediğine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-225">Which one you choose will largely depend on how your existing app supports CORS.</span></span> <span data-ttu-id="3e474-226">Uygulama öznitelikleri kullanıyorsa, muhtemelen özniteliğini en kolay şekilde kullanmaya geçiş yapabilirsiniz `EnableCors` .</span><span class="sxs-lookup"><span data-stu-id="3e474-226">If the app uses attributes, you can probably migrate to use the `EnableCors` attribute most easily.</span></span> <span data-ttu-id="3e474-227">Uygulamanız filtreler kullanıyorsa, bu yaklaşımı kullanmaya devam edebilirsiniz (ASP.NET Core) veya bu yaklaşım için kullanılan tipik yaklaşım olmasa da, öznitelikleri veya ilkeleri kullanmak için geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e474-227">If your app uses filters, you could continue using that approach (though it's not the typical approach used in ASP.NET Core), or migrate to use attributes or policies.</span></span> <span data-ttu-id="3e474-228">Uç nokta yönlendirme, ASP.NET Core 3 ile sunulan görece yeni bir özelliktir ve bu nedenle ASP.NET MVC 5 veya ASP.NET Web API 2 uygulamalarında kapalı bir analog yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e474-228">Endpoint routing is a relatively new feature introduced with ASP.NET Core 3 and as such it doesn't have a close analog in ASP.NET MVC 5 or ASP.NET Web API 2 apps.</span></span>

## <a name="custom-areas"></a><span data-ttu-id="3e474-229">Özel bölgeler</span><span class="sxs-lookup"><span data-stu-id="3e474-229">Custom areas</span></span>

<span data-ttu-id="3e474-230">Birçok ASP.NET MVC uygulaması, projeyi düzenlemek için alan kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e474-230">Many ASP.NET MVC apps use Areas to organize the project.</span></span> <span data-ttu-id="3e474-231">Bölgeler genellikle bir *bölgeler* klasöründeki projenin kökünde bulunur ve uygulama başladığında, genellikle içinde bir kayıt olmalıdır `Application_Start()` .</span><span class="sxs-lookup"><span data-stu-id="3e474-231">Areas typically reside in the root of the project in an *Areas* folder, and must be registered when the application starts, typically in `Application_Start()`:</span></span>

```csharp
AreaRegistration.RegisterAllAreas();
```

<span data-ttu-id="3e474-232">Başlangıçtaki tüm alanları kaydetmenin alternatifi, `RouteArea` tek tek denetleyicilerde özniteliğini kullanmaktır:</span><span class="sxs-lookup"><span data-stu-id="3e474-232">An alternative to registering all areas in startup is to use the `RouteArea` attribute on individual controllers:</span></span>

```csharp
[RouteArea("Admin")]
public class SomeController : Controller
```

<span data-ttu-id="3e474-233">Alan kullanırken, farklı alanlardaki eylemlere bağlantılar oluşturmak için ek bağımsız değişkenler HTML yardımcı yöntemlerine geçirilir:</span><span class="sxs-lookup"><span data-stu-id="3e474-233">When using Areas, additional arguments are passed into HTML helper methods to generate links to actions in different areas:</span></span>

```cshtml
@Html.ActionLink("News", "Index", "News", new { area = "News" }, null)
```

<span data-ttu-id="3e474-234">ASP.NET Web API 'SI uygulamaları, denetleyicileri projedeki herhangi bir klasöre yerleştirilediklerinden, genellikle alanları açık bir şekilde kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="3e474-234">ASP.NET Web API apps don't typically use areas explicitly, since their controllers can be placed in any folder in the project.</span></span> <span data-ttu-id="3e474-235">Takımlar, API denetleyicilerini düzenlemek gibi herhangi bir klasör yapısını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-235">Teams can use any folder structure they like to organize their API controllers.</span></span>

<span data-ttu-id="3e474-236">ASP.NET Core MVC 'de [alan](/aspnet/core/mvc/controllers/areas) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-236">[Areas](/aspnet/core/mvc/controllers/areas) are supported in ASP.NET Core MVC.</span></span> <span data-ttu-id="3e474-237">Kullanılan yaklaşım, ASP.NET MVC 5 içindeki alanların kullanımıyla neredeyse aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3e474-237">The approach used is nearly identical to the use of areas in ASP.NET MVC 5.</span></span> <span data-ttu-id="3e474-238">Alan kullanarak kod geçişi yapan geliştiriciler aşağıdaki farklılıkları göz önünde bulundurmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="3e474-238">Developers migrating code using areas should keep in mind the following differences:</span></span>

- <span data-ttu-id="3e474-239">`AreaRegistration.RegisterAllAreas` ASP.NET Core MVC 'de kullanılmaz</span><span class="sxs-lookup"><span data-stu-id="3e474-239">`AreaRegistration.RegisterAllAreas` is not used in ASP.NET Core MVC</span></span>
- <span data-ttu-id="3e474-240">Bölgeler, özniteliği kullanılarak uygulanır `[Area("name")]` ( `RouteArea` ASP.NET MVC 5 içinde değil)</span><span class="sxs-lookup"><span data-stu-id="3e474-240">Areas are applied using the `[Area("name")]` attribute (not `RouteArea` as in ASP.NET MVC 5)</span></span>
- <span data-ttu-id="3e474-241">İsterseniz, yol tablosu şablonlarına (veya öznitelik yönlendirme kullanabilirler) alan eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-241">Areas can be added to the route table templates, if desired (or they can use attribute routing)</span></span>

<span data-ttu-id="3e474-242">ASP.NET Core MVC 'de yol tablosuna alan desteği eklemek için, `Configure` *Başlangıç. cs*' ye şunu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3e474-242">To add area support to the route table in ASP.NET Core MVC, you would add the following in `Configure` in *Startup.cs*:</span></span>

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

<span data-ttu-id="3e474-243">Alanları, yol tanımındaki anahtar sözcüğü kullanılarak öznitelik yönlendirme ile de kullanılabilir `{area}` (yol şablonlarıyla kullanılabilecek birkaç [ayrılmış yönlendirme adlarından](/aspnet/core/mvc/controllers/routing#reserved-routing-names) biridir).</span><span class="sxs-lookup"><span data-stu-id="3e474-243">Areas can also be used with attribute routing, using the `{area}` keyword in the route definition (it's one of several [reserved routing names](/aspnet/core/mvc/controllers/routing#reserved-routing-names) that can be used with route templates).</span></span>

<span data-ttu-id="3e474-244">Etiket Yardımcıları `asp-area` , Razor görünümlerinde ve sayfalarında bağlantı oluşturmak için kullanılabilecek özniteliği olan bölgeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="3e474-244">Tag helpers support areas with the `asp-area` attribute, which can be used to generate links in Razor views and pages:</span></span>

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

<span data-ttu-id="3e474-245">Razor Pages geçiş yapıyorsanız, *Sayfalar* klasörünüzde bir *alan* klasörü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-245">If you're migrating to Razor Pages you will need to use an *Areas* folder in your *Pages* folder.</span></span> <span data-ttu-id="3e474-246">Daha fazla bilgi için bkz. [Razor Pages alanlara](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages)bakın.</span><span class="sxs-lookup"><span data-stu-id="3e474-246">For more information, see [Areas with Razor Pages](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages).</span></span>

<span data-ttu-id="3e474-247">Yukarıdaki kılavuza ek olarak takımlar ASP.NET Core içindeki yönlendirmenin, geçiş planlama sürecinin bir parçası olarak [alanlarla nasıl çalıştığını](/aspnet/core/mvc/controllers/routing#areas) incelemelidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-247">In addition to the above guidance, teams should review [how routing in ASP.NET Core works with areas](/aspnet/core/mvc/controllers/routing#areas) as part of their migration planning process.</span></span>

## <a name="integration-tests-for-aspnet-mvc-and-aspnet-web-api"></a><span data-ttu-id="3e474-248">ASP.NET MVC ve ASP.NET Web API 'SI için tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="3e474-248">Integration tests for ASP.NET MVC and ASP.NET Web API</span></span>

<span data-ttu-id="3e474-249">Tümleştirme testleri, bir uygulamanın çeşitli farklı bölümlerinin doğru şekilde çalıştığını doğrulayan otomatikleştirilmiş testlerdir.</span><span class="sxs-lookup"><span data-stu-id="3e474-249">Integration tests are automated tests that verify several different parts of an app work together correctly.</span></span> <span data-ttu-id="3e474-250">Genellikle uygulamayı bir yerel IIS veya IIS Express gibi gerçek bir Web sunucusuna dağıtmaya dahil olan ASP.NET MVC ve ASP.NET Web API 'SI için tümleştirme testleri yazma ve ardından HTTP istemcisi kullanarak bu barındırılan uygulamaya istek yapma.</span><span class="sxs-lookup"><span data-stu-id="3e474-250">Writing integration tests for ASP.NET MVC and ASP.NET Web API usually involved deploying the app to a real web server, such as a local instance of IIS or IIS Express, and then making requests to this hosted application using an HTTP client.</span></span> <span data-ttu-id="3e474-251">Bu testlerin bazıları [Selenium](https://www.selenium.dev/)gibi tarayıcı otomasyon araçları kullanılarak istemci tarafı Kullanıcı arabirimiyle etkileşime geçebilir, ancak bunlar genellikle tümleştirme testleri yerine *UI testleri* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-251">Some of these tests may interact with the client-side user interface using browser automation tools like [Selenium](https://www.selenium.dev/), though often these are referred to as *UI tests* rather than integration tests.</span></span>

<span data-ttu-id="3e474-252">Geçirilen uygulamanız orijinal sürümü ile aynı davranışı paylaşıyorsa, takımın tümleştirme testlerini gerçekleştirmek için kullandığı mevcut teknolojiden (ve UI testlerinde), daha önce olduğu gibi çalışmaya devam etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e474-252">If your migrated app shares the same behavior as its original version, whatever existing technology the team is using to perform integration tests (and UI tests) should continue to work just as it did before.</span></span> <span data-ttu-id="3e474-253">Bu testler genellikle test ettikleri uygulamayı barındırmak için kullanılan temel teknolojiden farklıdır ve yalnızca HTTP istekleri aracılığıyla etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="3e474-253">These tests are usually indifferent to the underlying technology used to host the app they're testing, and interact with it only through HTTP requests.</span></span> <span data-ttu-id="3e474-254">Her şeyin daha zor olduğu durumlarda, testlerin her testten önce bilinen iyi bir duruma getirmek için uygulamayla etkileşime girmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3e474-254">Where things may get more challenging is with how the tests interact with the app to get it into a known good state prior to each test.</span></span> <span data-ttu-id="3e474-255">Yapılandırma ve başlatma ASP.NET Core ASP.NET MVC veya ASP.NET Web API 'siyle karşılaştırıldığında önemli ölçüde farklı olduğundan, bu durum biraz geçiş çabasında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-255">This may require some migration effort, since configuration and startup are significantly different in ASP.NET Core compared to ASP.NET MVC or ASP.NET Web API.</span></span>

<span data-ttu-id="3e474-256">Ekipler, [ASP.NET Core yerleşik tümleştirme test](/aspnet/core/test/integration-tests) desteğini kullanmak üzere tümleştirme testlerini geçirmeyi kesinlikle düşünmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e474-256">Teams should strongly consider migrating their integration tests to use [ASP.NET Core's built-in integration testing](/aspnet/core/test/integration-tests) support.</span></span> <span data-ttu-id="3e474-257">ASP.NET Core, uygulamalar, kullanılarak yapılandırılan bir öğesine dağıtarak test edilebilir `TestHost` `WebApplicationFactory` .</span><span class="sxs-lookup"><span data-stu-id="3e474-257">In ASP.NET Core, apps can be tested by deploying them to a `TestHost`, which is configured using a `WebApplicationFactory`.</span></span> <span data-ttu-id="3e474-258">Uygulamayı test etmek için barındırmak için gereken çok sayıda kurulum vardır, ancak bu durumda, bireysel tümleştirme testlerinin oluşturulması çok basittir.</span><span class="sxs-lookup"><span data-stu-id="3e474-258">There's a little bit of setup required to host the app for testing, but once this is in place, creating individual integration tests is very straightforward.</span></span>

<span data-ttu-id="3e474-259">ASP.NET Core tümleştirme testi desteğinin en iyi özelliklerinden biri, uygulamanın bellekte barındırılmasından biridir.</span><span class="sxs-lookup"><span data-stu-id="3e474-259">One of the best features of ASP.NET Core's integration testing support is that the app is hosted in memory.</span></span> <span data-ttu-id="3e474-260">Uygulamayı barındırmak için gerçek bir Web sunucusu yapılandırmaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e474-260">There's no need to configure a real webserver to host the app.</span></span> <span data-ttu-id="3e474-261">Tarayıcı Otomasyonu aracı kullanmanız gerekmez (yalnızca ASP.NET Core test ediyorsanız, istemci tarafı davranışını test eteceğiz).</span><span class="sxs-lookup"><span data-stu-id="3e474-261">There's no need to use a browser automation tool (if you're only testing ASP.NET Core and not client-side behavior).</span></span> <span data-ttu-id="3e474-262">Güvenlik Duvarı sorunları veya işlem başlatma/durdurma sorunları gibi otomatikleştirilmiş tümleştirme testleri için gerçek bir Web sunucusu kullanılmaya çalışırken karşılaşılabilecek birçok sorun, bu yaklaşımla ortadan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3e474-262">Many of the problems that can be encountered when trying to use a real web server for automated integration tests, such as firewall issues or process start/stop issues, are eliminated with this approach.</span></span> <span data-ttu-id="3e474-263">İsteklerin tümü ağ gereksinimi olmadan bellekte yapıldığından, testler aynı zamanda ayrı bir Web sunucusu ayarlaması ve ağ üzerinden iletişim kurması gereken testlerden çok daha hızlı çalışır (aynı makine üzerinde çalışıyor olsa bile).</span><span class="sxs-lookup"><span data-stu-id="3e474-263">Since the requests are all made in memory with no network requirement, the tests also tend to run much faster than tests that must set up a separate webserver and communicate with it over the network (even if it's running on the same machine).</span></span>

<span data-ttu-id="3e474-264">Aşağıda bir örnek ASP.NET Core tümleştirme testi (bazen alt düzey tümleştirme sınamalarından ayırt etmek için *işlevsel testler* olarak adlandırılır) [Eshoponweb Reference uygulamasından](https://github.com/dotnet-architecture/eShopOnWeb)görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e474-264">Below you can see an example ASP.NET Core integration test (sometimes referred to as *functional tests* to distinguish them from lower-level integration tests) from the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb):</span></span>

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

<span data-ttu-id="3e474-265">Geçirilmekte olan uygulamanın tümleştirme testi yoksa, geçiş işlemi bir miktar eklemek için harika bir fırsat olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e474-265">If the app being migrated has no integration tests, the migration process can be a great opportunity to add some.</span></span> <span data-ttu-id="3e474-266">Bu testler, geçirilen uygulamanın takım tarafından beklediği şekilde davrandığını doğrulayabilirler.</span><span class="sxs-lookup"><span data-stu-id="3e474-266">These tests can verify that the migrated app behaves as the team expects.</span></span> <span data-ttu-id="3e474-267">Bu tür testler bir geçişin başlarında olduğunda, daha sonra geçiş çabalarının uygulamanın daha önce geçirilmiş bölümlerini bozmadığından emin olabilirler.</span><span class="sxs-lookup"><span data-stu-id="3e474-267">When such tests are in place early in a migration, they can ensure that later migration efforts do not break previously migrated portions of the app.</span></span> <span data-ttu-id="3e474-268">ASP.NET Core ' de tümleştirme testlerini ayarlamaya ve çalıştırmaya ne kadar kolay bir şekilde, bu tür testlerin ayarlanması için harcanan yatırımın dönüşü genellikle oldukça yüksektir.</span><span class="sxs-lookup"><span data-stu-id="3e474-268">Given how easy it is to set up and run integration tests in ASP.NET Core, the return on the investment spent setting up such tests is usually pretty high.</span></span>

## <a name="wcf-client-configuration"></a><span data-ttu-id="3e474-269">WCF istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="3e474-269">WCF client configuration</span></span>

<span data-ttu-id="3e474-270">Uygulamanız Şu anda bir istemci olarak WCF hizmetlerini kullanıyorsa, bu senaryo desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e474-270">If your app currently relies on WCF services as a client, this scenario is supported.</span></span> <span data-ttu-id="3e474-271">Ancak, yeni *appsettings.js* dosyasını kullanmak için *web.config* [yapılandırmanızı geçirmeniz](/aspnet/core/migration/configuration) gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="3e474-271">However, you will need to [migrate your configuration](/aspnet/core/migration/configuration) from *web.config* to use the new *appsettings.json* file.</span></span> <span data-ttu-id="3e474-272">Diğer bir seçenek de, siz oluşturduğunuz zaman, istemcilerinize programlı olarak gerekli yapılandırma eklemektir.</span><span class="sxs-lookup"><span data-stu-id="3e474-272">Another option is to add any necessary configuration to your clients programmatically when you create them.</span></span> <span data-ttu-id="3e474-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3e474-273">For example:</span></span>

```csharp
var wcfClient = new OrderServiceClient(
    new BasicHttpBinding(BasicHttpSecurityMode.None),
    new EndpointAddress("http://localhost:5050/OrderService.svc"));
```

<span data-ttu-id="3e474-274">Kuruluşunuzun, uygulamanızın kullandığı WCF kullanılarak oluşturulmuş kapsamlı hizmetleri varsa, bunları gRPC kullanmaya geçirmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="3e474-274">If your organization has extensive services built using WCF that your app relies on, consider migrating them to use gRPC instead.</span></span> <span data-ttu-id="3e474-275">GRPC hakkında daha fazla bilgi için, neden geçiş yapmak isteyebileceğiniz ve ayrıntılı bir geçiş kılavuzu için bkz. [WCF geliştiricileri Için GRPC](/dotnet/architecture/grpc-for-wcf-developers/) eKitap.</span><span class="sxs-lookup"><span data-stu-id="3e474-275">For more details on gRPC, why you may wish to migrate, and a detailed migration guide, consult the [gRPC for WCF Developers](/dotnet/architecture/grpc-for-wcf-developers/) eBook.</span></span>

## <a name="references"></a><span data-ttu-id="3e474-276">Başvurular</span><span class="sxs-lookup"><span data-stu-id="3e474-276">References</span></span>

- [<span data-ttu-id="3e474-277">ASP.NET Web API 'SI Içerik anlaşması</span><span class="sxs-lookup"><span data-stu-id="3e474-277">ASP.NET Web API Content Negotiation</span></span>](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="3e474-278">ASP.NET Core Web API 'sindeki yanıt verilerini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="3e474-278">Format response data in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/formatting)
- [<span data-ttu-id="3e474-279">ASP.NET Web API 'sinde özel model ciltleri</span><span class="sxs-lookup"><span data-stu-id="3e474-279">Custom Model Binders in ASP.NET Web API</span></span>](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)
- [<span data-ttu-id="3e474-280">ASP.NET Core özel model ciltleri</span><span class="sxs-lookup"><span data-stu-id="3e474-280">Custom Model Binders in ASP.NET Core</span></span>](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)
- <span data-ttu-id="3e474-281">[ASP.NET Web API 2 ' de medya biçimleri](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)</span><span class="sxs-lookup"><span data-stu-id="3e474-281">[Media Formatters in ASP.NET Web API 2](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)</span></span>\
- [<span data-ttu-id="3e474-282">ASP.NET Core Web API 'sindeki özel formatıcılar</span><span class="sxs-lookup"><span data-stu-id="3e474-282">Custom formatters in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/custom-formatters)
- [<span data-ttu-id="3e474-283">ASP.NET Core filtreler</span><span class="sxs-lookup"><span data-stu-id="3e474-283">Filters in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/filters)
- [<span data-ttu-id="3e474-284">ASP.NET Web API 2 ' de yol kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3e474-284">Route constraints in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints)
- [<span data-ttu-id="3e474-285">ASP.NET MVC 5 ' teki yol kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3e474-285">Route constraints in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/#route-constraints)
- [<span data-ttu-id="3e474-286">ASP.NET Core Route kısıtlama başvurusu</span><span class="sxs-lookup"><span data-stu-id="3e474-286">ASP.NET Core Route Constraint Reference</span></span>](/aspnet/core/fundamentals/routing#route-constraint-reference)
- [<span data-ttu-id="3e474-287">ASP.NET Web API 2 ' de özel ileti işleyicileri</span><span class="sxs-lookup"><span data-stu-id="3e474-287">Custom message handlers in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)
- [<span data-ttu-id="3e474-288">MVC 5 ve Web API 2 ' de basit CORS denetimi</span><span class="sxs-lookup"><span data-stu-id="3e474-288">Simple CORS control in MVC 5 and Web API 2</span></span>](https://stackoverflow.com/questions/6290053/setting-access-control-allow-origin-in-asp-net-mvc-simplest-possible-method)
- [<span data-ttu-id="3e474-289">Web API 'de çapraz kaynak Isteklerini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3e474-289">Enabling Cross-Origin Requests in Web API</span></span>](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)
- [<span data-ttu-id="3e474-290">ASP.NET Core 'de çıkış noktaları arası Istekleri (CORS) etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3e474-290">Enable Cross-Origin Requests (CORS) in ASP.NET Core</span></span>](/aspnet/core/security/cors)
- [<span data-ttu-id="3e474-291">ASP.NET Core bölgeler</span><span class="sxs-lookup"><span data-stu-id="3e474-291">Areas in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/areas)
- [<span data-ttu-id="3e474-292">ASP.NET Core tümleştirme testleri</span><span class="sxs-lookup"><span data-stu-id="3e474-292">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
><span data-ttu-id="3e474-293">[Önceki](example-migration-eshop.md) 
> [Sonraki](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="3e474-293">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
