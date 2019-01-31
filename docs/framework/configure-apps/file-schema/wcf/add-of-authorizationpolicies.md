---
title: <add> , <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 6a1a7d6b1ef9732e015536d8a78c058fe348113f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255503"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="7e59f-102">\<Ekle >, \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="7e59f-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="7e59f-103">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e59f-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="7e59f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7e59f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e59f-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="7e59f-105">\<behaviors></span></span>  
<span data-ttu-id="7e59f-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="7e59f-106">\<behavior></span></span>  
<span data-ttu-id="7e59f-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="7e59f-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="7e59f-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="7e59f-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="7e59f-109">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="7e59f-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e59f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e59f-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="7e59f-111">Tür</span><span class="sxs-lookup"><span data-stu-id="7e59f-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e59f-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e59f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7e59f-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e59f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e59f-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7e59f-114">Attributes</span></span>  
  
|<span data-ttu-id="7e59f-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7e59f-115">Attribute</span></span>|<span data-ttu-id="7e59f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e59f-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="7e59f-117">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e59f-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="7e59f-118">Windows Communication Foundation (WCF) erişim denetimi modeli, sağlama türü olarak yetkilendirme ilkeleri kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="7e59f-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="7e59f-119">Bu öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e59f-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="7e59f-120">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="7e59f-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e59f-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e59f-121">Child Elements</span></span>  
 <span data-ttu-id="7e59f-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="7e59f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e59f-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7e59f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7e59f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="7e59f-124">Element</span></span>|<span data-ttu-id="7e59f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e59f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e59f-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="7e59f-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="7e59f-127">Yetkilendirme İlkesi türü koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e59f-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e59f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e59f-128">Remarks</span></span>  
 <span data-ttu-id="7e59f-129">Gereken tek bir her yetkilendirme ilkesi içeren `policyType` dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="7e59f-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="7e59f-130">Öznitelik, bir giriş talep kümesini talep başka bir dizi dönüşümünü sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e59f-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="7e59f-131">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="7e59f-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="7e59f-132">Bir yetkilendirme ilkesi birlikte nasıl çalıştığı hakkında daha fazla bilgi için bkz. <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="7e59f-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e59f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e59f-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="7e59f-134">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="7e59f-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="7e59f-135">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e59f-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="7e59f-136">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="7e59f-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="7e59f-137">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="7e59f-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
