---
title: <remove> ' ın <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 9ab1162ff5d86b8a9d43dae79ebf9c9321119206
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119710"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="dac95-102">\<kaldırma >, \<claimTypeRequirements > öğesi</span><span class="sxs-lookup"><span data-stu-id="dac95-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="dac95-103">Birleştirilmiş kimlik bilgisindeki kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dac95-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="dac95-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dac95-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dac95-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="dac95-105">\<bindings></span></span>  
<span data-ttu-id="dac95-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="dac95-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="dac95-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="dac95-107">\<binding></span></span>  
<span data-ttu-id="dac95-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="dac95-108">\<security></span></span>  
<span data-ttu-id="dac95-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="dac95-109">\<message></span></span>  
<span data-ttu-id="dac95-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="dac95-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac95-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dac95-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dac95-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dac95-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dac95-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dac95-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dac95-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dac95-114">Attributes</span></span>  
  
|<span data-ttu-id="dac95-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dac95-115">Attribute</span></span>|<span data-ttu-id="dac95-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dac95-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dac95-117">ClaimType</span><span class="sxs-lookup"><span data-stu-id="dac95-117">claimType</span></span>|<span data-ttu-id="dac95-118">Kaldırılacak talep türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="dac95-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dac95-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dac95-119">Child Elements</span></span>  
 <span data-ttu-id="dac95-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="dac95-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dac95-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dac95-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dac95-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="dac95-122">Element</span></span>|<span data-ttu-id="dac95-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dac95-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dac95-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="dac95-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="dac95-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dac95-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="dac95-126">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="dac95-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="dac95-127">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="dac95-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="dac95-128">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dac95-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="dac95-129">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dac95-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dac95-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dac95-130">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
