---
title: Ara yazılımı modüller ve işleyicilerle karşılaştırın
description: Bu bölüm, istek işleme ardışık düzenleri için ara yazılımı tanımlayan ASP.NET Core uygulamalarla işleyicileri ve modülleri kullanan ASP.NET uygulamaları için yapı farklarını ele alırlar.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3bc3c30a1ee988550cca907d7289583161337cb9
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122878"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="25f2d-103">Ara yazılımı modüller ve işleyicilerle karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="25f2d-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="25f2d-104">Mevcut ASP.NET MVC veya Web API uygulamanız OWıN/Katana kullanıyorsa, en büyük olasılıkla ara yazılım kavramı hakkında bilgi sahibi olduğunuz ASP.NET Core oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="25f2d-105">Ancak, çoğu ASP.NET uygulaması, ara yazılım yerine HTTP modüllerine ve HTTP işleyicileriyle yararlanır.</span><span class="sxs-lookup"><span data-stu-id="25f2d-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="25f2d-106">Bunları ASP.NET Core geçirmek için ek çaba gerekir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="25f2d-107">ASP.NET modülleri ve işleyicileri</span><span class="sxs-lookup"><span data-stu-id="25f2d-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="25f2d-108">[Http modülleri ve http işleyicileri](/troubleshoot/aspnet/http-modules-handlers) , ASP.NET mimarisinin ayrılmaz bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="25f2d-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="25f2d-109">İstek işlenirken, her istek birden çok HTTP modülü tarafından işlenir (örneğin, kimlik doğrulama modülü ve oturum modülü) ve ardından tek bir HTTP işleyici tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="25f2d-110">İşleyici isteği işledikten sonra, istek HTTP modülleri üzerinden geri akar.</span><span class="sxs-lookup"><span data-stu-id="25f2d-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="25f2d-111">Uygulamanız özel HTTP modülleri veya HTTP işleyicileri kullanıyorsa, bunları ASP.NET Core geçirme planına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="25f2d-112">ASP.NET Core en olası değişikliği ara yazılımlar.</span><span class="sxs-lookup"><span data-stu-id="25f2d-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="25f2d-113">ASP.NET Core ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="25f2d-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="25f2d-114">ASP.NET Core her uygulamanın yönteminde bir istek işlem hattı tanımlar `Configure` .</span><span class="sxs-lookup"><span data-stu-id="25f2d-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="25f2d-115">Bu istek ardışık düzeni, bir gelen isteğin uygulama tarafından nasıl işlendiğini tanımlar. işlem hattının her bir yöntemi, bir yöntem sonlanana kadar bir sonraki yöntemi çağırır ve *Ara yazılım* zinciri sonlandırıldığında ve yığın geri döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="25f2d-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="25f2d-116">Ara yazılım tüm istekleri hedefleyebilir veya yalnızca istenen yola veya diğer faktörlere bağlı olarak belirli isteklere eşlenecek şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="25f2d-117">`Configure`Uygulama yönteminde tamamen veya ayrı bir sınıfta uygulanan şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="25f2d-118">HTTP modüllerini kullanan bir ASP.NET MVC uygulamasındaki davranış, büyük olasılıkla [özel ara yazılım](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)için en uygun seçenektir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="25f2d-119">Özel HTTP işleyicileri, aynı yola yanıt veren özel rotalar veya uç noktalar ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="accessing-httpcontext"></a><span data-ttu-id="25f2d-120">HttpContext 'e erişme</span><span class="sxs-lookup"><span data-stu-id="25f2d-120">Accessing HttpContext</span></span>

<span data-ttu-id="25f2d-121">Birçok .NET uygulaması, geçerli isteğin bağlamına ile başvurur `HttpContext.Current` .</span><span class="sxs-lookup"><span data-stu-id="25f2d-121">Many .NET apps reference the current request's context through `HttpContext.Current`.</span></span> <span data-ttu-id="25f2d-122">Bu statik erişim, bireysel isteklerin dışındaki test ve diğer kod kullanımıyla ilgili yaygın bir sorun kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25f2d-122">This static access can be a common source of problems with testing and other code usage outside of individual requests.</span></span> <span data-ttu-id="25f2d-123">ASP.NET Core uygulamalar oluştururken, geçerli HttpContext 'e erişim, bu örnekte gösterildiği gibi, ara yazılım üzerinde yöntem parametresi olarak sağlanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="25f2d-123">When building ASP.NET Core apps, access to the current HttpContext should be provided as a method parameter on middleware, as this sample demonstrates:</span></span>

```csharp
public class Middleware
{
    private readonly RequestDelegate _next;

    public Middleware(RequestDelegate next)
    {
        _next = next;
    }

    public Task Invoke(HttpContext httpContext)
    {
        return _next(httpContext);
    }
}
```

<span data-ttu-id="25f2d-124">Benzer şekilde, ASP.NET Core filtreler, geçerli HttpContext 'in erişebileceği yöntemlerine bir bağlam bağımsız değişkeni iletir:</span><span class="sxs-lookup"><span data-stu-id="25f2d-124">Similarly, ASP.NET Core filters pass a context argument to their methods, from which the current HttpContext can be accessed:</span></span>

```csharp
public class MyActionFilterAttribute : ActionFilterAttribute
{
    public override void OnResultExecuting(ResultExecutingContext context)
    {
        var headers = context.HttpContext.Request.Headers;
        // do something based on a header

        base.OnResultExecuting(context);
    }
}
```

<span data-ttu-id="25f2d-125">Bir statik çağrı kullanmak yerine HttpContext 'e erişim gerektiren bileşenleriniz veya hizmetleriniz varsa, `HttpContext.Current` bunun yerine Oluşturucu bağımlılığı ekleme ve [ıhttpcontextaccessor](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) arabirimini kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="25f2d-125">If you have components or services that require access to HttpContext, rather than using a static call like `HttpContext.Current` you should instead use constructor dependency injection and the [IHttpContextAccessor](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) interface:</span></span>

```csharp
public class MyService
{
    private readonly IHttpContextAccessor _httpContextAccessor;

    public MyService(IHttpContextAccessor httpContextAccessor)
    {
        _httpContextAccessor = httpContextAccessor;
    }

    public void DoSomething()
    {
        var currentContext = _httpContextAccessor.HttpContext;
    }
}
```

<span data-ttu-id="25f2d-126">Bu yaklaşım, bir şekilde erişim sağlarken, geçerli bağlam için yöntemin statik eşlenmesini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="25f2d-126">This approach eliminates the static coupling of the method to the current context while providing access in a testable fashion.</span></span>

## <a name="references"></a><span data-ttu-id="25f2d-127">Başvurular</span><span class="sxs-lookup"><span data-stu-id="25f2d-127">References</span></span>

- [<span data-ttu-id="25f2d-128">ASP.NET HTTP modülleri ve HTTP işleyicileri</span><span class="sxs-lookup"><span data-stu-id="25f2d-128">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="25f2d-129">ASP.NET Core ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="25f2d-129">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="25f2d-130">[Önceki](dependency-injection-differences.md) 
> [Sonraki](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="25f2d-130">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
