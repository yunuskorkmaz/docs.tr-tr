---
title: SYSLIB0002 hatası
description: Derleme zamanı hatası SYSLIB0002 üreten kullanımdan çıkarılması hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 00fd42975c9286221b75c87caef8d2109b9b7100
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333357"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="8cfab-103">SYSLIB0002: PrincipalPermissionAttribute artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="8cfab-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="8cfab-104"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Oluşturucu kullanımdan kalkmıştır ve `SYSLIB0002` .NET 5,0 ' den başlayarak derleme zamanı hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8cfab-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="8cfab-105">Bu özniteliği örnekleyemezsiniz veya bir yönteme uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8cfab-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="8cfab-106">Kullanımdan çıkarma uyarılarının aksine, hatayı bastırılamaz.</span><span class="sxs-lookup"><span data-stu-id="8cfab-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="8cfab-107">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="8cfab-107">Workarounds</span></span>

- <span data-ttu-id="8cfab-108">Özniteliği bir ASP.NET MVC eylem yöntemine uyguluyorsanız:</span><span class="sxs-lookup"><span data-stu-id="8cfab-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="8cfab-109">ASP kullanmayı düşünün. NET 'in yerleşik yetkilendirme altyapısı.</span><span class="sxs-lookup"><span data-stu-id="8cfab-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="8cfab-110">Aşağıdaki kod, bir denetleyiciye bir özniteliğe nasıl not ekleneceğini gösterir <xref:System.Web.Mvc.AuthorizeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="8cfab-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="8cfab-111">ASP.NET çalışma zamanı, eylemi gerçekleştirmeden önce kullanıcıyı yetkilendirecektir.</span><span class="sxs-lookup"><span data-stu-id="8cfab-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

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

  <span data-ttu-id="8cfab-112">Daha fazla bilgi için, [ASP.NET Core rol tabanlı yetkilendirme](/aspnet/core/security/authorization/roles) ve [ASP.NET Core yetkilendirme bölümüne giriş](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="8cfab-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="8cfab-113">Özniteliği, bir Web uygulaması bağlamı dışında kitaplık koduna uyguluyorsanız:</span><span class="sxs-lookup"><span data-stu-id="8cfab-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="8cfab-114">Yöntemini çağırarak, kendi yönteminizin başlangıcında denetimleri el ile gerçekleştirin <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8cfab-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8cfab-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cfab-115">See also</span></span>

- [<span data-ttu-id="8cfab-116">PrincipalPermissionAttribute hata olarak kullanımdan kalktı</span><span class="sxs-lookup"><span data-stu-id="8cfab-116">PrincipalPermissionAttribute is obsolete as error</span></span>](3.1-5.0.md#principalpermissionattribute-is-obsolete-as-error)
