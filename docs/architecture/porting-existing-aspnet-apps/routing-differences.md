---
title: ASP.NET MVC ve ASP.NET Core arasındaki yönlendirme farklılıkları
description: Yönlendirme nasıl tanımlanır ve ASP.NET MVC 'de çalışma zamanında nasıl çalışır? Yönlendirme ASP.NET Core uygulamalarda farklı midir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d5c18948248f03a19c97461efe3df38a5be9360b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105861"
---
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="f4052-104">ASP.NET MVC ve ASP.NET Core arasındaki yönlendirme farklılıkları</span><span class="sxs-lookup"><span data-stu-id="f4052-104">Routing differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="f4052-105">Yönlendirme, gelen tarayıcı isteklerini belirli denetleyici eylemlerine (veya Razor Pages işleyicileriyle) eşleştirmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="f4052-105">Routing is responsible for mapping incoming browser requests to particular controller actions (or Razor Pages handlers).</span></span> <span data-ttu-id="f4052-106">Bu bölümde, yönlendirmenin ASP.NET MVC (ve Web API) ile ASP.NET Core (MVC, Razor Pages ve diğer durumlarda) arasında nasıl farklı olduğu ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4052-106">This section covers how routing differs between ASP.NET MVC (and Web API) and ASP.NET Core (MVC, Razor Pages, and otherwise).</span></span>

## <a name="routing-in-aspnet-mvc-and-web-api"></a><span data-ttu-id="f4052-107">ASP.NET MVC ve Web API 'de yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-107">Routing in ASP.NET MVC and Web API</span></span>

<span data-ttu-id="f4052-108">ASP.NET MVC, yönlendirmeye iki yaklaşım sunar:</span><span class="sxs-lookup"><span data-stu-id="f4052-108">ASP.NET MVC offers two approaches to routing:</span></span>

1. <span data-ttu-id="f4052-109">Gelen istekleri denetleyici eylemlerle eşleştirmek için kullanılabilen yolların bir koleksiyonu olan yol tablosu.</span><span class="sxs-lookup"><span data-stu-id="f4052-109">The route table, which is a collection of routes that can be used to match incoming requests to controller actions.</span></span>
1. <span data-ttu-id="f4052-110">Aynı işlevi gerçekleştiren, ancak genel bir yol tablosu düzenlemesi yerine eylemlerin kendileri dekorasyon olarak elde edilen öznitelik yönlendirme özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f4052-110">Attribute routing, which performs the same function but is achieved by decorating the actions themselves, rather than editing a global route table.</span></span>

## <a name="route-table"></a><span data-ttu-id="f4052-111">Yol tablosu</span><span class="sxs-lookup"><span data-stu-id="f4052-111">Route table</span></span>

<span data-ttu-id="f4052-112">Yol tablosu, uygulama başlatıldığında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="f4052-112">The route table is configured when the app starts up.</span></span> <span data-ttu-id="f4052-113">Genellikle, genel yol koleksiyonunu yapılandırmak için bir statik yöntem çağrısı kullanılır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="f4052-113">Typically, a static method call is used to configure the global route collection, like so:</span></span>

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

<span data-ttu-id="f4052-114">Yukarıdaki kodda yol tablosu, `RouteCollection` ile yeni rotalar eklemek için kullanılan türü tarafından yönetilir `MapRoute` .</span><span class="sxs-lookup"><span data-stu-id="f4052-114">In the preceding code, the route table is managed by the `RouteCollection` type, which is used to add new routes with `MapRoute`.</span></span> <span data-ttu-id="f4052-115">Yollar, ve denetleyiciler, Eylemler, bölgeler ve diğer yer tutucular için parametreleri içerebilen bir yol dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f4052-115">Routes are named and include a route string, which can include parameters for controllers, actions, areas, and other placeholders.</span></span> <span data-ttu-id="f4052-116">Bir uygulama standart bir kuralı izliyorsa, bu kural için ek rotalar kullanılarak yapılandırılmış özel durumlarla birlikte eylemlerinin büyük bir kısmının bu tek varsayılan yol tarafından işlenebilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4052-116">If an app follows a standard convention, most of its actions can be handled by this single default route, with any exceptions to this convention configured using additional routes.</span></span>

### <a name="attribute-routing-in-aspnet-mvc"></a><span data-ttu-id="f4052-117">ASP.NET MVC 'de öznitelik yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-117">Attribute routing in ASP.NET MVC</span></span>

