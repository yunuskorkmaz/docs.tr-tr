---
title: '&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 1e77e3c978c1e385aec983d5e2d4bea64697c43e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145295"
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="bd653-102">&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;</span><span class="sxs-lookup"><span data-stu-id="bd653-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="bd653-103">Birleştirilmiş kimlik bilgisindeki kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd653-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="bd653-104">Bu koleksiyon boş başlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd653-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="bd653-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd653-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd653-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bd653-106">\<bindings></span></span>  
<span data-ttu-id="bd653-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="bd653-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="bd653-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bd653-108">\<binding></span></span>  
<span data-ttu-id="bd653-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bd653-109">\<security></span></span>  
<span data-ttu-id="bd653-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="bd653-110">\<message></span></span>  
<span data-ttu-id="bd653-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="bd653-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd653-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd653-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd653-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd653-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bd653-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd653-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd653-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd653-115">Attributes</span></span>  
 <span data-ttu-id="bd653-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd653-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd653-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd653-117">Child Elements</span></span>  
 <span data-ttu-id="bd653-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd653-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd653-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd653-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bd653-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd653-120">Element</span></span>|<span data-ttu-id="bd653-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd653-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd653-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="bd653-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="bd653-123">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd653-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="bd653-124">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="bd653-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="bd653-125">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="bd653-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="bd653-126">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd653-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="bd653-127">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd653-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd653-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd653-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
