---
title: '&lt;claimTypeRequirements&gt; öğesini &lt;kaldırma&gt;'
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 7610a8e95996f15133ae58ec33c4afd9e2309cac
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146218"
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="9e1da-102">&lt;claimTypeRequirements&gt; öğesini &lt;kaldırma&gt;</span><span class="sxs-lookup"><span data-stu-id="9e1da-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="9e1da-103">Birleştirilmiş kimlik bilgisindeki kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e1da-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="9e1da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9e1da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9e1da-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9e1da-105">\<bindings></span></span>  
<span data-ttu-id="9e1da-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="9e1da-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="9e1da-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9e1da-107">\<binding></span></span>  
<span data-ttu-id="9e1da-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9e1da-108">\<security></span></span>  
<span data-ttu-id="9e1da-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="9e1da-109">\<message></span></span>  
<span data-ttu-id="9e1da-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="9e1da-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e1da-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e1da-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e1da-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e1da-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9e1da-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e1da-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e1da-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9e1da-114">Attributes</span></span>  
  
|<span data-ttu-id="9e1da-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9e1da-115">Attribute</span></span>|<span data-ttu-id="9e1da-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e1da-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e1da-117">ClaimType</span><span class="sxs-lookup"><span data-stu-id="9e1da-117">claimType</span></span>|<span data-ttu-id="9e1da-118">Kaldırılacak talep türünü tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="9e1da-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e1da-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e1da-119">Child Elements</span></span>  
 <span data-ttu-id="9e1da-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="9e1da-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e1da-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9e1da-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9e1da-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="9e1da-122">Element</span></span>|<span data-ttu-id="9e1da-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e1da-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e1da-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="9e1da-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="9e1da-125">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e1da-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="9e1da-126">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="9e1da-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="9e1da-127">Federe bir senaryoda, hizmetleri gereksinimlerine gelen kimlik bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="9e1da-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9e1da-128">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e1da-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9e1da-129">Bu koleksiyondaki her öğe bir birleştirilmiş kimlik bilgisinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e1da-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e1da-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e1da-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
