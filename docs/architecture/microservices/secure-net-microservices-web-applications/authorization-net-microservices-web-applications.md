---
title: .NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-ASP.NET Core uygulamalar-rol tabanlı ve ilke tabanlı başlıca yetkilendirme seçeneklerine genel bakış alın.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296470"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="21b3e-103">.NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında</span><span class="sxs-lookup"><span data-stu-id="21b3e-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="21b3e-104">Kimlik doğrulamasından sonra, ASP.NET Core Web API 'Lerinin erişimi yetkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="21b3e-105">Bu işlem, bir hizmetin API 'Leri bazı kimliği doğrulanmış kullanıcılar için kullanılabilir olmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="21b3e-106">[Yetkilendirme](/aspnet/core/security/authorization/introduction) , kullanıcıların rollerine göre veya özel ilkeye göre yapılabilir ve bu da talepleri veya diğer buluşsal yöntemleri inceleyerek olabilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="21b3e-107">Bir ASP.NET Core MVC yoluna erişimi kısıtlamak, aşağıdaki örnekte gösterildiği gibi, eylem yöntemine (veya denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa denetleyicinin sınıfına) bir yetkilendirme özniteliği uygulamanın kolay bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="21b3e-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="21b3e-108">Varsayılan olarak, parametresiz bir yetkilendirme özniteliği eklemek, bu denetleyici veya eylem için kimliği doğrulanmış kullanıcılara göre sınırlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="21b3e-109">Bir API 'yi yalnızca belirli kullanıcılar için kullanılabilir olacak şekilde kısıtlamak için, bu öznitelik, kullanıcıların karşılaması gereken rolleri veya ilkeleri belirtmek için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="21b3e-110">Rol tabanlı yetkilendirme uygulama</span><span class="sxs-lookup"><span data-stu-id="21b3e-110">Implement role-based authorization</span></span>

<span data-ttu-id="21b3e-111">ASP.NET Core kimliğin yerleşik bir rol kavramı vardır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="21b3e-112">Kullanıcıların yanı sıra, ASP.NET Core kimlik, uygulama tarafından kullanılan farklı rollerle ilgili bilgileri depolar ve hangi kullanıcıların hangi rollere atandığını izler.</span><span class="sxs-lookup"><span data-stu-id="21b3e-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="21b3e-113">Bu atamalar, kalıcı depolama alanındaki rolleri güncelleştiren `RoleManager` türü ile program aracılığıyla değiştirilebilir ve kullanıcılara roller verebilir veya bunları iptal edebilir `UserManager` türü.</span><span class="sxs-lookup"><span data-stu-id="21b3e-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="21b3e-114">JWT taşıyıcı belirteçleriyle kimlik doğrulaması yapıyorsanız, ASP.NET Core JWT taşıyıcı kimlik doğrulama ara yazılımı, bir kullanıcının rollerini belirteçte bulunan rol taleplerini temel alarak doldurur.</span><span class="sxs-lookup"><span data-stu-id="21b3e-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="21b3e-115">Belirli rollerdeki kullanıcılarla bir MVC eylemine veya denetleyiciye erişimi sınırlandırmak için, yetkilendirme ek açıklamasına (öznitelik) aşağıdaki kod parçasında gösterildiği gibi bir rol parametresi dahil edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="21b3e-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="21b3e-116">Bu örnekte, yalnızca yönetici veya PowerUser rollerinin kullanıcıları ControlPanel denetleyicisindeki (SetTime eylemini yürütme gibi) API 'Lere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="21b3e-117">Kapanmaya yönelik API, yalnızca yönetici rolündeki kullanıcılara erişime izin verecek şekilde kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="21b3e-118">Bir kullanıcının birden çok rolde olmasını gerektirmek için, aşağıdaki örnekte gösterildiği gibi birden çok yetkilendirme özniteliği kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="21b3e-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="21b3e-119">Bu örnekte, API1 çağırmak için bir kullanıcının şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="21b3e-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="21b3e-120">Yönetici *veya* PowerUseR rolünde olun *ve*</span><span class="sxs-lookup"><span data-stu-id="21b3e-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="21b3e-121">RemoteEmployee rolünde olun *ve*</span><span class="sxs-lookup"><span data-stu-id="21b3e-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="21b3e-122">CustomPolicy yetkilendirmesi için özel bir işleyici karşılanacak.</span><span class="sxs-lookup"><span data-stu-id="21b3e-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="21b3e-123">İlke tabanlı yetkilendirme uygulama</span><span class="sxs-lookup"><span data-stu-id="21b3e-123">Implement policy-based authorization</span></span>

