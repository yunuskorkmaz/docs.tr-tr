---
title: <clear><claimTypeRequirements> öğesinin
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: e7e3bebd85decbaa4d216743f9bea9e135b87995
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926130"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="a7e5c-102">\<\<ClaimTypeRequirements > öğesinin > Temizle</span><span class="sxs-lookup"><span data-stu-id="a7e5c-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="a7e5c-103">Tüm talep türlerinin federal kimlik bilgilerinde kaldırılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="a7e5c-104">Bu, koleksiyonun boş başlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="a7e5c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7e5c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7e5c-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-106">\<bindings></span></span>  
<span data-ttu-id="a7e5c-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a7e5c-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-108">\<binding></span></span>  
<span data-ttu-id="a7e5c-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-109">\<security></span></span>  
<span data-ttu-id="a7e5c-110">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-110">\<message></span></span>  
<span data-ttu-id="a7e5c-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e5c-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e5c-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7e5c-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e5c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a7e5c-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7e5c-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7e5c-115">Attributes</span></span>  
 <span data-ttu-id="a7e5c-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7e5c-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e5c-117">Child Elements</span></span>  
 <span data-ttu-id="a7e5c-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7e5c-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7e5c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a7e5c-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7e5c-120">Element</span></span>|<span data-ttu-id="a7e5c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7e5c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7e5c-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a7e5c-122">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="a7e5c-123">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a7e5c-124">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a7e5c-125">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a7e5c-126">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a7e5c-127">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7e5c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e5c-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
