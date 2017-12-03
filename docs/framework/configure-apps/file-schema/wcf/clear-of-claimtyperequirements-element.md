---
title: "&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a5c3b101c51bcba1c1a579dcf99001c4b8dbab2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="0375e-102">&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;</span><span class="sxs-lookup"><span data-stu-id="0375e-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="0375e-103">Tüm talep federe kimlik bilgisi kaldırılacak türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0375e-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="0375e-104">Bu koleksiyon boş başlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0375e-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="0375e-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0375e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0375e-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0375e-106">\<bindings></span></span>  
<span data-ttu-id="0375e-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="0375e-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="0375e-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0375e-108">\<binding></span></span>  
<span data-ttu-id="0375e-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="0375e-109">\<security></span></span>  
<span data-ttu-id="0375e-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="0375e-110">\<message></span></span>  
<span data-ttu-id="0375e-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="0375e-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0375e-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0375e-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0375e-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0375e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0375e-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0375e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0375e-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0375e-115">Attributes</span></span>  
 <span data-ttu-id="0375e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="0375e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0375e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0375e-117">Child Elements</span></span>  
 <span data-ttu-id="0375e-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="0375e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0375e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0375e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0375e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="0375e-120">Element</span></span>|<span data-ttu-id="0375e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0375e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0375e-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="0375e-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="0375e-123">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0375e-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="0375e-124">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="0375e-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="0375e-125">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="0375e-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="0375e-126">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0375e-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="0375e-127">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0375e-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0375e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0375e-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