<span data-ttu-id="21b3e-124">Özel yetkilendirme kuralları, [Yetkilendirme İlkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html)kullanılarak da yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="21b3e-125">Bu bölümde genel bakış sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-125">This section provides an overview.</span></span> <span data-ttu-id="21b3e-126">Daha fazla bilgi için bkz. [ASP.net Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="21b3e-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="21b3e-127">Özel yetkilendirme ilkeleri hizmeti kullanılarak Startup. ConfigureServices yöntemine kaydedilir. Addaduthorleştirme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21b3e-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="21b3e-128">Bu yöntem, AuthorizationOptions bağımsız değişkenini yapılandıran bir temsilci alır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="21b3e-129">Örnekte gösterildiği gibi, ilkeler farklı tür gereksinimlerle ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="21b3e-130">İlkeler kaydedildikten sonra, yetkilendirme özniteliğinin Ilke bağımsız değişkeni olarak ilke adını geçirerek bir eyleme veya denetleyiciye uygulanabilir (örneğin, `[Authorize(Policy="EmployeesOnly")]`) Ilkeler yalnızca bir tane değil birden çok gereksinimi olabilir (Bu örneklerde gösterildiği gibi).</span><span class="sxs-lookup"><span data-stu-id="21b3e-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="21b3e-131">Önceki örnekte, ilk AddPolicy çağrısı role göre yetkilendirmek için yalnızca alternatif bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="21b3e-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="21b3e-132">Bir API 'ye `[Authorize(Policy="AdministratorsOnly")]` uygulanmışsa, yalnızca yönetici rolündeki kullanıcılar erişebilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="21b3e-133">İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> çağrısı, Kullanıcı için belirli bir talebin mevcut olmasını gerektirmek için kolay bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="21b3e-134"><xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> yöntemi talep için de isteğe bağlı olarak beklenen değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="21b3e-135">Değerler belirtilmişse, gereksinim yalnızca Kullanıcı doğru türde ve belirtilen değerlerden birine ait bir talebe sahipse karşılanır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="21b3e-136">JWT taşıyıcı kimlik doğrulama ara yazılımını kullanıyorsanız, tüm JWT özellikleri kullanıcı talepleri olarak kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="21b3e-137">Burada gösterilen en ilginç ilke, özel bir yetkilendirme gereksinimi kullandığından, üçüncü `AddPolicy` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="21b3e-138">Özel yetkilendirme gereksinimlerini kullanarak, yetkilendirmenin nasıl gerçekleştirileceği konusunda harika bir denetim sahibi olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21b3e-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="21b3e-139">Bunun çalışması için bu türleri uygulamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="21b3e-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="21b3e-140"><xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> türetilen ve gereksinimin ayrıntılarını belirten alanlar içeren bir gereksinim türü.</span><span class="sxs-lookup"><span data-stu-id="21b3e-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="21b3e-141">Örnekte bu, örnek `MinimumAgeRequirement` türü için bir yaş alanıdır.</span><span class="sxs-lookup"><span data-stu-id="21b3e-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="21b3e-142"><xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>uygulayan bir işleyici; burada T, işleyicinin karşılayabileceği <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> türüdür.</span><span class="sxs-lookup"><span data-stu-id="21b3e-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="21b3e-143">İşleyicinin, Kullanıcı hakkında bilgi içeren belirtilen bağlamın gereksinimi karşılayıp karşılamadığını denetleyen <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> yöntemini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="21b3e-144">Kullanıcı, gereksinimi karşılıyorsa, `context.Succeed` çağrısı kullanıcının yetkili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="21b3e-145">Bir kullanıcının bir yetkilendirme gereksinimini karşılayabilmesi için birden çok yol varsa, birden çok işleyici oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="21b3e-146">Özel ilke gereksinimlerinin `AddPolicy` çağrılarıyla kaydedilmesinin yanı sıra, bağımlılık ekleme (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) aracılığıyla özel gereksinim işleyicilerini de kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="21b3e-147">Bir kullanıcının yaşını (bir `DateOfBirth` talebine göre) denetlemeye yönelik özel bir yetkilendirme gereksinimi ve işleyicinin bir örneği ASP.NET Core [Yetkilendirme belgelerinde](https://docs.asp.net/en/latest/security/authorization/policies.html)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="21b3e-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="21b3e-148">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="21b3e-148">Additional resources</span></span>

- <span data-ttu-id="21b3e-149">**ASP.NET Core kimlik doğrulaması** </span><span class="sxs-lookup"><span data-stu-id="21b3e-149">**ASP.NET Core Authentication** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="21b3e-150">**ASP.NET Core yetkilendirme** </span><span class="sxs-lookup"><span data-stu-id="21b3e-150">**ASP.NET Core Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="21b3e-151">**Rol tabanlı yetkilendirme** </span><span class="sxs-lookup"><span data-stu-id="21b3e-151">**Role-based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="21b3e-152">**Özel Ilke tabanlı yetkilendirme** </span><span class="sxs-lookup"><span data-stu-id="21b3e-152">**Custom Policy-Based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="21b3e-153">[Önceki](index.md)
>[İleri](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="21b3e-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
