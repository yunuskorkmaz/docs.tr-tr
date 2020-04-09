---
title: .NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında
description: .NET Microservices ve Web Applications güvenlik - ASP.NET Core uygulamalarında ana yetkilendirme seçeneklerine genel bir bakış alın - rol tabanlı ve politika tabanlı.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 27936a33ea2bb46cedb9d10ee47a2117e1843e14
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988212"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>.NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında

Kimlik doğrulamadan sonra, ASP.NET Core Web API'leri erişim yetkisi gerekir. Bu işlem, bir hizmetin API'leri bazı kimlik doğrulaması yapılan kullanıcılar için kullanılabilir hale getirmenize, ancak tümüne değil, tümüne olanak sağlamasına olanak tanır. [Yetkilendirme,](/aspnet/core/security/authorization/introduction) kullanıcıların rollerine veya talepleri veya diğer buluşsal incelemeleri incelemeyi içerebilecek özel ilkelere dayalı olarak yapılabilir.

ASP.NET Core MVC rotasına erişimi kısıtlamak, aşağıdaki örnekte gösterildiği gibi, eylem yöntemine (veya denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa denetleyicinin sınıfına) bir Yetkilendirme özniteliği uygulamak kadar kolaydır:

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

Varsayılan olarak, parametrelerolmadan bir Yetkilendirme özniteliği eklemek, bu denetleyici veya eylem için kimlik doğrulaması yapılan kullanıcılara erişimi sınırlandıracaktır. Bir API'nin yalnızca belirli kullanıcılar için kullanılabilir olmasını daha fazla kısıtlamak için, öznitelik, kullanıcıların karşılaması gereken rolleri veya ilkeleri belirtmek için genişletilebilir.

## <a name="implement-role-based-authorization"></a>Rol tabanlı yetkilendirmeyi uygulama

ASP.NET Çekirdek Kimlik rolleri yerleşik bir kavram vardır. ASP.NET Çekirdek Kimlik, kullanıcılara ek olarak uygulama tarafından kullanılan farklı roller hakkında bilgi depolar ve hangi kullanıcıların hangi rollere atandığını izler. Bu atamalar, kalıcı depolamadaki `RoleManager` rolleri güncelleyen tür ve kullanıcılardan `UserManager` roller veren veya iptal edebilen türle programlı olarak değiştirilebilir.

JWT taşıyıcı belirteçleri ile kimlik doğrulaması iseniz, ASP.NET Core JWT taşıyıcı kimlik doğrulama aracı belirteç bulunan rol iddialarına dayalı olarak kullanıcının rollerini dolduracaktır. Bir MVC eylemine veya denetleyicisine erişimi belirli rollerdeki kullanıcılarla sınırlamak için, aşağıdaki kod parçasında gösterildiği gibi Yetkilendirme ek açıklamasına (öznitelik) bir Rol parametresi ekleyebilirsiniz:

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

Bu örnekte, Yalnızca Administrator veya PowerUser rollerindeki kullanıcılar ControlPanel denetleyicisinde (SetTime eylemini yürütme gibi) API'lara erişebilir. Kapatma API'si, yalnızca Yönetici rolündeki kullanıcılara erişime izin vermek için daha da kısıtlanır.

Bir kullanıcının birden çok rolde olmasını sağlamak için, aşağıdaki örnekte gösterildiği gibi birden çok Yetkilendirme özniteliği kullanırsınız:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Bu örnekte, API1'i aramak için bir kullanıcının şunları yapması gerekir:

- Administrator *veya* PowerUser rolünde olun *ve*

- RemoteEmployee rolünde olun *ve*

- CustomPolicy yetkilendirmesi için özel bir işleyiciyi karşıla.

## <a name="implement-policy-based-authorization"></a>İlke tabanlı yetkilendirmeyi uygulama

