---
description: 'Daha fazla bilgi edinin: <serviceAuthorization> öğesi'
title: <serviceAuthorization> öğesi
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: ee447f487027ed12f829dd0fd364556ce095d7d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682936"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="e0380-103">\<serviceAuthorization> öğesi</span><span class="sxs-lookup"><span data-stu-id="e0380-103">\<serviceAuthorization> element</span></span>

<span data-ttu-id="e0380-104">Hizmet işlemlerine erişim yetkisi veren ayarları belirtir</span><span class="sxs-lookup"><span data-stu-id="e0380-104">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="e0380-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0380-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e0380-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="e0380-106">Attributes and elements</span></span>

<span data-ttu-id="e0380-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır:</span><span class="sxs-lookup"><span data-stu-id="e0380-107">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="e0380-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e0380-108">Attributes</span></span>

|<span data-ttu-id="e0380-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e0380-109">Attribute</span></span>|<span data-ttu-id="e0380-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0380-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0380-111">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="e0380-111">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="e0380-112">Hizmette tüm işlemlerin çağıranın kimliğine bürünmesini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e0380-112">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="e0380-113">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="e0380-113">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e0380-114">Belirli bir hizmet işlemi çağıranı taklit ettiğinde, belirtilen hizmeti yürütmeden önce iş parçacığı bağlamı arayan bağlamına geçiş yapılır.</span><span class="sxs-lookup"><span data-stu-id="e0380-114">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="e0380-115">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="e0380-115">principalPermissionMode</span></span>|<span data-ttu-id="e0380-116">Sunucuda işlemleri yürütmek için kullanılan sorumluyu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0380-116">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="e0380-117">Değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e0380-117">Values include the following:</span></span><br /><br /> <span data-ttu-id="e0380-118">-   Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="e0380-118">-   None</span></span><br /><span data-ttu-id="e0380-119">-UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="e0380-119">-   UseWindowsGroups</span></span><br /><span data-ttu-id="e0380-120">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="e0380-120">-   UseAspNetRoles</span></span><br /><span data-ttu-id="e0380-121">-Özel</span><span class="sxs-lookup"><span data-stu-id="e0380-121">-   Custom</span></span><br /><br /> <span data-ttu-id="e0380-122">Varsayılan değer UseWindowsGroups değeridir.</span><span class="sxs-lookup"><span data-stu-id="e0380-122">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="e0380-123">Değer, türündedir <xref:System.ServiceModel.Description.PrincipalPermissionMode> .</span><span class="sxs-lookup"><span data-stu-id="e0380-123">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="e0380-124">Bu özniteliği kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: erişimi, PrincipalPermissionAttribute sınıfı Ile kısıtlama](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="e0380-124">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="e0380-125">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="e0380-125">roleProviderName</span></span>|<span data-ttu-id="e0380-126">Bir Windows Communication Foundation (WCF) uygulaması için rol bilgileri sağlayan rol sağlayıcısının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e0380-126">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e0380-127">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e0380-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="e0380-128">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="e0380-128">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="e0380-129">Hizmet Yetkilendirme Yöneticisi türünü içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="e0380-129">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="e0380-130">Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="e0380-130">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="e0380-131">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="e0380-131">Child elements</span></span>

|<span data-ttu-id="e0380-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0380-132">Element</span></span>|<span data-ttu-id="e0380-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0380-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0380-134">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="e0380-134">authorizationPolicies</span></span>|<span data-ttu-id="e0380-135">Anahtar sözcüğü kullanılarak eklenebilen bir yetkilendirme ilkesi türü koleksiyonu içerir `add` .</span><span class="sxs-lookup"><span data-stu-id="e0380-135">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="e0380-136">Her yetkilendirme ilkesi `policyType` , bir dize olan tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="e0380-136">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="e0380-137">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0380-137">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e0380-138">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="e0380-138">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="e0380-139">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e0380-139">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="e0380-140">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="e0380-140">Parent elements</span></span>

|<span data-ttu-id="e0380-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="e0380-141">Element</span></span>|<span data-ttu-id="e0380-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0380-142">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e0380-143">Bir hizmetin davranışı için ayarların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e0380-143">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="e0380-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0380-144">Remarks</span></span>

<span data-ttu-id="e0380-145">Bu bölüm yetkilendirme, özel rol sağlayıcıları ve kimliğe bürünme işlemlerini etkileyen öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e0380-145">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="e0380-146">`principalPermissionMode`Özniteliği, korumalı bir yöntemin kullanımını yetkilendirirken kullanılacak kullanıcı gruplarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0380-146">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="e0380-147">Varsayılan değer ' dir `UseWindowsGroups` ve bir kaynağa erişmeye çalışan bir kimlik için "Yöneticiler" veya "kullanıcılar" gibi Windows gruplarının arandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0380-147">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="e0380-148">`UseAspNetRoles`Aşağıdaki kodda gösterildiği gibi, öğesi altında yapılandırılan özel bir rol sağlayıcısı kullanmayı da belirtebilirsiniz \<system.web> :</span><span class="sxs-lookup"><span data-stu-id="e0380-148">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="e0380-149">Aşağıdaki kod, `roleProviderName` özniteliğiyle birlikte kullanılan öğesini gösterir `principalPermissionMode` :</span><span class="sxs-lookup"><span data-stu-id="e0380-149">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="e0380-150">Bu yapılandırma öğesinin kullanımına ilişkin ayrıntılı bir örnek için bkz. [hizmet işlemlerine](../../../wcf/samples/authorizing-access-to-service-operations.md) ve [Yetkilendirme ilkesine](../../../wcf/samples/authorization-policy.md)erişimi yetkilendirme.</span><span class="sxs-lookup"><span data-stu-id="e0380-150">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e0380-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0380-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="e0380-152">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="e0380-152">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e0380-153">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="e0380-153">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="e0380-154">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0380-154">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="e0380-155">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="e0380-155">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="e0380-156">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="e0380-156">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
