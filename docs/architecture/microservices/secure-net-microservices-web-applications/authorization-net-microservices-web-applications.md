---
title: .NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında
description: .NET Microservices ve Web Applications güvenlik - ASP.NET Core uygulamalarında ana yetkilendirme seçeneklerine genel bir bakış alın - rol tabanlı ve politika tabanlı.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f6b69faceac9a9b4819212cc04f89080f3ddad56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501775"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="26b9a-103">.NET mikro hizmet ve web uygulamalarında yetkilendirme hakkında</span><span class="sxs-lookup"><span data-stu-id="26b9a-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="26b9a-104">Kimlik doğrulamadan sonra, ASP.NET Core Web API'leri erişim yetkisi gerekir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="26b9a-105">Bu işlem, bir hizmetin API'leri bazı kimlik doğrulaması yapılan kullanıcılar için kullanılabilir hale getirmenize, ancak tümüne değil, tümüne olanak sağlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="26b9a-106">[Yetkilendirme,](/aspnet/core/security/authorization/introduction) kullanıcıların rollerine veya talepleri veya diğer buluşsal incelemeleri incelemeyi içerebilecek özel ilkelere dayalı olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="26b9a-107">ASP.NET Core MVC rotasına erişimi kısıtlamak, aşağıdaki örnekte gösterildiği gibi, eylem yöntemine (veya denetleyicinin tüm eylemleri yetkilendirme gerektiriyorsa denetleyicinin sınıfına) bir Yetkilendirme özniteliği uygulamak kadar kolaydır:</span><span class="sxs-lookup"><span data-stu-id="26b9a-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="26b9a-108">Varsayılan olarak, parametrelerolmadan bir Yetkilendirme özniteliği eklemek, bu denetleyici veya eylem için kimlik doğrulaması yapılan kullanıcılara erişimi sınırlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="26b9a-109">Bir API'nin yalnızca belirli kullanıcılar için kullanılabilir olmasını daha fazla kısıtlamak için, öznitelik, kullanıcıların karşılaması gereken rolleri veya ilkeleri belirtmek için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="26b9a-110">Rol tabanlı yetkilendirmeyi uygulama</span><span class="sxs-lookup"><span data-stu-id="26b9a-110">Implement role-based authorization</span></span>

<span data-ttu-id="26b9a-111">ASP.NET Çekirdek Kimlik rolleri yerleşik bir kavram vardır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="26b9a-112">ASP.NET Çekirdek Kimlik, kullanıcılara ek olarak uygulama tarafından kullanılan farklı roller hakkında bilgi depolar ve hangi kullanıcıların hangi rollere atandığını izler.</span><span class="sxs-lookup"><span data-stu-id="26b9a-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="26b9a-113">Bu atamalar, kalıcı depolamadaki `RoleManager` rolleri güncelleyen tür ve kullanıcılardan `UserManager` roller veren veya iptal edebilen türle programlı olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="26b9a-114">JWT taşıyıcı belirteçleri ile kimlik doğrulaması iseniz, ASP.NET Core JWT taşıyıcı kimlik doğrulama aracı belirteç bulunan rol iddialarına dayalı olarak kullanıcının rollerini dolduracaktır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="26b9a-115">Bir MVC eylemine veya denetleyicisine erişimi belirli rollerdeki kullanıcılarla sınırlamak için, aşağıdaki kod parçasında gösterildiği gibi Yetkilendirme ek açıklamasına (öznitelik) bir Rol parametresi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="26b9a-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="26b9a-116">Bu örnekte, Yalnızca Administrator veya PowerUser rollerindeki kullanıcılar ControlPanel denetleyicisinde (SetTime eylemini yürütme gibi) API'lara erişebilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="26b9a-117">Kapatma API'si, yalnızca Yönetici rolündeki kullanıcılara erişime izin vermek için daha da kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="26b9a-118">Bir kullanıcının birden çok rolde olmasını sağlamak için, aşağıdaki örnekte gösterildiği gibi birden çok Yetkilendirme özniteliği kullanırsınız:</span><span class="sxs-lookup"><span data-stu-id="26b9a-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="26b9a-119">Bu örnekte, API1'i aramak için bir kullanıcının şunları yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="26b9a-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="26b9a-120">Administrator *veya* PowerUser rolünde olun *ve*</span><span class="sxs-lookup"><span data-stu-id="26b9a-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="26b9a-121">RemoteEmployee rolünde olun *ve*</span><span class="sxs-lookup"><span data-stu-id="26b9a-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="26b9a-122">CustomPolicy yetkilendirmesi için özel bir işleyiciyi karşıla.</span><span class="sxs-lookup"><span data-stu-id="26b9a-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="26b9a-123">İlke tabanlı yetkilendirmeyi uygulama</span><span class="sxs-lookup"><span data-stu-id="26b9a-123">Implement policy-based authorization</span></span>

