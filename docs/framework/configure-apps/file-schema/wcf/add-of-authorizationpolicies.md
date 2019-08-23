---
title: <add> / <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920268"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="cb177-102">\<\<AuthorizationPolicies > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="cb177-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="cb177-103">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb177-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="cb177-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cb177-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cb177-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="cb177-105">\<behaviors></span></span>  
<span data-ttu-id="cb177-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="cb177-106">\<behavior></span></span>  
<span data-ttu-id="cb177-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="cb177-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="cb177-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="cb177-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="cb177-109">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="cb177-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb177-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb177-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="cb177-111">Tür</span><span class="sxs-lookup"><span data-stu-id="cb177-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb177-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb177-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cb177-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb177-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb177-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb177-114">Attributes</span></span>  
  
|<span data-ttu-id="cb177-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb177-115">Attribute</span></span>|<span data-ttu-id="cb177-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb177-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="cb177-117">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cb177-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="cb177-118">Windows Communication Foundation (WCF) erişim denetimi modeli, bir yetkilendirme ilkelerinin kümesini tür olarak sağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="cb177-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="cb177-119">Bu öznitelik, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb177-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="cb177-120">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb177-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb177-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb177-121">Child Elements</span></span>  
 <span data-ttu-id="cb177-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb177-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb177-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb177-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cb177-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb177-124">Element</span></span>|<span data-ttu-id="cb177-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb177-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb177-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="cb177-126">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="cb177-127">Yetkilendirme ilkesi türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb177-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb177-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb177-128">Remarks</span></span>  
 <span data-ttu-id="cb177-129">Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="cb177-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="cb177-130">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb177-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="cb177-131">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb177-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="cb177-132">Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="cb177-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb177-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb177-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="cb177-134">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="cb177-134">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="cb177-135">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb177-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="cb177-136">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="cb177-136">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="cb177-137">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="cb177-137">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
