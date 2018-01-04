---
title: '&lt;authorizationPolicies&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72af0529cea2e6810bdb7a518874a313e3ceab40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="4cd3b-102">&lt;authorizationPolicies&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="4cd3b-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="4cd3b-103">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="4cd3b-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4cd3b-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-105">\<behaviors></span></span>  
<span data-ttu-id="4cd3b-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-106">\<behavior></span></span>  
<span data-ttu-id="4cd3b-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="4cd3b-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="4cd3b-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd3b-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cd3b-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="4cd3b-111">Tür</span><span class="sxs-lookup"><span data-stu-id="4cd3b-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cd3b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cd3b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4cd3b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cd3b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4cd3b-114">Attributes</span></span>  
  
|<span data-ttu-id="4cd3b-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4cd3b-115">Attribute</span></span>|<span data-ttu-id="4cd3b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cd3b-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="4cd3b-117">Gerekli bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="4cd3b-118">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Erişim denetimi modelini destekleyen türler olarak yetkilendirme ilkeleri kümesini sağlama.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="4cd3b-119">Bu öznitelik, bir giriş talep kümesini bir dönüştürme talep başka bir dizi içine sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4cd3b-120">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cd3b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cd3b-121">Child Elements</span></span>  
 <span data-ttu-id="4cd3b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cd3b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4cd3b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4cd3b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4cd3b-124">Element</span></span>|<span data-ttu-id="4cd3b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cd3b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4cd3b-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="4cd3b-127">Yetkilendirme İlkesi türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cd3b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cd3b-128">Remarks</span></span>  
 <span data-ttu-id="4cd3b-129">Her bir yetkilendirme ilkesi gereken tek bir içeren `policyType` bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="4cd3b-130">Öznitelik, bir giriş talep kümesini bir dönüştürme talep başka bir dizi içine sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4cd3b-131">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="4cd3b-132">Bir yetkilendirme ilkesi nasıl çalıştığı hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="4cd3b-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd3b-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4cd3b-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="4cd3b-134">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="4cd3b-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="4cd3b-135">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4cd3b-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="4cd3b-136">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="4cd3b-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="4cd3b-137">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="4cd3b-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
