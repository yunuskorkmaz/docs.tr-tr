---
title: <clear><claimTypeRequirements> öğesinin
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400523"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="176fd-102">\<\<ClaimTypeRequirements > öğesinin > Temizle</span><span class="sxs-lookup"><span data-stu-id="176fd-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="176fd-103">Tüm talep türlerinin federal kimlik bilgilerinde kaldırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="176fd-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="176fd-104">Bu, koleksiyonun boş başlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="176fd-104">This ensures that the collection starts empty.</span></span>  
  
<span data-ttu-id="176fd-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="176fd-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="176fd-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="176fd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="176fd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="176fd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="176fd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="176fd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ileti >** ](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="176fd-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequirements >** ](claimtyperequirements-for-message.md)</span><span class="sxs-lookup"><span data-stu-id="176fd-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)</span></span>\
<span data-ttu-id="176fd-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Temizle**</span><span class="sxs-lookup"><span data-stu-id="176fd-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176fd-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="176fd-114">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="176fd-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="176fd-115">Attributes and Elements</span></span>  
 <span data-ttu-id="176fd-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="176fd-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="176fd-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="176fd-117">Attributes</span></span>  
 <span data-ttu-id="176fd-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="176fd-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="176fd-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="176fd-119">Child Elements</span></span>  
 <span data-ttu-id="176fd-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="176fd-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="176fd-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="176fd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="176fd-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="176fd-122">Element</span></span>|<span data-ttu-id="176fd-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="176fd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="176fd-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="176fd-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="176fd-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="176fd-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="176fd-126">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="176fd-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="176fd-127">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="176fd-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="176fd-128">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="176fd-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="176fd-129">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="176fd-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="176fd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="176fd-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
