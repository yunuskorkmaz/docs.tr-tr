---
title: "&lt;claimTypeRequirements&gt; öğesini &lt;kaldırma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49009cb7e988c27ccc426e29c6ac973e553a0f73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="fdd5b-102">&lt;claimTypeRequirements&gt; öğesini &lt;kaldırma&gt;</span><span class="sxs-lookup"><span data-stu-id="fdd5b-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="fdd5b-103">Federe kimlik bilgisi kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="fdd5b-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fdd5b-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-105">\<bindings></span></span>  
<span data-ttu-id="fdd5b-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="fdd5b-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-107">\<binding></span></span>  
<span data-ttu-id="fdd5b-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-108">\<security></span></span>  
<span data-ttu-id="fdd5b-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-109">\<message></span></span>  
<span data-ttu-id="fdd5b-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd5b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdd5b-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdd5b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fdd5b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fdd5b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdd5b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fdd5b-114">Attributes</span></span>  
  
|<span data-ttu-id="fdd5b-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fdd5b-115">Attribute</span></span>|<span data-ttu-id="fdd5b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdd5b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fdd5b-117">claimType</span><span class="sxs-lookup"><span data-stu-id="fdd5b-117">claimType</span></span>|<span data-ttu-id="fdd5b-118">Kaldırılacak talep türünü tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdd5b-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fdd5b-119">Child Elements</span></span>  
 <span data-ttu-id="fdd5b-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdd5b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fdd5b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fdd5b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="fdd5b-122">Element</span></span>|<span data-ttu-id="fdd5b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdd5b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdd5b-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="fdd5b-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="fdd5b-125">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="fdd5b-126">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="fdd5b-127">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="fdd5b-128">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="fdd5b-129">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdd5b-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdd5b-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
