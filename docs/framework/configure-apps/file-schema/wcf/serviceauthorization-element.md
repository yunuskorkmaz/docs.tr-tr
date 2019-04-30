---
title: <serviceAuthorization> öğesi
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: 7099c5eca9cf28624153a705e4e16136628214a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670358"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="41e25-102">\<serviceAuthorization > öğesi</span><span class="sxs-lookup"><span data-stu-id="41e25-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="41e25-103">Hizmet işlemleri erişim yetkisi ayarlarını belirtir</span><span class="sxs-lookup"><span data-stu-id="41e25-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="41e25-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41e25-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="41e25-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="41e25-105">\<behaviors></span></span>  
<span data-ttu-id="41e25-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="41e25-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="41e25-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="41e25-107">\<behavior></span></span>  
<span data-ttu-id="41e25-108">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="41e25-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e25-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41e25-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41e25-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41e25-110">Attributes and Elements</span></span>  
 <span data-ttu-id="41e25-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41e25-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41e25-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41e25-112">Attributes</span></span>  
  
|<span data-ttu-id="41e25-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41e25-113">Attribute</span></span>|<span data-ttu-id="41e25-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41e25-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41e25-115">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="41e25-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="41e25-116">Hizmetteki tüm işlemlerin çağıranın kimliğine bürünüp bürünmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="41e25-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="41e25-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="41e25-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="41e25-118">Belirli bir hizmet işlemine çağıranın kimliğine bürünür, iş parçacığı bağlamını, belirtilen hizmet yürütmeden önce çağıranın bağlamına anahtarlanır.</span><span class="sxs-lookup"><span data-stu-id="41e25-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="41e25-119">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="41e25-119">principalPermissionMode</span></span>|<span data-ttu-id="41e25-120">Sunucu üzerinde işlem gerçekleştirmek için kullanılan asıl öğeleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="41e25-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="41e25-121">Değerler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="41e25-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="41e25-122">-Yok</span><span class="sxs-lookup"><span data-stu-id="41e25-122">-   None</span></span><br /><span data-ttu-id="41e25-123">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="41e25-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="41e25-124">-   UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="41e25-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="41e25-125">-Özel</span><span class="sxs-lookup"><span data-stu-id="41e25-125">-   Custom</span></span><br /><br /> <span data-ttu-id="41e25-126">UseWindowsGroups varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="41e25-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="41e25-127">Değer türünde <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="41e25-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="41e25-128">Bu öznitelik kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="41e25-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="41e25-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="41e25-129">roleProviderName</span></span>|<span data-ttu-id="41e25-130">Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısının adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="41e25-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="41e25-131">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="41e25-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="41e25-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="41e25-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="41e25-133">Hizmet Yetkilendirme Yöneticisi türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="41e25-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="41e25-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="41e25-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41e25-135">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41e25-135">Child Elements</span></span>  
  
|<span data-ttu-id="41e25-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="41e25-136">Element</span></span>|<span data-ttu-id="41e25-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41e25-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41e25-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="41e25-138">authorizationPolicies</span></span>|<span data-ttu-id="41e25-139">Hangi kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir `add` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="41e25-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="41e25-140">Gereken tek bir her yetkilendirme ilkesi içeren `policyType` dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="41e25-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="41e25-141">Öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="41e25-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="41e25-142">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="41e25-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="41e25-143">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="41e25-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41e25-144">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41e25-144">Parent Elements</span></span>  
  
|<span data-ttu-id="41e25-145">Öğe</span><span class="sxs-lookup"><span data-stu-id="41e25-145">Element</span></span>|<span data-ttu-id="41e25-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41e25-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41e25-147">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="41e25-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="41e25-148">İçin bir hizmet davranışı ayar koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="41e25-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41e25-149">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41e25-149">Remarks</span></span>  
 <span data-ttu-id="41e25-150">Bu bölümde, kimliğe bürünme yetkilendirme ve özel rol sağlayıcıları etkileyen öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="41e25-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="41e25-151">`principalPermissionMode` Özniteliği, korumalı bir yöntem kullanımını yetkilendirirken kullanmak için kullanıcı gruplarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41e25-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="41e25-152">Varsayılan değer `UseWindowsGroups` ve "Yöneticiler" veya "Kullanıcılar" gibi Windows gruplarını bir kaynağa erişmeye çalışırken bir kimlik için aranır belirtir.</span><span class="sxs-lookup"><span data-stu-id="41e25-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="41e25-153">Ayrıca belirtebileceğiniz `UseAspNetRoles` altında yapılandırılmış bir özel rol sağlayıcıyı kullanacak şekilde \<system.web > öğesi, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="41e25-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="41e25-154">Aşağıdaki kodda gösterildiği `roleProviderName` ile kullanılan `principalPermissionMode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="41e25-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="41e25-155">Bu yapılandırma öğesini kullanarak bir ayrıntılı örnek için bkz: [hizmet işlemlerine erişimi yetkilendirme](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="41e25-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e25-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41e25-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="41e25-157">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="41e25-157">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="41e25-158">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="41e25-158">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="41e25-159">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="41e25-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="41e25-160">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="41e25-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="41e25-161">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="41e25-161">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
