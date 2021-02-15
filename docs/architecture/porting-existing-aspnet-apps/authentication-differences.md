---
title: ASP.NET MVC ve ASP.NET Core arasındaki kimlik doğrulama ve yetkilendirmeyi karşılaştırın
description: ASP.NET MVC ve ASP.NET Core arasındaki kimlik doğrulama ve yetkilendirme farklılıkları Özeti.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: fd8c11290a296612af822dd6c1a7816f915f09f7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488925"
---
# <a name="compare-authentication-and-authorization-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki kimlik doğrulama ve yetkilendirmeyi karşılaştırın

ASP.NET MVC 5 ' te, kimlik doğrulaması *App_Start* klasöründe *Startup.auth.cs* ' de yapılandırılır. ASP.NET Core MVC 'de bu yapılandırma içinde oluşur `Startup.cs` . Kimlik doğrulama ve yetkilendirme, içindeki istek ardışık düzenine eklenen ara yazılımlar kullanılarak gerçekleştirilir `ConfigureServices` :

```csharp
// inside Startup.ConfigureServices

app.UseRouting();

app.UseAuthentication();
app.UseAuthorization();

app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

Kimlik doğrulama ara yazılımını, ara yazılım ardışık düzeninde uygun bir sıraya eklemek önemlidir. Yalnızca bu uygulamayı ara yazılım için yapan istekler bundan etkilenir. Örneğin, öğesine yapılan bir çağrı `UseStaticFiles()` burada gösterilen kodun üstüne yerleştirilmişse, kimlik doğrulama ve yetkilendirme tarafından korunmaz.

ASP.NET MVC ve Web API 'sinde, uygulamalar genellikle özelliğini kullanarak geçerli kullanıcıya başvurur `ClaimsPrincipal.Current` . Bu özellik ASP.NET Core ayarlanmamış ve uygulamanızdaki herhangi bir davranış, [](https://docs.microsoft.com/aspnet/core/migration/claimsprincipal-current) `User` üzerinde özelliğini kullanarak `ControllerBase` veya geçerli olan `HttpContext` ve `User` özelliğine başvurarak ClaimsPrincipal. Current öğesinden geçiş yapmak zorunda olacaktır. Bu çözümlerin hiçbiri bir seçenek değilse, hizmetler kullanıcıyı bir bağımsız değişken olarak talep edebilir, bu durumda uygulamanın başka bir yerinde sağlanması gerekir ya da `IHttpContextAccessor` istenebilir ve ' ı almak için kullanılabilir `HttpContext` .

## <a name="authorization"></a>Yetkilendirme

Yetkilendirme, belirli bir kullanıcının uygulama içinde neler yapabileceğini tanımlar. Yalnızca kullanıcının kim olduğunu tanımlayarak ilgili olan kimlik doğrulamasından ayrıdır. ASP.NET Core, yetkilendirme için basit, bildirime dayalı bir rol ve zengin, ilke tabanlı bir model sağlar. Bir kaynağın yetkilendirme gerektirdiğini belirtmek, `[Authorize]` özniteliği eyleme veya denetleyiciye eklemek kadar basittir. MVC görünümlerinden Razor Pages geçiş yapıyorsanız, [başlangıçta Razor Pages yapılandırdığınızda yetkilendirme kurallarını belirtmeniz](https://docs.microsoft.com/aspnet/core/security/authorization/razor-pages-authorization)gerekir.

ASP.NET Core yetkilendirme, anonim kullanıcıları yalarken kimlik doğrulamalı kullanıcılara izin verirken basit olabilir. Ya da rol tabanlı, talep tabanlı ya da ilke tabanlı yetkilendirme yaklaşımlarını destekleyecek şekilde ölçeklendirebilir. Bu yaklaşımlar hakkında daha fazla bilgi için [ASP.NET Core 'de yetkilendirme](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)ile ilgili belgelere bakın. Büyük olasılıkla, bunlardan birinin geçerli yetkilendirme yaklaşımınız ile yakından hizalandığını fark edeceksiniz.

## <a name="references"></a>Başvurular

- [ASP.NET MVC ile güvenlik, kimlik doğrulama ve yetkilendirme](https://docs.microsoft.com/aspnet/mvc/overview/security/)
- [Kimlik doğrulaması ve kimliği ASP.NET Core geçir](https://docs.microsoft.com/aspnet/mvc/overview/security/)
- [ClaimsPrincipal. Current öğesinden geçir](https://docs.microsoft.com/aspnet/core/migration/claimsprincipal-current)
- [ASP.NET Core yetkilendirme için giriş](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

>[!div class="step-by-step"]
>[Önceki](webapi-differences.md) 
> [Sonraki](identity-differences.md)
