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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 69752480a7f399a202d497e12a783ffa091dd4b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="a2993-102">&lt;claimTypeRequirements&gt; öğesi &lt;temizleme&gt;</span><span class="sxs-lookup"><span data-stu-id="a2993-102">&lt;clear&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="a2993-103">Tüm talep federe kimlik bilgisi kaldırılacak türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2993-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="a2993-104">Bu koleksiyon boş başlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2993-104">This ensures that the collection starts empty.</span></span>  
  
 <span data-ttu-id="a2993-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a2993-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a2993-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a2993-106">\<bindings></span></span>  
<span data-ttu-id="a2993-107">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a2993-107">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a2993-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a2993-108">\<binding></span></span>  
<span data-ttu-id="a2993-109">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a2993-109">\<security></span></span>  
<span data-ttu-id="a2993-110">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="a2993-110">\<message></span></span>  
<span data-ttu-id="a2993-111">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a2993-111">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2993-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2993-112">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2993-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2993-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a2993-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2993-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2993-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a2993-115">Attributes</span></span>  
 <span data-ttu-id="a2993-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2993-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2993-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2993-117">Child Elements</span></span>  
 <span data-ttu-id="a2993-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="a2993-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2993-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2993-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a2993-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="a2993-120">Element</span></span>|<span data-ttu-id="a2993-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2993-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2993-122">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a2993-122">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="a2993-123">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2993-123">Specifies a collection of required claim types.</span></span> <span data-ttu-id="a2993-124">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a2993-124">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="a2993-125">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a2993-125">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a2993-126">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2993-126">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a2993-127">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2993-127">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2993-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2993-128">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
