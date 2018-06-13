---
title: .NET mikro ve web uygulamaları hakkında yetkilendirme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET mikro ve web uygulamaları hakkında yetkilendirme
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2ea56f5a28d115fc5d91a98604b82565c8bf5c78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582827"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="7fa3d-103">.NET mikro ve web uygulamaları hakkında yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="7fa3d-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="7fa3d-104">Kimlik doğrulamasından sonra ASP.NET çekirdek Web API'lerine erişim yetkisi vermek gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="7fa3d-105">Bu işlem, bazı kimliği doğrulanmış kullanıcılar için kullanılabilir, ancak değil tüm API'leri yapmak bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="7fa3d-106">[Yetkilendirme](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) kullanıcıların rollerini tabanlı Bitti veya, talep veya diğer buluşsal yöntemler inceleniyor içerebilen özel ilkesini temel alarak.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-106">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="7fa3d-107">Bir Authorize özniteliği eylem yöntemine (veya denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa denetleyicinin sınıf), aşağıdaki gösterildiği örnek olarak uygulama olarak, bir ASP.NET Core MVC rotaya erişimi kısıtlama kadar kolaydır:</span><span class="sxs-lookup"><span data-stu-id="7fa3d-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="7fa3d-108">Varsayılan olarak, parametresiz bir Authorize özniteliği eklemek, denetleyici veya eylem için kimliği doğrulanmış kullanıcılara erişimi sınırlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="7fa3d-109">Daha fazla yalnızca belirli kullanıcılar için kullanılabilir olması için bir API kısıtlamak için özniteliği gerekli rolleri veya kullanıcıların getirmelidir ilkeleri belirtmek için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="7fa3d-110">Rol tabanlı yetkilendirme uygulama</span><span class="sxs-lookup"><span data-stu-id="7fa3d-110">Implementing role-based authorization</span></span>

<span data-ttu-id="7fa3d-111">ASP.NET Core kimliği rolleri yerleşik bir kavramı vardır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="7fa3d-112">Kullanıcılar, ek olarak ASP.NET Core kimliği uygulama tarafından kullanılan farklı rolleri hakkında bilgi depolar ve hangi kullanıcıların hangi rollerine atanan izler.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="7fa3d-113">Bu atamaları RoleManager türü (olan kalıcı depolama rollerinde güncelleştirmeleri) ve (atayabilir veya rolleri kullanıcılardan atamasını) UserManager türü ile programlı olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-113">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="7fa3d-114">JWT taşıyıcı belirteçleri ile kimlik doğrulaması, ASP.NET Core JWT taşıyıcı kimlik doğrulaması ara yazılımı belirteç bulundu rol talepleri dayalı bir kullanıcının rollerini doldurur.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-114">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="7fa3d-115">Bir MVC eylem veya denetleyici belirli roller kullanıcılara erişimi sınırlamak için bir rol parametresi Authorize üstbilgisinde aşağıdaki örnekte gösterildiği gibi içerebilir:</span><span class="sxs-lookup"><span data-stu-id="7fa3d-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="7fa3d-116">Bu örnekte, (örneğin SetTime eylemi yürütürken) ControlPanel denetleyicideki API'leri yalnızca yönetici veya PowerUser rollerdeki kullanıcılar erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="7fa3d-117">Kapatma API yönetici rolünde kullanıcılar yalnızca erişmesine izin vermek için daha fazla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="7fa3d-118">Bir kullanıcının birden çok rollerinde olması zorunlu kılmak için aşağıdaki örnekte gösterildiği gibi birden çok Authorize öznitelik kullanın:</span><span class="sxs-lookup"><span data-stu-id="7fa3d-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="7fa3d-119">Bu örnekte, API1, çağırmak için bir kullanıcı gerekir:</span><span class="sxs-lookup"><span data-stu-id="7fa3d-119">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="7fa3d-120">Yönetici olması *veya* PowerUser rol *ve*</span><span class="sxs-lookup"><span data-stu-id="7fa3d-120">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="7fa3d-121">RemoteEmployee rolünde olması *ve*</span><span class="sxs-lookup"><span data-stu-id="7fa3d-121">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="7fa3d-122">CustomPolicy yetkilendirme için özel bir işleyici karşılar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="7fa3d-123">İlke tabanlı bir yetkilendirme uygulama</span><span class="sxs-lookup"><span data-stu-id="7fa3d-123">Implementing policy-based authorization</span></span>

