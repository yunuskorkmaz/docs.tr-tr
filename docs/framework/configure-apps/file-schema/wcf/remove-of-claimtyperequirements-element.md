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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 96155ed805d99a3678c5d20d83a490efb9811815
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-of-ltclaimtyperequirementsgt-element"></a><span data-ttu-id="e7593-102">&lt;claimTypeRequirements&gt; öğesini &lt;kaldırma&gt;</span><span class="sxs-lookup"><span data-stu-id="e7593-102">&lt;remove&gt; of &lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="e7593-103">Federe kimlik bilgisi kaldırılacak talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7593-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
 <span data-ttu-id="e7593-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e7593-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7593-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="e7593-105">\<bindings></span></span>  
<span data-ttu-id="e7593-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="e7593-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="e7593-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e7593-107">\<binding></span></span>  
<span data-ttu-id="e7593-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="e7593-108">\<security></span></span>  
<span data-ttu-id="e7593-109">\<İleti ></span><span class="sxs-lookup"><span data-stu-id="e7593-109">\<message></span></span>  
<span data-ttu-id="e7593-110">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="e7593-110">\<claimTypeRequirements></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7593-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7593-111">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>  
      <remove claimType="URI" />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7593-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7593-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e7593-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7593-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7593-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7593-114">Attributes</span></span>  
  
|<span data-ttu-id="e7593-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7593-115">Attribute</span></span>|<span data-ttu-id="e7593-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7593-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7593-117">claimType</span><span class="sxs-lookup"><span data-stu-id="e7593-117">claimType</span></span>|<span data-ttu-id="e7593-118">Kaldırılacak talep türünü tanımlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="e7593-118">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7593-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7593-119">Child Elements</span></span>  
 <span data-ttu-id="e7593-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7593-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7593-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7593-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e7593-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7593-122">Element</span></span>|<span data-ttu-id="e7593-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7593-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7593-124">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="e7593-124">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|<span data-ttu-id="e7593-125">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7593-125">Specifies a collection of required claim types.</span></span> <span data-ttu-id="e7593-126">Her öğe türünde <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e7593-126">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="e7593-127">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="e7593-127">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e7593-128">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7593-128">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e7593-129">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7593-129">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7593-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7593-130">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
