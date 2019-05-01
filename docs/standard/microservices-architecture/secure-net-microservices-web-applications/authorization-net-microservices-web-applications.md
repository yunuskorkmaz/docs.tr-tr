---
title: .NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında
description: .NET mikro Hizmetleri ve Web uygulamaları - güvenlik, ASP.NET Core uygulamaları - rol tabanlı ve ilke tabanlı ana yetkilendirme seçeneklerine genel bakış edinin.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019509"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında

Kimlik doğrulamasından sonra ASP.NET Core Web API'lerine erişim yetkisi vermek gerekir. Bu işlem, bazı kimliği doğrulanmış kullanıcılar tarafından kullanılabilir, ancak çok tüm API'leri yapmak bir hizmet sağlar. [Yetkilendirme](/aspnet/core/security/authorization/introduction) kullanıcıların rollere göre Bitti veya talep veya diğer buluşsal yöntemler inceleyerek içerebilir özel ilkesini temel alarak.

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

## <a name="implement-role-based-authorization"></a>Uygulama rol tabanlı yetkilendirme

ASP.NET Core kimliği yerleşik bir rol kavramları vardır. Kullanıcıların, yanı sıra ASP.NET Core kimliği uygulama tarafından kullanılan farklı roller hakkındaki bilgileri saklar ve hangi kullanıcıların hangi rollerine atandığı izler. Bu atamaları ile program aracılığıyla değiştirilebilir `RoleManager` güncelleştiren rollerdeki kalıcı depolama türü ve `UserManager` verebilir veya kullanıcıların rollerini iptal türü.

JWT taşıyıcı belirteçleri ile kimlik doğrulaması, ASP.NET Core JWT taşıyıcı kimlik doğrulaması ara yazılımı belirteçte rol talepleri göre bir kullanıcının rollerini doldurur. Bir MVC eylem veya denetleyici belirli roller kullanıcılara erişimi sınırlamak için bir rol parametresi Authorize açıklamada (öznitelik), aşağıdaki kod parçasını gösterildiği gibi ekleyebilirsiniz:

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

- Yönetici olması *veya* PowerUser rol *ve*

- RemoteEmployee rolünde olması *ve*

- CustomPolicy yetkilendirme için özel bir işleyici karşılar.

## <a name="implement-policy-based-authorization"></a>İlke tabanlı yetkilendirme uygulayın

Özel Yetkilendirme kuralları da yazılabilir kullanarak [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html). Bu bölümde, genel bir bakış sağlar. Daha fazla bilgi için [ASP.NET yetkilendirme Atölyesi](https://github.com/blowdart/AspNetAuthorizationWorkshop).

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

Örnekte gösterildiği gibi ilkeleri farklı gereksinimleri ile ilişkilendirilebilir. İlkeleri kaydolduktan sonra bir eylem veya denetleyici Authorize özniteliği ilke bağımsız değişkeni bir ilkenin adını geçirerek uygulanabilirler (örneğin, `[Authorize(Policy="EmployeesOnly")]`) İlkeleri (Bu gösterildiği gibi yalnızca bir tane değil birden çok gereksinimleri olabilir örnekler için).

Önceki örnekte, ilk AddPolicy çağrı role göre yetkilendirme yalnızca bir diğer yoludur. Varsa `[Authorize(Policy="AdministratorsOnly")]` yönetici rolündeki kullanıcılar erişebilmesi için yalnızca bir API için uygulanır.

İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> çağrı belirli bir talep kullanıcı için mevcut olduğunu istemek için kolay bir yolunu gösterir. <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> Yöntemi ayrıca isteğe bağlı olarak talep için beklenen değerleri alır. Değer belirtilmişse, yalnızca kullanıcının hem doğru türde bir talep ve belirtilen değerlerden biri varsa bu gereksinimi karşılarsınız. JWT taşıyıcı kimlik doğrulaması ara yazılımı kullanıyorsanız, kullanıcı talepleri tüm JWT özellikleri kullanılabilir.

Üçüncü İşte gösterilen en ilginç ilke `AddPolicy` yöntemi, bir özel kimlik doğrulama gereksinimini kullandığından. Özel yetkilendirme gereksinimleri kullanarak Yetkilendirme nasıl gerçekleştirildiğini denetim harika bir fırsat olabilir. Bunun çalışması için bu tür uygulamanız gerekir:

- Türetilen bir gereksinimleri türü <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> ve gereksinim ayrıntılarını belirtme alanları içerir. Örnekte, bu örnek için bir yaş alan olup, `MinimumAgeRequirement` türü.

- Uygulayan bir işleyici <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, burada T türü <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> işleyici karşılayan. İşleyici uygulamalıdır <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> yöntemi kullanıcı hakkındaki bilgileri içeren belirtilen bir bağlam gereksinimini karşılayıp karşılamadığını denetler.

Kullanıcı, gereksinim, bir çağrı karşılayıp karşılamadığını `context.Succeed` kullanıcı yetki verildiğini gösterir. Bir kullanıcı bir kimlik doğrulama gereksinimini karşılayan birden çok yol varsa, birden fazla işleyici oluşturulabilir.

Özel ilke gereksinimlerine kaydetme yanı sıra `AddPolicy` çağrılar da ihtiyacınız özel gereksinim işleyicilerine bağımlılık ekleme yoluyla kaydetmek (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).

Özel yetkilendirme gereksinimi ve denetimi bir kullanıcının yaşını işleyici örneği (dayalı bir `DateOfBirth` talep) içinde ASP.NET Core kullanılabilir [yetkilendirme belgeleri](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core kimlik doğrulaması** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET Core yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Rol tabanlı yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Özel ilke tabanlı yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](developer-app-secrets-storage.md)