<span data-ttu-id="f4052-118">Eylemleriyle tanımlanan yolların, bir dış konumda tanımlanan yolların keşfedilmesine ve nedenlerinden daha kolay bir şekilde tanımlanması daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4052-118">Routes that are defined with their actions may be easier to discover and reason about than routes defined in an external location.</span></span> <span data-ttu-id="f4052-119">Öznitelik yönlendirmeyi kullanarak, tek bir eylem yönteminin rotası bir öznitelikle tanımlanmış olabilir `[Route]` :</span><span class="sxs-lookup"><span data-stu-id="f4052-119">Using attribute routing, an individual action method can have its route defined with a `[Route]` attribute:</span></span>

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

<span data-ttu-id="f4052-120">[ASP.NET MVC 5 ' teki öznitelik yönlendirme özelliği](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) , denetleyici düzeyinde eklenebilen (ve bu denetleyici içindeki tüm eylemlere uygulanan) Varsayılanları ve önekleri de destekler.</span><span class="sxs-lookup"><span data-stu-id="f4052-120">[Attribute routing in ASP.NET MVC 5](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) also supports defaults and prefixes, which can be added at the controller level (and which are applied to all actions within that controller).</span></span> <span data-ttu-id="f4052-121">Ayrıntılar için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="f4052-121">Refer to the documentation for details.</span></span>

<span data-ttu-id="f4052-122">Öznitelik yönlendirmeyi ayarlama, varsayılan yol tablosu yapılandırmasına bir satır eklenmesini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f4052-122">Setting up attribute routing requires adding one line to the default route table configuration:</span></span>

```csharp
routes.MapMvcAttributeRoutes();
```

<span data-ttu-id="f4052-123">Öznitelik yönlendirme, hem yerleşik hem de özel yol kısıtlamalarından yararlanabilir ve özniteliği kullanılarak adlandırılmış yollar ve alanların kullanımını destekler `[RouteArea]` .</span><span class="sxs-lookup"><span data-stu-id="f4052-123">Attribute routing can take advantage of route constraints, both built-in and custom, and supports named routes and areas using the `[RouteArea]` attribute.</span></span> <span data-ttu-id="f4052-124">Uygulamanız alan kullanıyorsa, daha fazla satır ekleyerek rota kayıt kodunuzda bu şekilde destek yapılandırmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f4052-124">If your app uses areas, you'll need to configure support for them in your route registration code by adding one more line:</span></span>

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a><span data-ttu-id="f4052-125">ASP.NET Web API 2 ' de öznitelik yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-125">Attribute routing in ASP.NET Web API 2</span></span>

<span data-ttu-id="f4052-126">[ASP.NET Web API 2 ' de öznitelik yönlendirme](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) , küçük farklılıklar Ile ASP.NET MVC 5 ' teki yönlendirmeye benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f4052-126">[Attribute routing in ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) is similar to routing in ASP.NET MVC 5, with minor differences.</span></span> <span data-ttu-id="f4052-127">Web API 2 ' yi yapılandırma genellikle uygulama başlatma sırasında çağrılan kendi sınıfında yapılır.</span><span class="sxs-lookup"><span data-stu-id="f4052-127">Configuring Web API 2 is typically done in its own class, which is called during app startup.</span></span> <span data-ttu-id="f4052-128">Öznitelik Yönlendirme yapılandırması bu sınıfta işlenir:</span><span class="sxs-lookup"><span data-stu-id="f4052-128">Attribute routing configuration is handled in this class:</span></span>

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

<span data-ttu-id="f4052-129">Önceki kodda gösterildiği gibi, öznitelik yönlendirme Web API uygulamalarında kural tabanlı yönlendirme ile birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f4052-129">As shown in the preceding code, attribute routing may be combined with convention-based routing in Web API apps.</span></span>

<span data-ttu-id="f4052-130">Öznitelik yönlendirmeye ek olarak, [ASP.NET Web API 'SI](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) http yöntemine (ÖRNEĞIN, Get veya post), `{action}` bir yoldaki yer tutucuyu (varsa) ve eylemin parametrelerini temel alarak hangi eylemin çağrılacağını seçer.</span><span class="sxs-lookup"><span data-stu-id="f4052-130">In addition to attribute routing, [ASP.NET Web API chooses which action to call](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) based on the HTTP method (for example, GET or POST), the `{action}` placeholder in a route (if any), and parameters of the action.</span></span> <span data-ttu-id="f4052-131">Çoğu durumda, eylemin adı, ilgili HTTP yöntemiyle eşleşen "Get" veya "Post" ile eylem adının sonuna önek olarak kullanılmasından bağımsız olarak, eşleşip eşleşmediğine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f4052-131">In many cases, the name of the action will help determine whether it's matched, since prefixing the action name with "Get" or "Post" is used to match the appropriate HTTP method to it.</span></span> <span data-ttu-id="f4052-132">Alternatif olarak, eylemler gibi uygun bir HTTP yöntemi özniteliğiyle birlikte kullanılabilir ve `[HttpGet]` BIR http yöntemiyle ön eki olmayan eylem adlarının kullanılmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f4052-132">Alternatively, actions can be decorated with an appropriate HTTP method attribute, like `[HttpGet]`, allowing the use of action names that aren't prefixed with an HTTP method.</span></span>

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

<span data-ttu-id="f4052-133">Yukarıdaki denetleyici verildiğinde, eylemle eşleşen bir HTTP GET isteği `localhost:123/products/` `GetAll` .</span><span class="sxs-lookup"><span data-stu-id="f4052-133">Given the above controller, an HTTP GET request to `localhost:123/products/` matches the `GetAll` action.</span></span> <span data-ttu-id="f4052-134">Eylemle eşleşen bir HTTP GET isteği `localhost:123/products?name=ardalis` `FindProductsByName` .</span><span class="sxs-lookup"><span data-stu-id="f4052-134">An HTTP GET request to `localhost:123/products?name=ardalis` matches the `FindProductsByName` action.</span></span>

## <a name="routing-in-aspnet-core-31"></a><span data-ttu-id="f4052-135">ASP.NET Core 3,1 ' de yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-135">Routing in ASP.NET Core 3.1</span></span>

<span data-ttu-id="f4052-136">ASP.NET Core, yönlendirme, gelen isteklerin URL 'Leriyle eylemlere veya diğer uç noktalara eşleşen yönlendirme ara yazılımı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="f4052-136">In ASP.NET Core, routing is handled by routing middleware, which matches the URLs of incoming requests to actions or other endpoints.</span></span> <span data-ttu-id="f4052-137">Denetleyici eylemleri genel olarak yönlendirildi veya Attribute-yönlendirildi olarak atanır.</span><span class="sxs-lookup"><span data-stu-id="f4052-137">Controller actions are either conventionally routed or attribute-routed.</span></span> <span data-ttu-id="f4052-138">Geleneksel yönlendirme, ASP.NET MVC ve Web API 'sinde kullanılan yol tablosu yaklaşımına benzerdir.</span><span class="sxs-lookup"><span data-stu-id="f4052-138">Conventional routing is similar to the route table approach used in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="f4052-139">Geleneksel, öznitelik veya her ikisini de kullanıyorsanız, uygulamanızı yönlendirme ara yazılımını kullanacak şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4052-139">Whether you're using conventional, attribute, or both, you need to configure your app to use the routing middleware.</span></span> <span data-ttu-id="f4052-140">Ara yazılımı kullanmak için aşağıdaki kodu yönteminizin içine ekleyin `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="f4052-140">To use the middleware, add the following code to your `Startup.Configure` method:</span></span>

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a><span data-ttu-id="f4052-141">Geleneksel yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-141">Conventional routing</span></span>

<span data-ttu-id="f4052-142">Geleneksel yönlendirme ile, gelen URL 'Leri uygulamadaki *uç noktalarla* eşleştirmek için kullanılacak bir veya daha fazla kural ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="f4052-142">With conventional routing, you set up one or more conventions that will be used to match incoming URLs to *endpoints* in the app.</span></span> <span data-ttu-id="f4052-143">ASP.NET Core, bu uç noktalar ASP.NET MVC veya Web API 'SI gibi denetleyici eylemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4052-143">In ASP.NET Core, these endpoints may be controller actions, like in ASP.NET MVC or Web API.</span></span> <span data-ttu-id="f4052-144">Uç noktalar Ayrıca Razor Pages, sistem durumu denetimleri veya SignalR hub 'ları olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4052-144">The endpoints could also be Razor Pages, Health Checks, or SignalR hubs.</span></span> <span data-ttu-id="f4052-145">Bu yönlendirilebilir özelliklerin tümü uç noktalar kullanılarak benzer bir biçimde yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="f4052-145">All of these routable features are configured in a similar fashion using endpoints:</span></span>

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

<span data-ttu-id="f4052-146">Yukarıdaki kod, `UseRouting` sistem durumu denetimleri, denetleyiciler ve Razor Pages dahil olmak üzere çeşitli uç noktaları yapılandırmak için kullanılır (Buna ek olarak).</span><span class="sxs-lookup"><span data-stu-id="f4052-146">The preceding code is used (in addition to `UseRouting`) to configure various endpoints, including Health Checks, controllers, and Razor Pages.</span></span> <span data-ttu-id="f4052-147">Denetleyiciler için yukarıdaki yapılandırma, `{controller}/{action}/{id?}` ASP.NET MVC 'nin ilk sürümlerinden beri önerilen oldukça standart bir model olan varsayılan bir yönlendirme kuralı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4052-147">For controllers, the above configuration specifies a default routing convention, which is the fairly standard `{controller}/{action}/{id?}` pattern that's been recommended since the first versions of ASP.NET MVC.</span></span>

### <a name="attribute-routing"></a><span data-ttu-id="f4052-148">Öznitelik yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-148">Attribute routing</span></span>

<span data-ttu-id="f4052-149">ASP.NET Core öznitelik yönlendirme, denetleyicilerde yönlendirmeyi yapılandırmak için tercih edilen yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="f4052-149">Attribute routing in ASP.NET Core is the preferred approach for configuring routing in controllers.</span></span> <span data-ttu-id="f4052-150">API 'Ler oluşturuyorsanız, bu `[ApiController]` öznitelik denetleyicilerinize uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4052-150">If you're building APIs, the `[ApiController]` attribute should be applied to your controllers.</span></span> <span data-ttu-id="f4052-151">Diğer şeyler arasında bu öznitelik, bu tür denetleyici sınıflarında eylemler için öznitelik yönlendirmenin kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f4052-151">Among other things, this attribute requires the use of attribute routing for actions in such controller classes.</span></span>

<span data-ttu-id="f4052-152">ASP.NET Core öznitelik yönlendirme ASP.NET MVC ve Web API 'sinde benzer şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="f4052-152">Attribute routing in ASP.NET Core behaves similarly in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="f4052-153">Ancak, özniteliği desteklemeye ek olarak `[Route]` , yönlendirme bilgileri de http yöntemi özniteliğinin bir parçası olarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="f4052-153">In addition to supporting the `[Route]` attribute, however, route information can also be specified as part of the HTTP method attribute:</span></span>

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

<span data-ttu-id="f4052-154">Önceki sürümlerde olduğu gibi, yer tutucular içeren bir varsayılan yol belirtebilir ve bunu denetleyici sınıfı düzeyine ya da bir temel sınıfa ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4052-154">As with previous versions, you can specify a default route with placeholders, and add this at the controller class level or even on a base class.</span></span> <span data-ttu-id="f4052-155">`[Route]`Tüm bu durumlar için aynı özniteliği kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f4052-155">You use the same `[Route]` attribute for all of these cases.</span></span> <span data-ttu-id="f4052-156">Örneğin, bir temel API denetleyici sınıfı şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="f4052-156">For example, a base API controller class might look like this:</span></span>

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

<span data-ttu-id="f4052-157">Bu özniteliği kullanarak, bu türden devralan sınıflar, denetleyici adı, eylem adı ve isteğe bağlı bir tamsayı parametresine göre URL 'Leri eylemlere yönlendirir `id` .</span><span class="sxs-lookup"><span data-stu-id="f4052-157">Using this attribute, classes inheriting from this type would route URLs to actions based on the controller name, action name, and an optional integer `id` parameter.</span></span>

## <a name="references"></a><span data-ttu-id="f4052-158">Başvurular</span><span class="sxs-lookup"><span data-stu-id="f4052-158">References</span></span>

- [<span data-ttu-id="f4052-159">ASP.NET MVC yönlendirmeye genel bakış</span><span class="sxs-lookup"><span data-stu-id="f4052-159">ASP.NET MVC Routing Overview</span></span>](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [<span data-ttu-id="f4052-160">ASP.NET MVC 5 içinde öznitelik yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-160">Attribute Routing in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [<span data-ttu-id="f4052-161">ASP.NET Web API 2 ' de öznitelik yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-161">Attribute routing in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [<span data-ttu-id="f4052-162">ASP.NET Web API 'sinde yönlendirme ve eylem seçimi</span><span class="sxs-lookup"><span data-stu-id="f4052-162">Routing and Action Selection in ASP.NET Web API</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [<span data-ttu-id="f4052-163">ASP.NET Core yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-163">Routing in ASP.NET Core</span></span>](/aspnet/core/fundamentals/routing)
- [<span data-ttu-id="f4052-164">ASP.NET Core MVC 'de denetleyici eylemlerine yönlendirme</span><span class="sxs-lookup"><span data-stu-id="f4052-164">Routing to controller actions in ASP.NET Core MVC</span></span>](/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
><span data-ttu-id="f4052-165">[Önceki](configuration-differences.md) 
> [Sonraki](comparing-razor-pages-aspnet-mvc.md)</span><span class="sxs-lookup"><span data-stu-id="f4052-165">[Previous](configuration-differences.md)
[Next](comparing-razor-pages-aspnet-mvc.md)</span></span>
