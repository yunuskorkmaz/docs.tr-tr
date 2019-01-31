---
title: <remove> ' ın <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 8058a90d61d8f94944d98a26c59bfbe225f611d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259514"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="dd819-102">\<kaldırma >, \<claimTypeRequirements > öğesi</span><span class="sxs-lookup"><span data-stu-id="dd819-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="dd819-103">Birleştirilmiş kimlik bilgisindeki kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd819-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="dd819-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd819-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd819-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="dd819-105">\<bindings></span></span>  
<span data-ttu-id="dd819-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="dd819-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="dd819-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="dd819-107">\<binding></span></span>  
<span data-ttu-id="dd819-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="dd819-108">\<security></span></span>  
<span data-ttu-id="dd819-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="dd819-109">\<message></span></span>  
<span data-ttu-id="dd819-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="dd819-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd819-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd819-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd819-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd819-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dd819-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd819-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd819-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dd819-114">Attributes</span></span>  
  
|<span data-ttu-id="dd819-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd819-115">Attribute</span></span>|<span data-ttu-id="dd819-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd819-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd819-117">ClaimType</span><span class="sxs-lookup"><span data-stu-id="dd819-117">claimType</span></span>|<span data-ttu-id="dd819-118">Kaldırılacak talep türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="dd819-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd819-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd819-119">Child Elements</span></span>  
 <span data-ttu-id="dd819-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="dd819-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd819-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd819-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dd819-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd819-122">Element</span></span>|<span data-ttu-id="dd819-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd819-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd819-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="dd819-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="dd819-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd819-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="dd819-126">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="dd819-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="dd819-127">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="dd819-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="dd819-128">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd819-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="dd819-129">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd819-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd819-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd819-130">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
