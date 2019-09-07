---
title: <add> / <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400693"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="aeaed-102">\<\<AuthorizationPolicies > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="aeaed-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="aeaed-103">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-103">Specifies an authorization policy for claim transformation.</span></span>  
  
<span data-ttu-id="aeaed-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aeaed-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aeaed-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="aeaed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="aeaed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="aeaed-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceAuthorization >** ](serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)</span></span>\
<span data-ttu-id="aeaed-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authorizationPolicies >** ](authorizationpolicies.md)</span><span class="sxs-lookup"><span data-stu-id="aeaed-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)</span></span>\
<span data-ttu-id="aeaed-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="aeaed-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeaed-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aeaed-112">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="aeaed-113">Tür</span><span class="sxs-lookup"><span data-stu-id="aeaed-113">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeaed-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aeaed-114">Attributes and Elements</span></span>  
 <span data-ttu-id="aeaed-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeaed-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeaed-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aeaed-116">Attributes</span></span>  
  
|<span data-ttu-id="aeaed-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aeaed-117">Attribute</span></span>|<span data-ttu-id="aeaed-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeaed-118">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="aeaed-119">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="aeaed-119">A required String attribute.</span></span><br /><br /> <span data-ttu-id="aeaed-120">Windows Communication Foundation (WCF) erişim denetimi modeli, bir yetkilendirme ilkelerinin kümesini tür olarak sağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="aeaed-120">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="aeaed-121">Bu öznitelik, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-121">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="aeaed-122">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-122">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aeaed-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aeaed-123">Child Elements</span></span>  
 <span data-ttu-id="aeaed-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="aeaed-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aeaed-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aeaed-125">Parent Elements</span></span>  
  
|<span data-ttu-id="aeaed-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="aeaed-126">Element</span></span>|<span data-ttu-id="aeaed-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeaed-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aeaed-128">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="aeaed-128">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="aeaed-129">Yetkilendirme ilkesi türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-129">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeaed-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aeaed-130">Remarks</span></span>  
 <span data-ttu-id="aeaed-131">Her yetkilendirme ilkesi, bir dize olan `policyType` tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-131">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="aeaed-132">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-132">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="aeaed-133">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="aeaed-133">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="aeaed-134">Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="aeaed-134">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeaed-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeaed-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="aeaed-136">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="aeaed-136">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="aeaed-137">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="aeaed-137">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="aeaed-138">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="aeaed-138">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="aeaed-139">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="aeaed-139">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
