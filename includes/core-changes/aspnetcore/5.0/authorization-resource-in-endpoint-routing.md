---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441562"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>Yetkilendirme: uç nokta yönlendirmesinde kaynak HttpContext 'dir

ASP.NET Core 3,1 ' de Endpoint Routing kullanılırken, yetkilendirme için kullanılan kaynak uç noktasıdır. Bu yaklaşım, yol verilerine () erişim kazanmak için yeterli değildi <xref:Microsoft.AspNetCore.Routing.RouteData> . Daha önce MVC 'de, <xref:Microsoft.AspNetCore.Http.HttpContext> hem uç nokta () hem de yol verilerine erişim sağlayan bir kaynak geçirildi <xref:Microsoft.AspNetCore.Http.Endpoint> . Bu değişiklik, yetkilendirmeye geçirilen kaynağın her zaman ' i olmasını sağlar `HttpContext` .

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 7

#### <a name="old-behavior"></a>Eski davranış

Endpoint Routing ve yetkilendirme ara yazılımı ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) veya [[Yetkilendir]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) öznitelikleri kullanılırken, yetkilendirme öğesine geçirilen kaynak eşleşen uç noktadır.

#### <a name="new-behavior"></a>Yeni davranış

Endpoint Routing, ' i `HttpContext` Yetkilendirmeyi geçirir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Uç noktasına öğesinden ulaşabilirsiniz `HttpContext` . Ancak, uç noktadan yol verileri gibi şeylere kadar bir yöntem yoktu. Uç nokta olmayan yönlendirmenin işlevselliğinde bir kayıp vardı.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız uç nokta kaynağını kullanıyorsa, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` uç noktaya erişmeye devam etmek için üzerinde öğesini çağırın.

ASP.NET Core 5,0 Preview 8 ve üzeri sürümlerde, ile eski davranışa dönüştürebilirsiniz <xref:System.AppContext.SetSwitch%2A> . Örneğin:

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Hiçbiri

<!--

#### Affected APIs

Not detectable via API analysis

-->
