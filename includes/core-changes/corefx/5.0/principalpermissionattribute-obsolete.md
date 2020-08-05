---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556351"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a>PrincipalPermissionAttribute hata olarak kullanımdan kalktı

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Oluşturucu kullanımdan kalkmıştır ve derleme zamanı hatası oluşturur. Bu özniteliği örnekleyemezsiniz veya bir yönteme uygulayamazsınız.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ve .NET Core 'da, özniteliğiyle yöntemlere not ekleyebilirsiniz <xref:System.Security.Permissions.PrincipalPermissionAttribute> . Örnek:

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

.NET 5,0 ' den başlayarak <xref:System.Security.Permissions.PrincipalPermissionAttribute> özniteliği bir yönteme uygulayamazsınız. Özniteliği için Oluşturucu artık kullanılmıyor ve derleme zamanı hatası veriyor. Kullanımdan çıkarma uyarılarının aksine, hatayı bastırılamaz.

#### <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Türü, alt sınıfını oluşturan diğer türler gibi <xref:System.Security.Permissions.SecurityAttribute> bir parçasıdır. NET 'in kod erişim güvenliği (CAS) altyapısı. .NET Framework 2. x-4. x içinde, çalışma zamanı, <xref:System.Security.Permissions.PrincipalPermissionAttribute> uygulama tam güven senaryosunda çalışıyor olsa bile Yöntem girişinde ek açıklamaları zorlar. .NET Core ve .NET 5,0 ve üzeri CAS özniteliklerini desteklemez ve çalışma zamanı bunları yoksayar.

.NET Framework .NET Core ve .NET 5,0 davranışlarındaki bu fark, erişimin engellenmesi gereken ancak bunun yerine izin verilen bir "başarısız açma" senaryosu oluşmasına neden olabilir. "Başarısız açma" senaryosunu engellemek için artık .NET 5,0 veya üstünü hedefleyen kodda özniteliği uygulayamazsınız.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 7

#### <a name="recommended-action"></a>Önerilen eylem

Kullanımdan çıkarma hatasıyla karşılaşırsanız, işlem yapmanız gerekir.

- **Özniteliği bir ASP.NET MVC eylem yöntemine uyguluyorsanız:**

  ASP kullanmayı düşünün. NET 'in yerleşik yetkilendirme altyapısı. Aşağıdaki kod, bir denetleyiciye bir özniteliğe nasıl not ekleneceğini gösterir <xref:System.Web.Mvc.AuthorizeAttribute> . ASP.NET çalışma zamanı, eylemi gerçekleştirmeden önce kullanıcıyı yetkilendirecektir.

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  Daha fazla bilgi için, [ASP.NET Core rol tabanlı yetkilendirme](/aspnet/core/security/authorization/roles) ve [ASP.NET Core yetkilendirme bölümüne giriş](/aspnet/core/security/authorization/introduction).

- **Özniteliği, bir Web uygulaması bağlamı dışında kitaplık koduna uyguluyorsanız:**

  Yönteminizin başlangıcında denetimleri el ile gerçekleştirin. Bu, yöntemi kullanılarak yapılabilir <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> .

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a>Kategori

- Core .NET kitaplıkları
- Güvenlik

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
