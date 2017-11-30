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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d835d96c89e8b292fc2c038794aa4056fda3a095
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="e3edf-102">&lt;authorizationPolicies&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="e3edf-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="e3edf-103">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edf-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="e3edf-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e3edf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3edf-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="e3edf-105">\<behaviors></span></span>  
<span data-ttu-id="e3edf-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e3edf-106">\<behavior></span></span>  
<span data-ttu-id="e3edf-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="e3edf-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="e3edf-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="e3edf-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="e3edf-109">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="e3edf-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3edf-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3edf-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="e3edf-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e3edf-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3edf-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3edf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e3edf-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e3edf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3edf-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e3edf-114">Attributes</span></span>  
  
|<span data-ttu-id="e3edf-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e3edf-115">Attribute</span></span>|<span data-ttu-id="e3edf-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3edf-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="e3edf-117">Gerekli bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e3edf-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="e3edf-118">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Erişim denetimi modelini destekleyen türler olarak yetkilendirme ilkeleri kümesini sağlama.</span><span class="sxs-lookup"><span data-stu-id="e3edf-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="e3edf-119">Bu öznitelik, bir giriş talep kümesini bir dönüştürme talep başka bir dizi içine sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edf-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e3edf-120">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="e3edf-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3edf-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3edf-121">Child Elements</span></span>  
 <span data-ttu-id="e3edf-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e3edf-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3edf-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e3edf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e3edf-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e3edf-124">Element</span></span>|<span data-ttu-id="e3edf-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3edf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3edf-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="e3edf-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="e3edf-127">Yetkilendirme İlkesi türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edf-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3edf-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3edf-128">Remarks</span></span>  
 <span data-ttu-id="e3edf-129">Her bir yetkilendirme ilkesi gereken tek bir içeren `policyType` bir dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e3edf-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="e3edf-130">Öznitelik, bir giriş talep kümesini bir dönüştürme talep başka bir dizi içine sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3edf-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="e3edf-131">Erişim denetimi verilen veya reddedilen oturum tabanlı.</span><span class="sxs-lookup"><span data-stu-id="e3edf-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="e3edf-132">Bir yetkilendirme ilkesi nasıl çalıştığı hakkında daha fazla bilgi için bkz: <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve [yetkilendirme ilkesi](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="e3edf-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3edf-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3edf-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="e3edf-134">Hizmet işlemlerine erişimi yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="e3edf-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="e3edf-135">Nasıl yapılır: bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3edf-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="e3edf-136">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="e3edf-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="e3edf-137">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="e3edf-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
