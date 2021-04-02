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
# <a name="compare-middleware-to-modules-and-handlers"></a>Ara yazılımı modüller ve işleyicilerle karşılaştırın

Mevcut ASP.NET MVC veya Web API uygulamanız OWıN/Katana kullanıyorsa, en büyük olasılıkla ara yazılım kavramı hakkında bilgi sahibi olduğunuz ASP.NET Core oldukça basittir. Ancak, çoğu ASP.NET uygulaması, ara yazılım yerine HTTP modüllerine ve HTTP işleyicileriyle yararlanır. Bunları ASP.NET Core geçirmek için ek çaba gerekir.

## <a name="aspnet-modules-and-handlers"></a>ASP.NET modülleri ve işleyicileri

[Http modülleri ve http işleyicileri](/troubleshoot/aspnet/http-modules-handlers) , ASP.NET mimarisinin ayrılmaz bir parçasıdır. İstek işlenirken, her istek birden çok HTTP modülü tarafından işlenir (örneğin, kimlik doğrulama modülü ve oturum modülü) ve ardından tek bir HTTP işleyici tarafından işlenir. İşleyici isteği işledikten sonra, istek HTTP modülleri üzerinden geri akar.

Uygulamanız özel HTTP modülleri veya HTTP işleyicileri kullanıyorsa, bunları ASP.NET Core geçirme planına sahip olmanız gerekir. ASP.NET Core en olası değişikliği ara yazılımlar.

## <a name="aspnet-core-middleware"></a>ASP.NET Core ara yazılımı

ASP.NET Core her uygulamanın yönteminde bir istek işlem hattı tanımlar `Configure` . Bu istek ardışık düzeni, bir gelen isteğin uygulama tarafından nasıl işlendiğini tanımlar. işlem hattının her bir yöntemi, bir yöntem sonlanana kadar bir sonraki yöntemi çağırır ve *Ara yazılım* zinciri sonlandırıldığında ve yığın geri döndürüyor. Ara yazılım tüm istekleri hedefleyebilir veya yalnızca istenen yola veya diğer faktörlere bağlı olarak belirli isteklere eşlenecek şekilde yapılandırılabilir. `Configure`Uygulama yönteminde tamamen veya ayrı bir sınıfta uygulanan şekilde yapılandırılabilir.

HTTP modüllerini kullanan bir ASP.NET MVC uygulamasındaki davranış, büyük olasılıkla [özel ara yazılım](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)için en uygun seçenektir. Özel HTTP işleyicileri, aynı yola yanıt veren özel rotalar veya uç noktalar ile değiştirilebilir.

## <a name="accessing-httpcontext"></a>HttpContext 'e erişme

Birçok .NET uygulaması, geçerli isteğin bağlamına ile başvurur `HttpContext.Current` . Bu statik erişim, bireysel isteklerin dışındaki test ve diğer kod kullanımıyla ilgili yaygın bir sorun kaynağı olabilir. ASP.NET Core uygulamalar oluştururken, geçerli HttpContext 'e erişim, bu örnekte gösterildiği gibi, ara yazılım üzerinde yöntem parametresi olarak sağlanmalıdır:

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

Benzer şekilde, ASP.NET Core filtreler, geçerli HttpContext 'in erişebileceği yöntemlerine bir bağlam bağımsız değişkeni iletir:

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

Bir statik çağrı kullanmak yerine HttpContext 'e erişim gerektiren bileşenleriniz veya hizmetleriniz varsa, `HttpContext.Current` bunun yerine Oluşturucu bağımlılığı ekleme ve [ıhttpcontextaccessor](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.http.ihttpcontextaccessor) arabirimini kullanmanız gerekir:

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

Bu yaklaşım, bir şekilde erişim sağlarken, geçerli bağlam için yöntemin statik eşlenmesini ortadan kaldırır.

## <a name="references"></a>Başvurular

- [ASP.NET HTTP modülleri ve HTTP işleyicileri](/troubleshoot/aspnet/http-modules-handlers)
- [ASP.NET Core ara yazılımı](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
>[Önceki](dependency-injection-differences.md) 
> [Sonraki](configuration-differences.md)
