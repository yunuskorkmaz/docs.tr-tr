---
title: <remove><claimTypeRequirements> öğesinin
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399993"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="76f22-102">\<\<ClaimTypeRequirements > öğesinin > Kaldır</span><span class="sxs-lookup"><span data-stu-id="76f22-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="76f22-103">Federal kimlik bilgilerinde kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="76f22-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
<span data-ttu-id="76f22-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76f22-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="76f22-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="76f22-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="76f22-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="76f22-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="76f22-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="76f22-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ileti >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="76f22-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="76f22-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="76f22-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Kaldır**</span><span class="sxs-lookup"><span data-stu-id="76f22-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f22-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76f22-113">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76f22-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="76f22-114">Attributes and Elements</span></span>  
 <span data-ttu-id="76f22-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76f22-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76f22-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76f22-116">Attributes</span></span>  
  
|<span data-ttu-id="76f22-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="76f22-117">Attribute</span></span>|<span data-ttu-id="76f22-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76f22-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76f22-119">claimType</span><span class="sxs-lookup"><span data-stu-id="76f22-119">claimType</span></span>|<span data-ttu-id="76f22-120">Kaldırılacak talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="76f22-120">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76f22-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="76f22-121">Child Elements</span></span>  
 <span data-ttu-id="76f22-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="76f22-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76f22-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="76f22-123">Parent Elements</span></span>  
  
|<span data-ttu-id="76f22-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="76f22-124">Element</span></span>|<span data-ttu-id="76f22-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76f22-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76f22-126">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="76f22-126">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="76f22-127">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="76f22-127">Specifies a collection of required claim types.</span></span> <span data-ttu-id="76f22-128">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="76f22-128">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="76f22-129">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="76f22-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="76f22-130">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76f22-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="76f22-131">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="76f22-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76f22-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76f22-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
