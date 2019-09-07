---
title: <serviceAuthorization> öğesi
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b636b7006900ecff1be553cf32105df7cea7e800
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399700"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="fa8b3-102">\<serviceAuthorization > öğesi</span><span class="sxs-lookup"><span data-stu-id="fa8b3-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="fa8b3-103">Hizmet işlemlerine erişim yetkisi veren ayarları belirtir</span><span class="sxs-lookup"><span data-stu-id="fa8b3-103">Specifies settings that authorize access to service operations</span></span>  
  
<span data-ttu-id="fa8b3-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa8b3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fa8b3-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fa8b3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fa8b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fa8b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fa8b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fa8b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="fa8b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fa8b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="fa8b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="fa8b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa8b3-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa8b3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa8b3-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa8b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fa8b3-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa8b3-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa8b3-113">Attributes</span></span>  
  
|<span data-ttu-id="fa8b3-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa8b3-114">Attribute</span></span>|<span data-ttu-id="fa8b3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa8b3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa8b3-116">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="fa8b3-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="fa8b3-117">Hizmette tüm işlemlerin çağıranın kimliğine bürünmesini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="fa8b3-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="fa8b3-119">Belirli bir hizmet işlemi çağıranı taklit ettiğinde, belirtilen hizmeti yürütmeden önce iş parçacığı bağlamı arayan bağlamına geçiş yapılır.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="fa8b3-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="fa8b3-120">principalPermissionMode</span></span>|<span data-ttu-id="fa8b3-121">Sunucuda işlemleri yürütmek için kullanılan sorumluyu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="fa8b3-122">Değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fa8b3-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="fa8b3-123">-Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="fa8b3-123">-   None</span></span><br /><span data-ttu-id="fa8b3-124">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="fa8b3-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="fa8b3-125">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="fa8b3-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="fa8b3-126">-Özel</span><span class="sxs-lookup"><span data-stu-id="fa8b3-126">-   Custom</span></span><br /><br /> <span data-ttu-id="fa8b3-127">Varsayılan değer UseWindowsGroups değeridir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="fa8b3-128">Değer, türündedir <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="fa8b3-129">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: PrincipalPermissionAttribute sınıfıyla](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)erişimi kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="fa8b3-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="fa8b3-130">roleProviderName</span></span>|<span data-ttu-id="fa8b3-131">Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="fa8b3-132">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa8b3-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="fa8b3-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="fa8b3-134">Hizmet Yetkilendirme Yöneticisi türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="fa8b3-135">Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa8b3-136">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa8b3-136">Child Elements</span></span>  
  
|<span data-ttu-id="fa8b3-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa8b3-137">Element</span></span>|<span data-ttu-id="fa8b3-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa8b3-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa8b3-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="fa8b3-139">authorizationPolicies</span></span>|<span data-ttu-id="fa8b3-140">`add` Anahtar sözcüğü kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="fa8b3-141">Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="fa8b3-142">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="fa8b3-143">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="fa8b3-144">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa8b3-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa8b3-145">Parent Elements</span></span>  
  
|<span data-ttu-id="fa8b3-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa8b3-146">Element</span></span>|<span data-ttu-id="fa8b3-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa8b3-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa8b3-148">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="fa8b3-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fa8b3-149">Bir hizmetin davranışı için ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-149">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa8b3-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa8b3-150">Remarks</span></span>  
 <span data-ttu-id="fa8b3-151">Bu bölüm yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme işlemlerini etkileyen öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="fa8b3-152">Özniteliği `principalPermissionMode` , korumalı bir yöntemin kullanımını yetkilendirirken kullanılacak kullanıcı gruplarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="fa8b3-153">Varsayılan değer ' dir `UseWindowsGroups` ve bir kaynağa erişmeye çalışan bir kimlik için "Yöneticiler" veya "kullanıcılar" gibi Windows gruplarının arandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="fa8b3-154">Ayrıca, aşağıdaki kodda `UseAspNetRoles` gösterildiği gibi, \<System. Web > öğesi altında yapılandırılmış özel bir rol sağlayıcısı kullanmayı da belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="fa8b3-155">Aşağıdaki kod, `principalPermissionMode` özniteliğiyle birlikte `roleProviderName` kullanılan öğesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="fa8b3-156">Bu yapılandırma öğesinin kullanımına ilişkin ayrıntılı bir örnek için bkz. [hizmet işlemlerine](../../../wcf/samples/authorizing-access-to-service-operations.md) ve [Yetkilendirme ilkesine](../../../wcf/samples/authorization-policy.md)erişimi yetkilendirme.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8b3-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa8b3-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="fa8b3-158">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="fa8b3-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="fa8b3-159">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="fa8b3-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="fa8b3-160">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa8b3-160">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="fa8b3-161">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="fa8b3-161">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="fa8b3-162">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="fa8b3-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