<span data-ttu-id="7fa3d-124">Özel Yetkilendirme kuralları da yazılabilir kullanarak [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="7fa3d-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="7fa3d-125">Bu bölümde genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-125">In this section we provide an overview.</span></span> <span data-ttu-id="7fa3d-126">Daha ayrıntılı çevrimiçi olarak kullanılabilir [ASP.NET yetkilendirme Atölye](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="7fa3d-126">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="7fa3d-127">Özel yetkilendirme ilkeleri kullanarak hizmet Startup.ConfigureServices yönteminde kaydedilir. AddAuthorization yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="7fa3d-128">Bu yöntem AuthorizationOptions bağımsız değişken yapılandırır bir temsilciyi alır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="7fa3d-129">Örnekte gösterildiği gibi ilkeleri farklı gereksinimleri türleri ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="7fa3d-130">İlkeleri kaydedildikten sonra bunlar bir eylem veya denetleyici ilkenin adı Authorize özniteliği ilke bağımsız değişken olarak geçirerek uygulanabilir (örneğin, \[Authorize(Policy="EmployeesOnly")\]) İlkeleri olabilir birden çok gereksinimleri, yalnızca bir tane değil (Bu örneklerde gösterildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="7fa3d-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="7fa3d-131">Önceki örnekte, ilk AddPolicy çağrı role göre yetkilendirme sadece bir alternatif yoludur.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="7fa3d-132">Varsa \[Authorize(Policy="AdministratorsOnly")\] Yönetici rolü kullanıcılar buna erişebilir yalnızca bir API için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-132">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="7fa3d-133">İkinci AddPolicy çağrı kullanıcı için belirli bir talep bulunmalı istemek için kolay bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-133">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="7fa3d-134">RequireClaim yöntemi ayrıca isteğe bağlı olarak talep beklenen değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-134">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="7fa3d-135">Değerleri belirtilirse, yalnızca kullanıcının hem doğru türde bir talep ve belirtilen değerlerden biri varsa bu gereksinimi karşılarsınız.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="7fa3d-136">JWT taşıyıcı kimlik doğrulaması ara yazılımı kullanıyorsanız, kullanıcı talepleri tüm JWT özellikleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-136">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="7fa3d-137">Özel yetkilendirme gereksinimi kullandığından burada gösterilen en ilginç üçüncü AddPolicy yönteminde ilkesidir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-137">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="7fa3d-138">Özel yetkilendirme gereksinimleri kullanarak, büyük bir bölümünü yetkilendirme nasıl gerçekleştirildiğini üzerinde denetime sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="7fa3d-139">Bunun çalışması için bu tür uygulamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7fa3d-139">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="7fa3d-140">IAuthorizationRequirement türetilen ve alanları gereksinim ayrıntılarını belirtme içeren gereksinimleri türü.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-140">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="7fa3d-141">Örnekte, bu yaş örnek MinimumAgeRequirement türü için bir alandır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-141">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="7fa3d-142">AuthorizationHandler uygulayan bir işleyici&lt;T&gt;, burada T işleyici karşılayabilen IAuthorizationRequirement türüdür.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-142">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="7fa3d-143">İşleyici kullanıcı hakkındaki bilgileri içeren belirtilen bir bağlam gereksinimini karşılayıp karşılamadığını denetler HandleRequirementAsync yöntemi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-143">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="7fa3d-144">Kullanıcı bağlamı için bir çağrı gereksinimi karşılıyorsa. İşlem başarılı kullanıcı yetkili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-144">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="7fa3d-145">Bir kullanıcı bir kimlik doğrulama gereksinimini karşılayan birden çok yol varsa, birden çok işleyici oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa3d-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="7fa3d-146">Özel ilke gereksinimlerini AddPolicy aramaları kaydetmeye ek olarak, ayrıca özel gereksinim işleyicilerini bağımlılık ekleme (Hizmetleri. aracılığıyla kaydetmesine izin gerekir AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="7fa3d-146">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="7fa3d-147">Özel yetkilendirme gereksinimi ve (DateOfBirth talebe göre) kullanıcının yaş denetleme işleyici örneği ASP.NET çekirdek kullanılabilir [yetkilendirme belgelerine](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="7fa3d-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7fa3d-148">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7fa3d-148">Additional resources</span></span>

-   <span data-ttu-id="7fa3d-149">**ASP.NET Core kimlik doğrulaması**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-149">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="7fa3d-150">**ASP.NET Core yetkilendirme**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-150">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="7fa3d-151">**Rol tabanlı yetkilendirme**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-151">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="7fa3d-152">**Özel ilke tabanlı yetkilendirme**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-152">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="7fa3d-153">[Önceki] (index.md) [sonraki] (Geliştirici-app-gizli-storage.md)</span><span class="sxs-lookup"><span data-stu-id="7fa3d-153">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
