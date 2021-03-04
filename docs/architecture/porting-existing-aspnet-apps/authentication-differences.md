---
title: ASP.NET MVC ve ASP.NET Core arasındaki kimlik doğrulama ve yetkilendirmeyi karşılaştırın
description: ASP.NET MVC ve ASP.NET Core arasındaki kimlik doğrulama ve yetkilendirme farklılıkları Özeti.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: c8f3314186b7408e40d3a79cbc922a29eb75c5d2
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106146"
---
# <a name="compare-authentication-and-authorization-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="ec41f-103">ASP.NET MVC ve ASP.NET Core arasındaki kimlik doğrulama ve yetkilendirmeyi karşılaştırın</span><span class="sxs-lookup"><span data-stu-id="ec41f-103">Compare authentication and authorization between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="ec41f-104">ASP.NET MVC 5 ' te, kimlik doğrulaması *App_Start* klasöründe *Startup.auth.cs* ' de yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ec41f-104">In ASP.NET MVC 5, authentication is configured in *Startup.Auth.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="ec41f-105">ASP.NET Core MVC 'de bu yapılandırma içinde oluşur `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ec41f-105">In ASP.NET Core MVC, this configuration occurs in `Startup.cs`.</span></span> <span data-ttu-id="ec41f-106">Kimlik doğrulama ve yetkilendirme, içindeki istek ardışık düzenine eklenen ara yazılımlar kullanılarak gerçekleştirilir `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="ec41f-106">Authentication and authorization are performed using middleware added to the request pipeline in `ConfigureServices`:</span></span>

```csharp
// inside Startup.ConfigureServices

app.UseRouting();

app.UseAuthentication();
app.UseAuthorization();

app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

<span data-ttu-id="ec41f-107">Kimlik doğrulama ara yazılımını, ara yazılım ardışık düzeninde uygun bir sıraya eklemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ec41f-107">It's important to add the auth middleware in the appropriate order in the middleware pipeline.</span></span> <span data-ttu-id="ec41f-108">Yalnızca bu uygulamayı ara yazılım için yapan istekler bundan etkilenir.</span><span class="sxs-lookup"><span data-stu-id="ec41f-108">Only requests that make it to the middleware will be impacted by it.</span></span> <span data-ttu-id="ec41f-109">Örneğin, öğesine yapılan bir çağrı `UseStaticFiles()` burada gösterilen kodun üstüne yerleştirilmişse, kimlik doğrulama ve yetkilendirme tarafından korunmaz.</span><span class="sxs-lookup"><span data-stu-id="ec41f-109">For instance, if a call to `UseStaticFiles()` was placed above the code shown here, it wouldn't be protected by authentication and authorization.</span></span>

<span data-ttu-id="ec41f-110">ASP.NET MVC ve Web API 'sinde, uygulamalar genellikle özelliğini kullanarak geçerli kullanıcıya başvurur `ClaimsPrincipal.Current` .</span><span class="sxs-lookup"><span data-stu-id="ec41f-110">In ASP.NET MVC and Web API, apps often refer to the current user using the `ClaimsPrincipal.Current` property.</span></span> <span data-ttu-id="ec41f-111">Bu özellik ASP.NET Core ayarlanmamış ve uygulamanızdaki herhangi bir davranış, [](/aspnet/core/migration/claimsprincipal-current) `User` üzerinde özelliğini kullanarak `ControllerBase` veya geçerli olan `HttpContext` ve `User` özelliğine başvurarak ClaimsPrincipal. Current öğesinden geçiş yapmak zorunda olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ec41f-111">This property isn't set in ASP.NET Core, and any behavior in your app that depends on it will need to [migrate from ClaimsPrincipal.Current](/aspnet/core/migration/claimsprincipal-current) by using the `User` property on `ControllerBase` or getting access to the current `HttpContext` and referencing its `User` property.</span></span> <span data-ttu-id="ec41f-112">Bu çözümlerin hiçbiri bir seçenek değilse, hizmetler kullanıcıyı bir bağımsız değişken olarak talep edebilir, bu durumda uygulamanın başka bir yerinde sağlanması gerekir ya da `IHttpContextAccessor` istenebilir ve ' ı almak için kullanılabilir `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="ec41f-112">If neither of these solutions is an option, services can request the User as an argument, in which case it must be supplied from elsewhere in the app, or the `IHttpContextAccessor` can be requested and used to get the `HttpContext`.</span></span>

