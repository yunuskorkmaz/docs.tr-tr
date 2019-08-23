---
title: <serviceAuthorization> öğesi
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b73e2049afb460bf9be8b76ee272ba0547b61453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936389"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="6f996-102">\<serviceAuthorization > öğesi</span><span class="sxs-lookup"><span data-stu-id="6f996-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="6f996-103">Hizmet işlemlerine erişim yetkisi veren ayarları belirtir</span><span class="sxs-lookup"><span data-stu-id="6f996-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="6f996-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6f996-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f996-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6f996-105">\<behaviors></span></span>  
<span data-ttu-id="6f996-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6f996-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6f996-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6f996-107">\<behavior></span></span>  
<span data-ttu-id="6f996-108">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="6f996-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f996-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f996-109">Syntax</span></span>  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f996-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f996-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6f996-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f996-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f996-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6f996-112">Attributes</span></span>  
  
|<span data-ttu-id="6f996-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6f996-113">Attribute</span></span>|<span data-ttu-id="6f996-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f996-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f996-115">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="6f996-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="6f996-116">Hizmette tüm işlemlerin çağıranın kimliğine bürünmesini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6f996-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="6f996-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="6f996-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="6f996-118">Belirli bir hizmet işlemi çağıranı taklit ettiğinde, belirtilen hizmeti yürütmeden önce iş parçacığı bağlamı arayan bağlamına geçiş yapılır.</span><span class="sxs-lookup"><span data-stu-id="6f996-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="6f996-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="6f996-119">principalPermissionMode</span></span>|<span data-ttu-id="6f996-120">Sunucuda işlemleri yürütmek için kullanılan sorumluyu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6f996-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="6f996-121">Değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6f996-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="6f996-122">-Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="6f996-122">-   None</span></span><br /><span data-ttu-id="6f996-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="6f996-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="6f996-124">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="6f996-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="6f996-125">-Özel</span><span class="sxs-lookup"><span data-stu-id="6f996-125">-   Custom</span></span><br /><br /> <span data-ttu-id="6f996-126">Varsayılan değer UseWindowsGroups değeridir.</span><span class="sxs-lookup"><span data-stu-id="6f996-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="6f996-127">Değer, türündedir <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="6f996-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="6f996-128">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: PrincipalPermissionAttribute sınıfıyla](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)erişimi kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="6f996-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="6f996-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="6f996-129">roleProviderName</span></span>|<span data-ttu-id="6f996-130">Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="6f996-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="6f996-131">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="6f996-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="6f996-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="6f996-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="6f996-133">Hizmet Yetkilendirme Yöneticisi türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="6f996-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="6f996-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="6f996-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f996-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f996-135">Child Elements</span></span>  
  
|<span data-ttu-id="6f996-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f996-136">Element</span></span>|<span data-ttu-id="6f996-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f996-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f996-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="6f996-138">authorizationPolicies</span></span>|<span data-ttu-id="6f996-139">`add` Anahtar sözcüğü kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="6f996-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="6f996-140">Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="6f996-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="6f996-141">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f996-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="6f996-142">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="6f996-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="6f996-143">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="6f996-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f996-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6f996-144">Parent Elements</span></span>  
  
|<span data-ttu-id="6f996-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f996-145">Element</span></span>|<span data-ttu-id="6f996-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f996-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f996-147">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6f996-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6f996-148">Bir hizmetin davranışı için ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6f996-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f996-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f996-149">Remarks</span></span>  
 <span data-ttu-id="6f996-150">Bu bölüm yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme işlemlerini etkileyen öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6f996-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="6f996-151">Özniteliği `principalPermissionMode` , korumalı bir yöntemin kullanımını yetkilendirirken kullanılacak kullanıcı gruplarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f996-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="6f996-152">Varsayılan değer ' dir `UseWindowsGroups` ve bir kaynağa erişmeye çalışan bir kimlik için "Yöneticiler" veya "kullanıcılar" gibi Windows gruplarının arandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f996-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="6f996-153">Ayrıca, aşağıdaki kodda `UseAspNetRoles` gösterildiği gibi, \<System. Web > öğesi altında yapılandırılmış özel bir rol sağlayıcısı kullanmayı da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f996-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 <span data-ttu-id="6f996-154">Aşağıdaki kod, `principalPermissionMode` özniteliğiyle birlikte `roleProviderName` kullanılan öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f996-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="6f996-155">Bu yapılandırma öğesinin kullanımına ilişkin ayrıntılı bir örnek için bkz. [hizmet işlemlerine](../../../wcf/samples/authorizing-access-to-service-operations.md) ve [Yetkilendirme ilkesine](../../../wcf/samples/authorization-policy.md)erişimi yetkilendirme.</span><span class="sxs-lookup"><span data-stu-id="6f996-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f996-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f996-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="6f996-157">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="6f996-157">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6f996-158">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="6f996-158">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="6f996-159">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f996-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="6f996-160">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="6f996-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="6f996-161">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="6f996-161">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
