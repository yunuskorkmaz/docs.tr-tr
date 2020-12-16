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
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="ad3fe-103">SYSLIB0002: PrincipalPermissionAttribute artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="ad3fe-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="ad3fe-104"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Oluşturucu kullanımdan kalkmıştır ve `SYSLIB0002` .NET 5,0 ' den başlayarak derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ad3fe-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="ad3fe-105">Bu özniteliği örnekleyemezsiniz veya bir yönteme uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ad3fe-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="ad3fe-106">Kullanımdan çıkarma uyarılarının aksine, hatayı bastırılamaz.</span><span class="sxs-lookup"><span data-stu-id="ad3fe-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="ad3fe-107">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="ad3fe-107">Workarounds</span></span>

- <span data-ttu-id="ad3fe-108">Özniteliği bir ASP.NET MVC eylem yöntemine uyguluyorsanız:</span><span class="sxs-lookup"><span data-stu-id="ad3fe-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="ad3fe-109">ASP kullanmayı düşünün. NET 'in yerleşik yetkilendirme altyapısı.</span><span class="sxs-lookup"><span data-stu-id="ad3fe-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="ad3fe-110">Aşağıdaki kod, bir denetleyiciye bir özniteliğe nasıl not ekleneceğini gösterir <xref:System.Web.Mvc.AuthorizeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ad3fe-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="ad3fe-111">ASP.NET çalışma zamanı, eylemi gerçekleştirmeden önce kullanıcıyı yetkilendirecektir.</span><span class="sxs-lookup"><span data-stu-id="ad3fe-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="ad3fe-112">Daha fazla bilgi için, [ASP.NET Core rol tabanlı yetkilendirme](/aspnet/core/security/authorization/roles) ve [ASP.NET Core yetkilendirme bölümüne giriş](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="ad3fe-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="ad3fe-113">Özniteliği, bir Web uygulaması bağlamı dışında kitaplık koduna uyguluyorsanız:</span><span class="sxs-lookup"><span data-stu-id="ad3fe-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="ad3fe-114">Yöntemini çağırarak, kendi yönteminizin başlangıcında denetimleri el ile gerçekleştirin <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ad3fe-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad3fe-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad3fe-115">See also</span></span>

- [<span data-ttu-id="ad3fe-116">PrincipalPermissionAttribute hata olarak kullanımdan kalktı</span><span class="sxs-lookup"><span data-stu-id="ad3fe-116">PrincipalPermissionAttribute is obsolete as error</span></span>](../core-libraries/5.0/principalpermissionattribute-obsolete.md)