Özel yetkilendirme kuralları yetkilendirme [ilkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html)kullanılarak da yazılabilir. Bu bölüme genel bir bakış sağlar. Daha fazla bilgi için [ASP.NET Yetkilendirme Çalıştayı'na](https://github.com/blowdart/AspNetAuthorizationWorkshop)bakın.

Özel yetkilendirme ilkeleri, hizmeti kullanarak Başlangıç.ConfigureServices yönteminde kaydedilir. Yetkilendirme ekleme yöntemi. Bu yöntem, Yetkilendirme Seçenekleri bağımsız değişkenini yapılandıran bir temsilci alır.

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

Örnekte gösterildiği gibi, ilkeler farklı gereksinim türleri ile ilişkilendirilebilir. İlkeler kaydedildikten sonra, bir eyleme veya denetleyiciye, ilkeğin adını Yetkilendirilen özniteliğin İlkes `[Authorize(Policy="EmployeesOnly")]`bağımsız değişkeni olarak geçirerek (örneğin, ) İlkelerin yalnızca bir gereksinimi değil, birden çok gereksinimi olabilir (bu örneklerde gösterildiği gibi) uygulanabilir.

Önceki örnekte, ilk AddPolicy çağrısı role göre yetkilendirmenin alternatif bir yoludur. Bir `[Authorize(Policy="AdministratorsOnly")]` API'ye uygulanırsa, yalnızca Yönetici rolündeki kullanıcılar bu apiye erişebilir.

İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> arama, kullanıcı için belirli bir talebin bulunmasını gerektiren kolay bir yol olduğunu gösterir. Yöntem <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> de isteğe bağlı olarak talep için beklenen değerleri alır. Değerler belirtilirse, gereksinim yalnızca kullanıcının hem doğru türde hem de belirtilen değerlerden birine sahip olması durumunda karşılanır. JWT taşıyıcı kimlik doğrulama aracı kullanıyorsanız, tüm JWT özellikleri kullanıcı talepleri olarak kullanılabilir olacaktır.

Burada gösterilen en ilginç ilke, özel bir yetkilendirme gereksinimi kullandığından üçüncü `AddPolicy` yöntemdedir. Özel yetkilendirme gereksinimlerini kullanarak, yetkilendirmenin nasıl gerçekleştirildiği üzerinde büyük bir denetime sahip olabilirsiniz. Bunun işe yaraması için şu türleri uygulamanız gerekir:

- Gereksinimayrıntılarını belirten alanları içeren <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> ve bu gereksinimtüründen türeyen bir Gereksinim türü. Örnekte, bu örnek `MinimumAgeRequirement` türü için bir yaş alanıdır.

- <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>T'nin işleyicinin <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> karşılayabildiği tür olduğu bir işleyici. İşleyici, kullanıcı <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> hakkında bilgi içeren belirli bir bağlamın gereksinimi karşılayıp karşılamadığını denetleyen yöntemi uygulamalıdır.

Kullanıcı gereksinimi karşılarsa, bir `context.Succeed` arama kullanıcının yetkili olduğunu gösterir. Bir kullanıcının yetkilendirme gereksinimini karşılayabilen birden çok yolu varsa, birden çok işleyici oluşturulabilir.

Aramalar ile `AddPolicy` özel ilke gereksinimleri kaydetmeye ek olarak, ayrıca Bağımlılık Enjeksiyon (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) ile özel gereksinim işleyicileri kayıt gerekir.

Özel yetkilendirme gereksinimi örneği ve kullanıcının yaşını denetlemek için işleyici `DateOfBirth` (bir iddiaya dayalı) ASP.NET Çekirdek yetkilendirme [belgelerinde](https://docs.asp.net/en/latest/security/authorization/policies.html)mevcuttur.

## <a name="additional-resources"></a>Ek kaynaklar

- **ASP.NET Çekirdek Kimlik Doğrulama** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET Çekirdek Yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Rol Tabanlı Yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Özel İlke Tabanlı Yetkilendirme** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](developer-app-secrets-storage.md)
