---
title: SYSLIB0002 hatası
description: Derleme zamanı hatası SYSLIB0002 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 53eb51d5e525c463e5698710bdb6fa0c0907e43c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440783"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a>SYSLIB0002: PrincipalPermissionAttribute artık kullanılmıyor

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Oluşturucu kullanımdan kalkmıştır ve `SYSLIB0002` .NET 5,0 ' den başlayarak derleme zamanı hatası oluşturur. Bu özniteliği örnekleyemezsiniz veya bir yönteme uygulayamazsınız.

Kullanımdan çıkarma uyarılarının aksine, hatayı bastırılamaz.

## <a name="workarounds"></a>Geçici Çözümler

- Özniteliği bir ASP.NET MVC eylem yöntemine uyguluyorsanız:

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

- Özniteliği, bir Web uygulaması bağlamı dışında kitaplık koduna uyguluyorsanız:

  Yöntemini çağırarak, kendi yönteminizin başlangıcında denetimleri el ile gerçekleştirin <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> .

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

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [PrincipalPermissionAttribute hata olarak kullanımdan kalktı](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)
