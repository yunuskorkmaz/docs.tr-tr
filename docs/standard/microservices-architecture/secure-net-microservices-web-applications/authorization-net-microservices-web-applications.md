---
title: .NET mikro Hizmetleri ve web uygulamalarında yetkilendirme hakkında
description: .NET mikro Hizmetleri ve Web uygulamaları - güvenlik, ASP.NET Core uygulamaları - rol tabanlı ve ilke tabanlı ana yetkilendirme seçeneklerine genel bakış edinin.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466367"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="97280-103">.NET mikro Hizmetleri ve web uygulamalarında yetkilendirme hakkında</span><span class="sxs-lookup"><span data-stu-id="97280-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="97280-104">Kimlik doğrulamasından sonra ASP.NET Core Web API'lerine erişim yetkisi vermek gerekir.</span><span class="sxs-lookup"><span data-stu-id="97280-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="97280-105">Bu işlem, bazı kimliği doğrulanmış kullanıcılar tarafından kullanılabilir, ancak çok tüm API'leri yapmak bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="97280-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="97280-106">[Yetkilendirme](/aspnet/core/security/authorization/introduction) kullanıcıların rollere göre Bitti veya talep veya diğer buluşsal yöntemler inceleyerek içerebilir özel ilkesini temel alarak.</span><span class="sxs-lookup"><span data-stu-id="97280-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="97280-107">Bir Authorize özniteliği eylem yöntemine (veya denetleyicinin sınıf denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa), aşağıdaki gösterildiği örnek olarak uygulama olarak, bir ASP.NET Core MVC yönlendirme için erişimi kısıtlamak oldukça kolaydır:</span><span class="sxs-lookup"><span data-stu-id="97280-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="97280-108">Varsayılan olarak, parametresiz bir Authorize öznitelik ekleyerek bu denetleyici veya eylem için kimliği doğrulanmış kullanıcılara erişimi sınırlar.</span><span class="sxs-lookup"><span data-stu-id="97280-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="97280-109">Yalnızca belirli kullanıcılar için kullanılabilir olması için bir API daha da kısıtlamak için özniteliği gerekli rolleri veya kullanıcıları karşılamalıdır ilkeleri belirtmek için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="97280-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="97280-110">Uygulama rol tabanlı yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="97280-110">Implement role-based authorization</span></span>

<span data-ttu-id="97280-111">ASP.NET Core kimliği yerleşik bir rol kavramları vardır.</span><span class="sxs-lookup"><span data-stu-id="97280-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="97280-112">Kullanıcıların, yanı sıra ASP.NET Core kimliği uygulama tarafından kullanılan farklı roller hakkındaki bilgileri saklar ve hangi kullanıcıların hangi rollerine atandığı izler.</span><span class="sxs-lookup"><span data-stu-id="97280-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="97280-113">Bu atamaları ile program aracılığıyla değiştirilebilir `RoleManager` güncelleştiren rollerdeki kalıcı depolama türü ve `UserManager` verebilir veya kullanıcıların rollerini iptal türü.</span><span class="sxs-lookup"><span data-stu-id="97280-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="97280-114">JWT taşıyıcı belirteçleri ile kimlik doğrulaması, ASP.NET Core JWT taşıyıcı kimlik doğrulaması ara yazılımı belirteçte rol talepleri göre bir kullanıcının rollerini doldurur.</span><span class="sxs-lookup"><span data-stu-id="97280-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="97280-115">Bir MVC eylem veya denetleyici belirli roller kullanıcılara erişimi sınırlamak için bir rol parametresi Authorize açıklamada (öznitelik), aşağıdaki kod parçasını gösterildiği gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="97280-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="97280-116">Bu örnekte, yalnızca yönetici veya PowerUser rollerdeki kullanıcılar (örneğin SetTime eylemini yürütürken) ndaki denetleyici API'leri erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97280-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="97280-117">ShutDown API, yönetici rolünde yalnızca kullanıcı erişimine izin vermek için daha fazla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="97280-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="97280-118">Bir kullanıcı birden çok rol içinde olması gerekir için birden çok Authorize özniteliği aşağıdaki örnekte gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="97280-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="97280-119">Bu örnekte, bir kullanıcı API1, çağrılacak gerekir:</span><span class="sxs-lookup"><span data-stu-id="97280-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="97280-120">Yönetici olması *veya* PowerUser rol *ve*</span><span class="sxs-lookup"><span data-stu-id="97280-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="97280-121">RemoteEmployee rolünde olması *ve*</span><span class="sxs-lookup"><span data-stu-id="97280-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="97280-122">CustomPolicy yetkilendirme için özel bir işleyici karşılar.</span><span class="sxs-lookup"><span data-stu-id="97280-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="97280-123">İlke tabanlı yetkilendirme uygulayın</span><span class="sxs-lookup"><span data-stu-id="97280-123">Implement policy-based authorization</span></span>