<span data-ttu-id="26b9a-124">Özel yetkilendirme kuralları yetkilendirme [ilkeleri](https://docs.asp.net/en/latest/security/authorization/policies.html)kullanılarak da yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="26b9a-125">Bu bölüme genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="26b9a-125">This section provides an overview.</span></span> <span data-ttu-id="26b9a-126">Daha fazla bilgi için [ASP.NET Yetkilendirme Çalıştayı'na](https://github.com/blowdart/AspNetAuthorizationWorkshop)bakın.</span><span class="sxs-lookup"><span data-stu-id="26b9a-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="26b9a-127">Özel yetkilendirme ilkeleri, hizmeti kullanarak Başlangıç.ConfigureServices yönteminde kaydedilir. Yetkilendirme ekleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="26b9a-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="26b9a-128">Bu yöntem, Yetkilendirme Seçenekleri bağımsız değişkenini yapılandıran bir temsilci alır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="26b9a-129">Örnekte gösterildiği gibi, ilkeler farklı gereksinim türleri ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="26b9a-130">İlkeler kaydedildikten sonra, bir eyleme veya denetleyiciye, ilkeğin adını Yetkilendirilen özniteliğin İlkes `[Authorize(Policy="EmployeesOnly")]`bağımsız değişkeni olarak geçirerek (örneğin, ) İlkelerin yalnızca bir gereksinimi değil, birden çok gereksinimi olabilir (bu örneklerde gösterildiği gibi) uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="26b9a-131">Önceki örnekte, ilk AddPolicy çağrısı role göre yetkilendirmenin alternatif bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="26b9a-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="26b9a-132">Bir `[Authorize(Policy="AdministratorsOnly")]` API'ye uygulanırsa, yalnızca Yönetici rolündeki kullanıcılar bu apiye erişebilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="26b9a-133">İkinci <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> arama, kullanıcı için belirli bir talebin bulunmasını gerektiren kolay bir yol olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="26b9a-134">Yöntem <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> de isteğe bağlı olarak talep için beklenen değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="26b9a-135">Değerler belirtilirse, gereksinim yalnızca kullanıcının hem doğru türde hem de belirtilen değerlerden birine sahip olması durumunda karşılanır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="26b9a-136">JWT taşıyıcı kimlik doğrulama aracı kullanıyorsanız, tüm JWT özellikleri kullanıcı talepleri olarak kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="26b9a-137">Burada gösterilen en ilginç ilke, özel bir yetkilendirme gereksinimi kullandığından üçüncü `AddPolicy` yöntemdedir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="26b9a-138">Özel yetkilendirme gereksinimlerini kullanarak, yetkilendirmenin nasıl gerçekleştirildiği üzerinde büyük bir denetime sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b9a-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="26b9a-139">Bunun işe yaraması için şu türleri uygulamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="26b9a-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="26b9a-140">Gereksinimayrıntılarını belirten alanları içeren <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> ve bu gereksinimtüründen türeyen bir Gereksinim türü.</span><span class="sxs-lookup"><span data-stu-id="26b9a-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="26b9a-141">Örnekte, bu örnek `MinimumAgeRequirement` türü için bir yaş alanıdır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="26b9a-142"><xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>T'nin işleyicinin <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> karşılayabildiği tür olduğu bir işleyici.</span><span class="sxs-lookup"><span data-stu-id="26b9a-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="26b9a-143">İşleyici, kullanıcı <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> hakkında bilgi içeren belirli bir bağlamın gereksinimi karşılayıp karşılamadığını denetleyen yöntemi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="26b9a-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="26b9a-144">Kullanıcı gereksinimi karşılarsa, bir `context.Succeed` arama kullanıcının yetkili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="26b9a-145">Bir kullanıcının yetkilendirme gereksinimini karşılayabilen birden çok yolu varsa, birden çok işleyici oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="26b9a-146">Aramalar ile `AddPolicy` özel ilke gereksinimleri kaydetmeye ek olarak, ayrıca Bağımlılık Enjeksiyon (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`) ile özel gereksinim işleyicileri kayıt gerekir.</span><span class="sxs-lookup"><span data-stu-id="26b9a-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="26b9a-147">Özel yetkilendirme gereksinimi örneği ve kullanıcının yaşını denetlemek için işleyici `DateOfBirth` (bir iddiaya dayalı) ASP.NET Çekirdek yetkilendirme [belgelerinde](https://docs.asp.net/en/latest/security/authorization/policies.html)mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="26b9a-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="26b9a-148">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="26b9a-148">Additional resources</span></span>

- <span data-ttu-id="26b9a-149">**ASP.NET Çekirdek Kimlik Doğrulama** </span><span class="sxs-lookup"><span data-stu-id="26b9a-149">**ASP.NET Core Authentication** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="26b9a-150">**ASP.NET Çekirdek Yetkilendirme** </span><span class="sxs-lookup"><span data-stu-id="26b9a-150">**ASP.NET Core Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="26b9a-151">**Rol Tabanlı Yetkilendirme** </span><span class="sxs-lookup"><span data-stu-id="26b9a-151">**Role-based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="26b9a-152">**Özel İlke Tabanlı Yetkilendirme** </span><span class="sxs-lookup"><span data-stu-id="26b9a-152">**Custom Policy-Based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="26b9a-153">[Önceki](index.md)
>[Sonraki](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="26b9a-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
