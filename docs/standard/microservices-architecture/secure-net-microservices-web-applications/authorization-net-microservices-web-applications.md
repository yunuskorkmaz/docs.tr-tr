---
title: .NET mikro ve web uygulamaları hakkında yetkilendirme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET mikro ve web uygulamaları hakkında yetkilendirme
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2ea56f5a28d115fc5d91a98604b82565c8bf5c78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582827"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET mikro ve web uygulamaları hakkında yetkilendirme

Kimlik doğrulamasından sonra ASP.NET çekirdek Web API'lerine erişim yetkisi vermek gerekir. Bu işlem, bazı kimliği doğrulanmış kullanıcılar için kullanılabilir, ancak değil tüm API'leri yapmak bir hizmet sağlar. [Yetkilendirme](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) kullanıcıların rollerini tabanlı Bitti veya, talep veya diğer buluşsal yöntemler inceleniyor içerebilen özel ilkesini temel alarak.

Bir Authorize özniteliği eylem yöntemine (veya denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa denetleyicinin sınıf), aşağıdaki gösterildiği örnek olarak uygulama olarak, bir ASP.NET Core MVC rotaya erişimi kısıtlama kadar kolaydır:

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

Varsayılan olarak, parametresiz bir Authorize özniteliği eklemek, denetleyici veya eylem için kimliği doğrulanmış kullanıcılara erişimi sınırlar. Daha fazla yalnızca belirli kullanıcılar için kullanılabilir olması için bir API kısıtlamak için özniteliği gerekli rolleri veya kullanıcıların getirmelidir ilkeleri belirtmek için genişletilebilir.

## <a name="implementing-role-based-authorization"></a>Rol tabanlı yetkilendirme uygulama

ASP.NET Core kimliği rolleri yerleşik bir kavramı vardır. Kullanıcılar, ek olarak ASP.NET Core kimliği uygulama tarafından kullanılan farklı rolleri hakkında bilgi depolar ve hangi kullanıcıların hangi rollerine atanan izler. Bu atamaları RoleManager türü (olan kalıcı depolama rollerinde güncelleştirmeleri) ve (atayabilir veya rolleri kullanıcılardan atamasını) UserManager türü ile programlı olarak değiştirilebilir.

JWT taşıyıcı belirteçleri ile kimlik doğrulaması, ASP.NET Core JWT taşıyıcı kimlik doğrulaması ara yazılımı belirteç bulundu rol talepleri dayalı bir kullanıcının rollerini doldurur. Bir MVC eylem veya denetleyici belirli roller kullanıcılara erişimi sınırlamak için bir rol parametresi Authorize üstbilgisinde aşağıdaki örnekte gösterildiği gibi içerebilir:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

Bu örnekte, (örneğin SetTime eylemi yürütürken) ControlPanel denetleyicideki API'leri yalnızca yönetici veya PowerUser rollerdeki kullanıcılar erişebilir. Kapatma API yönetici rolünde kullanıcılar yalnızca erişmesine izin vermek için daha fazla sınırlıdır.

Bir kullanıcının birden çok rollerinde olması zorunlu kılmak için aşağıdaki örnekte gösterildiği gibi birden çok Authorize öznitelik kullanın:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Bu örnekte, API1, çağırmak için bir kullanıcı gerekir:

-   Yönetici olması *veya* PowerUser rol *ve*

-   RemoteEmployee rolünde olması *ve*

-   CustomPolicy yetkilendirme için özel bir işleyici karşılar.

## <a name="implementing-policy-based-authorization"></a>İlke tabanlı bir yetkilendirme uygulama

Özel Yetkilendirme kuralları da yazılabilir kullanarak [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html). Bu bölümde genel bir bakış sağlar. Daha ayrıntılı çevrimiçi olarak kullanılabilir [ASP.NET yetkilendirme Atölye](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Özel yetkilendirme ilkeleri kullanarak hizmet Startup.ConfigureServices yönteminde kaydedilir. AddAuthorization yöntemi. Bu yöntem AuthorizationOptions bağımsız değişken yapılandırır bir temsilciyi alır.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));
    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));
    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

Örnekte gösterildiği gibi ilkeleri farklı gereksinimleri türleri ile ilişkili olabilir. İlkeleri kaydedildikten sonra bunlar bir eylem veya denetleyici ilkenin adı Authorize özniteliği ilke bağımsız değişken olarak geçirerek uygulanabilir (örneğin, \[Authorize(Policy="EmployeesOnly")\]) İlkeleri olabilir birden çok gereksinimleri, yalnızca bir tane değil (Bu örneklerde gösterildiği gibi).

Önceki örnekte, ilk AddPolicy çağrı role göre yetkilendirme sadece bir alternatif yoludur. Varsa \[Authorize(Policy="AdministratorsOnly")\] Yönetici rolü kullanıcılar buna erişebilir yalnızca bir API için uygulanır.

İkinci AddPolicy çağrı kullanıcı için belirli bir talep bulunmalı istemek için kolay bir yol gösterir. RequireClaim yöntemi ayrıca isteğe bağlı olarak talep beklenen değerlerini alır. Değerleri belirtilirse, yalnızca kullanıcının hem doğru türde bir talep ve belirtilen değerlerden biri varsa bu gereksinimi karşılarsınız. JWT taşıyıcı kimlik doğrulaması ara yazılımı kullanıyorsanız, kullanıcı talepleri tüm JWT özellikleri kullanılabilir.

Özel yetkilendirme gereksinimi kullandığından burada gösterilen en ilginç üçüncü AddPolicy yönteminde ilkesidir. Özel yetkilendirme gereksinimleri kullanarak, büyük bir bölümünü yetkilendirme nasıl gerçekleştirildiğini üzerinde denetime sahip olabilir. Bunun çalışması için bu tür uygulamanız gerekir:

-   IAuthorizationRequirement türetilen ve alanları gereksinim ayrıntılarını belirtme içeren gereksinimleri türü. Örnekte, bu yaş örnek MinimumAgeRequirement türü için bir alandır.

-   AuthorizationHandler uygulayan bir işleyici&lt;T&gt;, burada T işleyici karşılayabilen IAuthorizationRequirement türüdür. İşleyici kullanıcı hakkındaki bilgileri içeren belirtilen bir bağlam gereksinimini karşılayıp karşılamadığını denetler HandleRequirementAsync yöntemi uygulamalıdır.

Kullanıcı bağlamı için bir çağrı gereksinimi karşılıyorsa. İşlem başarılı kullanıcı yetkili olduğunu gösterir. Bir kullanıcı bir kimlik doğrulama gereksinimini karşılayan birden çok yol varsa, birden çok işleyici oluşturulabilir.

Özel ilke gereksinimlerini AddPolicy aramaları kaydetmeye ek olarak, ayrıca özel gereksinim işleyicilerini bağımlılık ekleme (Hizmetleri. aracılığıyla kaydetmesine izin gerekir AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Özel yetkilendirme gereksinimi ve (DateOfBirth talebe göre) kullanıcının yaş denetleme işleyici örneği ASP.NET çekirdek kullanılabilir [yetkilendirme belgelerine](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Ek kaynaklar

-   **ASP.NET Core kimlik doğrulaması**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **ASP.NET Core yetkilendirme**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Rol tabanlı yetkilendirme**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Özel ilke tabanlı yetkilendirme**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (Geliştirici-app-gizli-storage.md)
