---
title: SYSLIB0002 hatası
description: Derleme zamanı hatası SYSLIB0002 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 774675e96d11a8e1b5d82767695d0defd1e8cfad
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596569"
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

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [PrincipalPermissionAttribute hata olarak kullanımdan kalktı](../core-libraries/5.0/principalpermissionattribute-obsolete.md)
