---
title: 'Son değişiklik: PrincipalPermissionAttribute hata olarak kullanımdan kalktı'
description: PrincipalPermissionAttribute oluşturucusunun artık kullanılmayan ve bir derleme zamanı hatası oluşturduğu çekirdek .NET kitaplıklarında .NET 5 ' ün son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 7568883935633e98b884b553efccf50504448b77
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257238"
---
# <a name="principalpermissionattribute-is-obsolete-as-error"></a>PrincipalPermissionAttribute hata olarak kullanımdan kalktı

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Oluşturucu kullanımdan kalkmıştır ve derleme zamanı hatası oluşturur. Bu özniteliği örnekleyemezsiniz veya bir yönteme uygulayamazsınız.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework ve .NET Core 'da, özniteliğiyle yöntemlere not ekleyebilirsiniz <xref:System.Security.Permissions.PrincipalPermissionAttribute> . Örnek:

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

.NET 5 ' <xref:System.Security.Permissions.PrincipalPermissionAttribute> ten başlayarak özniteliği bir metoda uygulayamazsınız. Özniteliği için Oluşturucu artık kullanılmıyor ve derleme zamanı hatası veriyor. Kullanımdan çıkarma uyarılarının aksine, hatayı bastırılamaz.

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Türü, alt sınıfını oluşturan diğer türler gibi <xref:System.Security.Permissions.SecurityAttribute> bir parçasıdır. NET 'in kod erişim güvenliği (CAS) altyapısı. .NET Framework 2. x-4. x içinde, çalışma zamanı, <xref:System.Security.Permissions.PrincipalPermissionAttribute> uygulama tam güven senaryosunda çalışıyor olsa bile Yöntem girişinde ek açıklamaları zorlar. .NET Core ve .NET 5 ve üzeri CAS özniteliklerini desteklemez ve çalışma zamanı bunları yoksayar.

.NET Framework .NET Core ve .NET 5 ' e yapılan davranıştaki bu fark, erişimin engellenmesi gereken ancak bunun yerine izin verilen bir "başarısız açma" senaryosu oluşmasına neden olabilir. "Başarısız açma" senaryosunu engellemek için, artık .NET 5 veya üstünü hedefleyen kodda özniteliği uygulayamazsınız.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name=""></a><a id="permission-action">Önerilen eylem</a>

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

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
