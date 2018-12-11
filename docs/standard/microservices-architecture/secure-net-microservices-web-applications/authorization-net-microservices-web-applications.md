---
title: .NET mikro Hizmetleri ve web uygulamalarında yetkilendirme hakkında
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET mikro Hizmetleri ve web uygulamalarında yetkilendirme hakkında
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 53202d0f890df040480b9f54c54aaefdd025dffa
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149572"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET mikro Hizmetleri ve web uygulamalarında yetkilendirme hakkında

Kimlik doğrulamasından sonra ASP.NET Core Web API'lerine erişim yetkisi vermek gerekir. Bu işlem, bazı kimliği doğrulanmış kullanıcılar tarafından kullanılabilir, ancak çok tüm API'leri yapmak bir hizmet sağlar. [Yetkilendirme](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) kullanıcıların rollere göre Bitti veya talep veya diğer buluşsal yöntemler inceleyerek içerebilir özel ilkesini temel alarak.

Bir Authorize özniteliği eylem yöntemine (veya denetleyicinin sınıf denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa), aşağıdaki gösterildiği örnek olarak uygulama olarak, bir ASP.NET Core MVC yönlendirme için erişimi kısıtlamak oldukça kolaydır:

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

Varsayılan olarak, parametresiz bir Authorize öznitelik ekleyerek bu denetleyici veya eylem için kimliği doğrulanmış kullanıcılara erişimi sınırlar. Yalnızca belirli kullanıcılar için kullanılabilir olması için bir API daha da kısıtlamak için özniteliği gerekli rolleri veya kullanıcıları karşılamalıdır ilkeleri belirtmek için genişletilebilir.

## <a name="implementing-role-based-authorization"></a>Rol tabanlı yetkilendirme uygulama

ASP.NET Core kimliği yerleşik bir rol kavramları vardır. Kullanıcıların, yanı sıra ASP.NET Core kimliği uygulama tarafından kullanılan farklı roller hakkındaki bilgileri saklar ve hangi kullanıcıların hangi rollerine atandığı izler. Bu atamaları (Bu rollerdeki kalıcı depolama güncelleştirmeleri) RoleManager tür ve (hangi atayabilir veya kullanıcıların rol atamasını) UserManager türü ile programlı olarak değiştirilebilir.

ASP.NET Core JWT taşıyıcı kimlik doğrulaması ara yazılımı, JWT taşıyıcı belirteçleri ile kimlik doğrulaması, rol talepleri belirteçte göre bir kullanıcının rollerini doldurur. Bir MVC eylem veya denetleyici belirli roller kullanıcılara erişimi sınırlamak için bir rol parametresi Authorize üst bilgisinde, aşağıdaki örnekte gösterildiği gibi ekleyebilirsiniz:

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

Bu örnekte, yalnızca yönetici veya PowerUser rollerdeki kullanıcılar (örneğin SetTime eylemini yürütürken) ndaki denetleyici API'leri erişebilirsiniz. ShutDown API, yönetici rolünde yalnızca kullanıcı erişimine izin vermek için daha fazla sınırlıdır.

Bir kullanıcı birden çok rol içinde olması gerekir için birden çok Authorize özniteliği aşağıdaki örnekte gösterildiği gibi kullanın:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Bu örnekte, bir kullanıcı API1, çağrılacak gerekir:

-   İçinde Yöneticisi olması *veya* PowerUser rol *ve*

-   RemoteEmployee rolünde olması *ve*

-   CustomPolicy yetkilendirme için özel bir işleyici karşılar.

## <a name="implementing-policy-based-authorization"></a>İlke tabanlı yetkilendirme uygulama

Özel Yetkilendirme kuralları da yazılabilir kullanarak [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html). Bu bölümde genel bir bakış sunuyoruz. Daha ayrıntılı çevrimiçi kullanılabilir [ASP.NET yetkilendirme Atölyesi](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Özel Yetkilendirme İlkeleri Startup.ConfigureServices yöntemin hizmeti kullanılarak kaydedilir. AddAuthorization yöntemi. Bu yöntem AuthorizationOptions bağımsız değişken yapılandıran bir temsilciyi alır.

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

Örnekte gösterildiği gibi ilkeleri farklı gereksinimleri ile ilişkilendirilebilir. İlkeleri kaydolduktan sonra bir eylem veya denetleyici Authorize özniteliği ilke bağımsız değişkeni bir ilkenin adını geçirerek uygulanabilirler (örneğin, \[Authorize(Policy="EmployeesOnly")\]) ilkelerine sahip olabilir birden fazla gereksinimi, yalnızca bir tane değil (Bu örneklerde gösterildiği gibi).

Önceki örnekte, ilk AddPolicy çağrı role göre yetkilendirme yalnızca bir diğer yoludur. Varsa \[Authorize(Policy="AdministratorsOnly")\] yönetici rolündeki kullanıcılar erişebilmesi için yalnızca bir API için uygulanır.

AddPolicy yapılan ikinci çağrı, belirli bir talep kullanıcı için mevcut olduğunu istemek için kolay bir yolunu gösterir. RequireClaim yöntem Ayrıca isteğe bağlı olarak talep için beklenen değerleri alır. Değer belirtilmişse, yalnızca kullanıcının hem doğru türde bir talep ve belirtilen değerlerden biri varsa bu gereksinimi karşılarsınız. JWT taşıyıcı kimlik doğrulaması ara yazılımı kullanıyorsanız, kullanıcı talepleri tüm JWT özellikleri kullanılabilir.

Özel yetkilendirme gereksinimi kullandığından burada gösterilen en ilginç üçüncü AddPolicy yönteminde ilkedir. Özel yetkilendirme gereksinimleri kullanarak Yetkilendirme nasıl gerçekleştirildiğini denetim harika bir fırsat olabilir. Bunun çalışması için bu tür uygulamanız gerekir:

-   IAuthorizationRequirement türetilen ve gereksinim ayrıntıları belirten alanlar içeren gereksinimleri türü. Örnekte, örnek MinimumAgeRequirement türü için bir yaş alanı budur.

-   AuthorizationHandler uygulayan bir işleyici&lt;T&gt;, burada T işleyici karşılayabilecek IAuthorizationRequirement türüdür. İşleyici, kullanıcı hakkında bilgileri içeren belirtilen bir bağlam gereksinimini karşılayıp karşılamadığını denetler HandleRequirementAsync yöntemi uygulaması gerekir.

Kullanıcı, gereksinim, bir bağlam çağrısı karşılıyorsa. Başarılı olacak kullanıcı yetki verildiğini gösterir. Bir kullanıcı bir kimlik doğrulama gereksinimini karşılayan birden çok yol varsa, birden fazla işleyici oluşturulabilir.

Özel ilke gereksinimlerini AddPolicy çağrıları ile kaydetmeye ek olarak, aynı zamanda özel gereksinim işleyicilerine bağımlılık ekleme (Hizmetler. aracılığıyla kayıt olmanız gereklidir AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Özel yetkilendirme gereksinimi ve denetimi (bir DateOfBirth talebi temel alan) bir kullanıcının yaşını işleyici örneği ASP.NET Core kullanılabilir [yetkilendirme belgeleri](https://docs.asp.net/en/latest/security/authorization/policies.html).

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
>[Önceki](index.md)
>[İleri](developer-app-secrets-storage.md)