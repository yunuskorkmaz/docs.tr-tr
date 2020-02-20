---
title: .NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-ASP.NET Core uygulamalar-rol tabanlı ve ilke tabanlı başlıca yetkilendirme seçeneklerine genel bakış alın.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f6b69faceac9a9b4819212cc04f89080f3ddad56
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501775"
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

ASP.NET Core kimliğin yerleşik bir rol kavramı vardır. Kullanıcıların yanı sıra, ASP.NET Core kimlik, uygulama tarafından kullanılan farklı rollerle ilgili bilgileri depolar ve hangi kullanıcıların hangi rollere atandığını izler. Bu atamalar, kalıcı depolama alanındaki rolleri güncelleştiren `RoleManager` türü ile program aracılığıyla değiştirilebilir ve kullanıcılara roller verebilir veya bunları iptal edebilir `UserManager` türü.

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

Örnekte gösterildiği gibi, ilkeler farklı tür gereksinimlerle ilişkilendirilebilir. İlkeler kaydedildikten sonra, yetkilendirme özniteliğinin Ilke bağımsız değişkeni olarak ilke adını geçirerek bir eyleme veya denetleyiciye uygulanabilir (örneğin, `[Authorize(Policy="EmployeesOnly")]`) Ilkeler yalnızca bir tane değil birden çok gereksinimi olabilir (Bu örneklerde gösterildiği gibi).

Önceki örnekte, ilk AddPolicy çağrısı role göre yetkilendirmek için yalnızca alternatif bir yoldur. Bir API 'ye `[Authorize(Policy="AdministratorsOnly")]` uygulanmışsa, yalnızca yönetici rolündeki kullanıcılar erişebilir.

İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> çağrısı, Kullanıcı için belirli bir talebin mevcut olmasını gerektirmek için kolay bir yol gösterir. <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> yöntemi talep için de isteğe bağlı olarak beklenen değerleri alır. Değerler belirtilmişse, gereksinim yalnızca Kullanıcı doğru türde ve belirtilen değerlerden birine ait bir talebe sahipse karşılanır. JWT taşıyıcı kimlik doğrulama ara yazılımını kullanıyorsanız, tüm JWT özellikleri kullanıcı talepleri olarak kullanılabilir olacaktır.

Burada gösterilen en ilginç ilke, özel bir yetkilendirme gereksinimi kullandığından, üçüncü `AddPolicy` yöntemidir. Özel yetkilendirme gereksinimlerini kullanarak, yetkilendirmenin nasıl gerçekleştirileceği konusunda harika bir denetim sahibi olabilirsiniz. Bunun çalışması için bu türleri uygulamanız gerekir:

- <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> türetilen ve gereksinimin ayrıntılarını belirten alanlar içeren bir gereksinim türü. Örnekte bu, örnek `MinimumAgeRequirement` türü için bir yaş alanıdır.

- <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>uygulayan bir işleyici; burada T, işleyicinin karşılayabileceği <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> türüdür. İşleyicinin, Kullanıcı hakkında bilgi içeren belirtilen bağlamın gereksinimi karşılayıp karşılamadığını denetleyen <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> yöntemini uygulaması gerekir.

Kullanıcı, gereksinimi karşılıyorsa, `context.Succeed` çağrısı kullanıcının yetkili olduğunu gösterir. Bir kullanıcının bir yetkilendirme gereksinimini karşılayabilmesi için birden çok yol varsa, birden çok işleyici oluşturulabilir.

Özel ilke gereksinimlerinin `AddPolicy` çağrılarıyla kaydedilmesinin yanı sıra, bağımlılık ekleme (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) aracılığıyla özel gereksinim işleyicilerini de kaydetmeniz gerekir.

Bir kullanıcının yaşını (bir `DateOfBirth` talebine göre) denetlemeye yönelik özel bir yetkilendirme gereksinimi ve işleyicinin bir örneği ASP.NET Core [Yetkilendirme belgelerinde](https://docs.asp.net/en/latest/security/authorization/policies.html)bulunabilir.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Core kimlik doğrulaması** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET Core yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Rol tabanlı yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Özel Ilke tabanlı yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](developer-app-secrets-storage.md)
