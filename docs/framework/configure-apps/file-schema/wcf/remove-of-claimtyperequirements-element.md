---
title: <remove><claimTypeRequirements> öğesinin
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7238c253bfbc3224c8bbd31265e197dd35e56514
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934231"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="7a66e-102">\<\<ClaimTypeRequirements > öğesinin > Kaldır</span><span class="sxs-lookup"><span data-stu-id="7a66e-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="7a66e-103">Federal kimlik bilgilerinde kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a66e-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="7a66e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7a66e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7a66e-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7a66e-105">\<bindings></span></span>  
<span data-ttu-id="7a66e-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="7a66e-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="7a66e-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="7a66e-107">\<binding></span></span>  
<span data-ttu-id="7a66e-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="7a66e-108">\<security></span></span>  
<span data-ttu-id="7a66e-109">\<ileti ></span><span class="sxs-lookup"><span data-stu-id="7a66e-109">\<message></span></span>  
<span data-ttu-id="7a66e-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="7a66e-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a66e-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a66e-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a66e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a66e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7a66e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7a66e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a66e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7a66e-114">Attributes</span></span>  
  
|<span data-ttu-id="7a66e-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7a66e-115">Attribute</span></span>|<span data-ttu-id="7a66e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a66e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a66e-117">claimType</span><span class="sxs-lookup"><span data-stu-id="7a66e-117">claimType</span></span>|<span data-ttu-id="7a66e-118">Kaldırılacak talebin türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="7a66e-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a66e-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a66e-119">Child Elements</span></span>  
 <span data-ttu-id="7a66e-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="7a66e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a66e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7a66e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7a66e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="7a66e-122">Element</span></span>|<span data-ttu-id="7a66e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a66e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a66e-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="7a66e-124">\<claimTypeRequirements></span></span>](claimtyperequirements-for-message.md)|<span data-ttu-id="7a66e-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a66e-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="7a66e-126">Her öğe türündedir <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="7a66e-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="7a66e-127">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="7a66e-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7a66e-128">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a66e-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7a66e-129">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7a66e-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a66e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a66e-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
