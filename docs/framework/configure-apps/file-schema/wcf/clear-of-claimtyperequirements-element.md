---
title: <clear> ' ın <claimTypeRequirements> öğesi
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 35d0391951204bd352918d3004f0cc4f9480b0e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704277"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="3f3d2-102">\<Temizle >, \<claimTypeRequirements > öğesi</span><span class="sxs-lookup"><span data-stu-id="3f3d2-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="3f3d2-103">Birleştirilmiş kimlik bilgisindeki kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="3f3d2-104">Bu koleksiyon boş başlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="3f3d2-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f3d2-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f3d2-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-106">\<bindings></span></span>  
<span data-ttu-id="3f3d2-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="3f3d2-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-108">\<binding></span></span>  
<span data-ttu-id="3f3d2-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-109">\<security></span></span>  
<span data-ttu-id="3f3d2-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-110">\<message></span></span>  
<span data-ttu-id="3f3d2-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3d2-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f3d2-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f3d2-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f3d2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3f3d2-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f3d2-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f3d2-115">Attributes</span></span>  
 <span data-ttu-id="3f3d2-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f3d2-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f3d2-117">Child Elements</span></span>  
 <span data-ttu-id="3f3d2-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f3d2-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f3d2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3f3d2-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f3d2-120">Element</span></span>|<span data-ttu-id="3f3d2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f3d2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f3d2-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3f3d2-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="3f3d2-123">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="3f3d2-124">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="3f3d2-125">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="3f3d2-126">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="3f3d2-127">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f3d2-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f3d2-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