## <a name="authorization"></a><span data-ttu-id="ec41f-113">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="ec41f-113">Authorization</span></span>

<span data-ttu-id="ec41f-114">Yetkilendirme, belirli bir kullanıcının uygulama içinde neler yapabileceğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ec41f-114">Authorization defines what a given user can do within the app.</span></span> <span data-ttu-id="ec41f-115">Yalnızca kullanıcının kim olduğunu tanımlayarak ilgili olan kimlik doğrulamasından ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="ec41f-115">It's separate from authentication, which is concerned merely with identifying who the user is.</span></span> <span data-ttu-id="ec41f-116">ASP.NET Core, yetkilendirme için basit, bildirime dayalı bir rol ve zengin, ilke tabanlı bir model sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec41f-116">ASP.NET Core provides a simple, declarative role and a rich, policy-based model for authorization.</span></span> <span data-ttu-id="ec41f-117">Bir kaynağın yetkilendirme gerektirdiğini belirtmek, `[Authorize]` özniteliği eyleme veya denetleyiciye eklemek kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="ec41f-117">Specifying that a resource requires authorization is often as simple as adding the `[Authorize]` attribute to the action or controller.</span></span> <span data-ttu-id="ec41f-118">MVC görünümlerinden Razor Pages geçiş yapıyorsanız, [başlangıçta Razor Pages yapılandırdığınızda yetkilendirme kurallarını belirtmeniz](/aspnet/core/security/authorization/razor-pages-authorization)gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec41f-118">If you're migrating to Razor Pages from MVC views, you should [specify conventions for authorization when you configure Razor Pages in Startup](/aspnet/core/security/authorization/razor-pages-authorization).</span></span>

<span data-ttu-id="ec41f-119">ASP.NET Core yetkilendirme, anonim kullanıcıları yalarken kimlik doğrulamalı kullanıcılara izin verirken basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec41f-119">Authorization in ASP.NET Core may be as simple as prohibiting anonymous users while allowing authenticated users.</span></span> <span data-ttu-id="ec41f-120">Ya da rol tabanlı, talep tabanlı ya da ilke tabanlı yetkilendirme yaklaşımlarını destekleyecek şekilde ölçeklendirebilir.</span><span class="sxs-lookup"><span data-stu-id="ec41f-120">Or it can scale up to support role-based, claims-based, or policy-based authorization approaches.</span></span> <span data-ttu-id="ec41f-121">Bu yaklaşımlar hakkında daha fazla bilgi için [ASP.NET Core 'de yetkilendirme](/aspnet/core/security/authorization/introduction)ile ilgili belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="ec41f-121">For more information on these approaches, see the documentation on [authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span> <span data-ttu-id="ec41f-122">Büyük olasılıkla, bunlardan birinin geçerli yetkilendirme yaklaşımınız ile yakından hizalandığını fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ec41f-122">You'll likely find that one of them is closely aligned with your current authorization approach.</span></span>

## <a name="references"></a><span data-ttu-id="ec41f-123">Başvurular</span><span class="sxs-lookup"><span data-stu-id="ec41f-123">References</span></span>

- [<span data-ttu-id="ec41f-124">ASP.NET MVC ile güvenlik, kimlik doğrulama ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="ec41f-124">Security, Authentication, and Authorization with ASP.NET MVC</span></span>](/aspnet/mvc/overview/security/)
- [<span data-ttu-id="ec41f-125">Kimlik doğrulaması ve kimliği ASP.NET Core geçir</span><span class="sxs-lookup"><span data-stu-id="ec41f-125">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/mvc/overview/security/)
- [<span data-ttu-id="ec41f-126">ClaimsPrincipal. Current öğesinden geçir</span><span class="sxs-lookup"><span data-stu-id="ec41f-126">Migrate from ClaimsPrincipal.Current</span></span>](/aspnet/core/migration/claimsprincipal-current)
- [<span data-ttu-id="ec41f-127">ASP.NET Core yetkilendirme için giriş</span><span class="sxs-lookup"><span data-stu-id="ec41f-127">Introduction to Authorization in ASP.NET Core</span></span>](/aspnet/core/security/authorization/introduction)

>[!div class="step-by-step"]
><span data-ttu-id="ec41f-128">[Önceki](webapi-differences.md) 
> [Sonraki](identity-differences.md)</span><span class="sxs-lookup"><span data-stu-id="ec41f-128">[Previous](webapi-differences.md)
[Next](identity-differences.md)</span></span>
