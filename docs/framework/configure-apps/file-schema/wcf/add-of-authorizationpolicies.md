---
title: <add> / <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 39cb89340907743c727a425bb2f140ac34842e3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181680"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="ce126-102">\<add> / \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="ce126-102">\<add> of \<authorizationPolicies></span></span>

<span data-ttu-id="ce126-103">Talep dönüştürme için bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce126-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ce126-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce126-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="ce126-105">Tür</span><span class="sxs-lookup"><span data-stu-id="ce126-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce126-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce126-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ce126-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce126-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce126-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce126-108">Attributes</span></span>  
  
|<span data-ttu-id="ce126-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce126-109">Attribute</span></span>|<span data-ttu-id="ce126-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce126-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="ce126-111">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ce126-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="ce126-112">Windows Communication Foundation (WCF) erişim denetimi modeli, bir yetkilendirme ilkelerinin kümesini tür olarak sağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="ce126-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="ce126-113">Bu öznitelik, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce126-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="ce126-114">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce126-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce126-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce126-115">Child Elements</span></span>  

 <span data-ttu-id="ce126-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="ce126-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce126-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce126-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ce126-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce126-118">Element</span></span>|<span data-ttu-id="ce126-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce126-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="ce126-120">Yetkilendirme ilkesi türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce126-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce126-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce126-121">Remarks</span></span>  

 <span data-ttu-id="ce126-122">Her yetkilendirme ilkesi `policyType` , bir dize olan tek bir gerekli özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="ce126-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="ce126-123">Özniteliği, bir giriş talepleri kümesinin başka bir talepler kümesine dönüştürülmesini sağlayan bir yetkilendirme ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce126-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="ce126-124">Erişim denetimi, bu temel alınarak verilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="ce126-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="ce126-125">Yetkilendirme ilkesinin nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Policy.IAuthorizationPolicy> . ve [Yetkilendirme İlkesi](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="ce126-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce126-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce126-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="ce126-127">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="ce126-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="ce126-128">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce126-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="ce126-129">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="ce126-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
