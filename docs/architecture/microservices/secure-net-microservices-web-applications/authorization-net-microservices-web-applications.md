---
title: .NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-ASP.NET Core uygulamalar-rol tabanlı ve ilke tabanlı başlıca yetkilendirme seçeneklerine genel bakış alın.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296470"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında

Kimlik doğrulamasından sonra, ASP.NET Core Web API 'Lerinin erişimi yetkilendirmeniz gerekir. Bu işlem, bir hizmetin API 'Leri bazı kimliği doğrulanmış kullanıcılar için kullanılabilir olmasına izin verir. [Yetkilendirme](/aspnet/core/security/authorization/introduction) , kullanıcıların rollerine göre veya özel ilkeye göre yapılabilir ve bu da talepleri veya diğer buluşsal yöntemleri inceleyerek olabilir.

Bir ASP.NET Core MVC yoluna erişimi kısıtlamak, aşağıdaki örnekte gösterildiği gibi, eylem yöntemine (veya denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa denetleyicinin sınıfına) bir yetkilendirme özniteliği uygulamanın kolay bir işlemdir:

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

Varsayılan olarak, parametresiz bir yetkilendirme özniteliği eklemek, bu denetleyici veya eylem için kimliği doğrulanmış kullanıcılara göre sınırlandıracaktır. Bir API 'yi yalnızca belirli kullanıcılar için kullanılabilir olacak şekilde kısıtlamak için, bu öznitelik, kullanıcıların karşılaması gereken rolleri veya ilkeleri belirtmek için genişletilebilir.

## <a name="implement-role-based-authorization"></a>Rol tabanlı yetkilendirme uygulama

ASP.NET Core kimliğin yerleşik bir rol kavramı vardır. Kullanıcıların yanı sıra, ASP.NET Core kimlik, uygulama tarafından kullanılan farklı rollerle ilgili bilgileri depolar ve hangi kullanıcıların hangi rollere atandığını izler. Bu atamalar, kalıcı depolama alanındaki rolleri güncelleştiren `RoleManager` tür ile programlı olarak değiştirilebilir `UserManager` ve kullanıcılardan rol verebilir veya bunları iptal edebilir.

JWT taşıyıcı belirteçleriyle kimlik doğrulaması yapıyorsanız, ASP.NET Core JWT taşıyıcı kimlik doğrulama ara yazılımı, bir kullanıcının rollerini belirteçte bulunan rol taleplerini temel alarak doldurur. Belirli rollerdeki kullanıcılarla bir MVC eylemine veya denetleyiciye erişimi sınırlandırmak için, yetkilendirme ek açıklamasına (öznitelik) aşağıdaki kod parçasında gösterildiği gibi bir rol parametresi dahil edebilirsiniz:

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

Bu örnekte, yalnızca yönetici veya PowerUser rollerinin kullanıcıları ControlPanel denetleyicisindeki (SetTime eylemini yürütme gibi) API 'Lere erişebilir. Kapanmaya yönelik API, yalnızca yönetici rolündeki kullanıcılara erişime izin verecek şekilde kısıtlıdır.

Bir kullanıcının birden çok rolde olmasını gerektirmek için, aşağıdaki örnekte gösterildiği gibi birden çok yetkilendirme özniteliği kullanırsınız:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Bu örnekte, API1 çağırmak için bir kullanıcının şunları yapmanız gerekir:

- Yönetici *veya* PowerUseR rolünde olun *ve*

- RemoteEmployee rolünde olun *ve*

- CustomPolicy yetkilendirmesi için özel bir işleyici karşılanacak.

## <a name="implement-policy-based-authorization"></a>İlke tabanlı yetkilendirme uygulama

Özel yetkilendirme kuralları, [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html)kullanılarak da yazılabilir. Bu bölümde genel bakış sunulmaktadır. Daha fazla bilgi için bkz. [ASP.net Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Özel yetkilendirme ilkeleri hizmeti kullanılarak Startup. ConfigureServices yöntemine kaydedilir. Addaduthorleştirme yöntemi. Bu yöntem, AuthorizationOptions bağımsız değişkenini yapılandıran bir temsilci alır.

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

Örnekte gösterildiği gibi, ilkeler farklı tür gereksinimlerle ilişkilendirilebilir. İlkeler kaydedildikten sonra, yetkilendirme özniteliğinin ilke bağımsız değişkeni olarak ilke adını geçirerek bir eyleme veya denetleyiciye uygulanabilir (örneğin, `[Authorize(Policy="EmployeesOnly")]`) ilkeler yalnızca bir tane değil birden çok gereksinimi olabilir (Bunlar aşağıda gösterildiği gibi). örnekler).

Önceki örnekte, ilk AddPolicy çağrısı role göre yetkilendirmek için yalnızca alternatif bir yoldur. `[Authorize(Policy="AdministratorsOnly")]` Bir API 'ye uygulanmışsa, yalnızca yönetici rolündeki kullanıcılar bu erişime erişebilir.

İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> çağrı, Kullanıcı için belirli bir talebin mevcut olmasını gerektirmek için kolay bir yol gösterir. <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> Yöntemi Ayrıca isteğe bağlı olarak talep için beklenen değerleri alır. Değerler belirtilmişse, gereksinim yalnızca Kullanıcı doğru türde ve belirtilen değerlerden birine ait bir talebe sahipse karşılanır. JWT taşıyıcı kimlik doğrulama ara yazılımını kullanıyorsanız, tüm JWT özellikleri kullanıcı talepleri olarak kullanılabilir olacaktır.

Burada gösterilen en ilginç ilke, özel bir yetkilendirme gereksinimi `AddPolicy` kullandığından, üçüncü yöntemde verilmiştir. Özel yetkilendirme gereksinimlerini kullanarak, yetkilendirmenin nasıl gerçekleştirileceği konusunda harika bir denetim sahibi olabilirsiniz. Bunun çalışması için bu türleri uygulamanız gerekir:

- Gereksiniminin ayrıntılarını belirten alanlar içeren ve <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> öğesinden türetilen bir gereksinim türü. Örnekte, bu örnek `MinimumAgeRequirement` tür için bir yaş alanıdır.

- Uygulayan <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>bir işleyici, burada T işleyicinin karşılayabileceği <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> türüdür. İşleyicinin, Kullanıcı hakkında bilgi <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> içeren belirtilen bağlamın gereksinimi karşılayıp karşılamadığını denetleyen yöntemini uygulaması gerekir.

Kullanıcı gereksinimi karşılıyorsa, için `context.Succeed` bir çağrısı, kullanıcının yetkili olduğunu gösterir. Bir kullanıcının bir yetkilendirme gereksinimini karşılayabilmesi için birden çok yol varsa, birden çok işleyici oluşturulabilir.

Çağrılarla `AddPolicy` özel ilke gereksinimlerinin kaydedilmesinin yanı sıra, bağımlılık ekleme (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) yoluyla özel gereksinim işleyicilerini de kaydetmeniz gerekir.

Bir kullanıcının yaşını ( `DateOfBirth` talebe bağlı olarak) denetlemek için özel bir yetkilendirme gereksinimi ve işleyicinin bir örneği ASP.NET Core [Yetkilendirme belgelerinde](https://docs.asp.net/en/latest/security/authorization/policies.html)bulunabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core kimlik doğrulaması** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET Core yetkilendirmesi** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Rol tabanlı yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Özel Ilke tabanlı yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](developer-app-secrets-storage.md)
