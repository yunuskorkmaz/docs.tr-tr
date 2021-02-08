---
description: 'Hakkında daha fazla bilgi <add> edinin: <authorizationPolicies>'
title: <add> / <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 616f09abfad51f41348b0ffa8557a4fd54492437
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804107"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="c943c-103">\<add> / \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="c943c-103">\<add> of \<authorizationPolicies></span></span>

<span data-ttu-id="c943c-104">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c943c-104">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c943c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c943c-105">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="c943c-106">Tür</span><span class="sxs-lookup"><span data-stu-id="c943c-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c943c-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c943c-107">Attributes and Elements</span></span>  

 <span data-ttu-id="c943c-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c943c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c943c-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c943c-109">Attributes</span></span>  
  
|<span data-ttu-id="c943c-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c943c-110">Attribute</span></span>|<span data-ttu-id="c943c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c943c-111">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="c943c-112">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c943c-112">A required String attribute.</span></span><br /><br /> <span data-ttu-id="c943c-113">Windows Communication Foundation (WCF) erişim denetimi modeli, bir yetkilendirme ilkelerinin kümesini tür olarak sağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="c943c-113">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="c943c-114">Bu öznitelik, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c943c-114">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="c943c-115">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="c943c-115">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c943c-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c943c-116">Child Elements</span></span>  

 <span data-ttu-id="c943c-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="c943c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c943c-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c943c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c943c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c943c-119">Element</span></span>|<span data-ttu-id="c943c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c943c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="c943c-121">Yetkilendirme ilkesi türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c943c-121">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c943c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c943c-122">Remarks</span></span>  

 <span data-ttu-id="c943c-123">Her yetkilendirme ilkesi `policyType` , bir dize olan tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c943c-123">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="c943c-124">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c943c-124">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="c943c-125">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="c943c-125">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="c943c-126">Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="c943c-126">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c943c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c943c-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="c943c-128">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c943c-128">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="c943c-129">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c943c-129">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="c943c-130">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="c943c-130">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