<span data-ttu-id="97280-124">Özel Yetkilendirme kuralları da yazılabilir kullanarak [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="97280-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="97280-125">Bu bölümde, genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="97280-125">This section provides an overview.</span></span> <span data-ttu-id="97280-126">Daha fazla bilgi için [ASP.NET yetkilendirme Atölyesi](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="97280-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="97280-127">Özel Yetkilendirme İlkeleri Startup.ConfigureServices yöntemin hizmeti kullanılarak kaydedilir. AddAuthorization yöntemi.</span><span class="sxs-lookup"><span data-stu-id="97280-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="97280-128">Bu yöntem AuthorizationOptions bağımsız değişken yapılandıran bir temsilciyi alır.</span><span class="sxs-lookup"><span data-stu-id="97280-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="97280-129">Örnekte gösterildiği gibi ilkeleri farklı gereksinimleri ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="97280-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="97280-130">İlkeleri kaydolduktan sonra bir eylem veya denetleyici Authorize özniteliği ilke bağımsız değişkeni bir ilkenin adını geçirerek uygulanabilirler (örneğin, `[Authorize(Policy="EmployeesOnly")]`) İlkeleri (Bu gösterildiği gibi yalnızca bir tane değil birden çok gereksinimleri olabilir örnekler için).</span><span class="sxs-lookup"><span data-stu-id="97280-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="97280-131">Önceki örnekte, ilk AddPolicy çağrı role göre yetkilendirme yalnızca bir diğer yoludur.</span><span class="sxs-lookup"><span data-stu-id="97280-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="97280-132">Varsa `[Authorize(Policy="AdministratorsOnly")]` yönetici rolündeki kullanıcılar erişebilmesi için yalnızca bir API için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="97280-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="97280-133">İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> çağrı belirli bir talep kullanıcı için mevcut olduğunu istemek için kolay bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="97280-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="97280-134"><xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> Yöntemi ayrıca isteğe bağlı olarak talep için beklenen değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="97280-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="97280-135">Değer belirtilmişse, yalnızca kullanıcının hem doğru türde bir talep ve belirtilen değerlerden biri varsa bu gereksinimi karşılarsınız.</span><span class="sxs-lookup"><span data-stu-id="97280-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="97280-136">JWT taşıyıcı kimlik doğrulaması ara yazılımı kullanıyorsanız, kullanıcı talepleri tüm JWT özellikleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97280-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="97280-137">Üçüncü İşte gösterilen en ilginç ilke `AddPolicy` yöntemi, bir özel kimlik doğrulama gereksinimini kullandığından.</span><span class="sxs-lookup"><span data-stu-id="97280-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="97280-138">Özel yetkilendirme gereksinimleri kullanarak Yetkilendirme nasıl gerçekleştirildiğini denetim harika bir fırsat olabilir.</span><span class="sxs-lookup"><span data-stu-id="97280-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="97280-139">Bunun çalışması için bu tür uygulamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="97280-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="97280-140">Türetilen bir gereksinimleri türü <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> ve gereksinim ayrıntılarını belirtme alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="97280-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="97280-141">Örnekte, bu örnek için bir yaş alan olup, `MinimumAgeRequirement` türü.</span><span class="sxs-lookup"><span data-stu-id="97280-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="97280-142">Uygulayan bir işleyici <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, burada T türü <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> işleyici karşılayan.</span><span class="sxs-lookup"><span data-stu-id="97280-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="97280-143">İşleyici uygulamalıdır <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> yöntemi kullanıcı hakkındaki bilgileri içeren belirtilen bir bağlam gereksinimini karşılayıp karşılamadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="97280-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="97280-144">Kullanıcı, gereksinim, bir çağrı karşılayıp karşılamadığını `context.Succeed` kullanıcı yetki verildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="97280-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="97280-145">Bir kullanıcı bir kimlik doğrulama gereksinimini karşılayan birden çok yol varsa, birden fazla işleyici oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="97280-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="97280-146">Özel ilke gereksinimlerine kaydetme yanı sıra `AddPolicy` çağrılar da ihtiyacınız özel gereksinim işleyicilerine bağımlılık ekleme yoluyla kaydetmek (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span><span class="sxs-lookup"><span data-stu-id="97280-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="97280-147">Özel yetkilendirme gereksinimi ve denetimi bir kullanıcının yaşını işleyici örneği (dayalı bir `DateOfBirth` talep) içinde ASP.NET Core kullanılabilir [yetkilendirme belgeleri](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="97280-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="97280-148">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="97280-148">Additional resources</span></span>

- <span data-ttu-id="97280-149">**ASP.NET Core kimlik doğrulaması** \\</span><span class="sxs-lookup"><span data-stu-id="97280-149">**ASP.NET Core Authentication** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="97280-150">**ASP.NET Core yetkilendirme** \\</span><span class="sxs-lookup"><span data-stu-id="97280-150">**ASP.NET Core Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="97280-151">**Rol tabanlı yetkilendirme** \\</span><span class="sxs-lookup"><span data-stu-id="97280-151">**Role-based Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="97280-152">**Özel ilke tabanlı yetkilendirme** \\</span><span class="sxs-lookup"><span data-stu-id="97280-152">**Custom Policy-Based Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="97280-153">[Önceki](index.md)
>[İleri](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="97280-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
