---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2226b4f55025c9dec3fdeb4f9b4f51016ffd3e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="ba11e-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="ba11e-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="ba11e-103">Özel ilke onaylamalarını bağlamaları hakkında alma denetimleri bir ilke alma belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba11e-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="ba11e-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ba11e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba11e-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="ba11e-105">\<client></span></span>  
<span data-ttu-id="ba11e-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="ba11e-106">\<metadata></span></span>  
<span data-ttu-id="ba11e-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="ba11e-107">\<policyImporters></span></span>  
<span data-ttu-id="ba11e-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="ba11e-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba11e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba11e-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba11e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba11e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ba11e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba11e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba11e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ba11e-112">Attributes</span></span>  
  
|<span data-ttu-id="ba11e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ba11e-113">Attribute</span></span>|<span data-ttu-id="ba11e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba11e-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ba11e-115">Bu öğe türü.</span><span class="sxs-lookup"><span data-stu-id="ba11e-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba11e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba11e-116">Child Elements</span></span>  
 <span data-ttu-id="ba11e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="ba11e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba11e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba11e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ba11e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba11e-119">Element</span></span>|<span data-ttu-id="ba11e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba11e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba11e-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="ba11e-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="ba11e-122">Özel ilke onaylamalarını bağlamaları hakkında alma Denetim İlkesi ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba11e-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba11e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba11e-123">Remarks</span></span>  
 <span data-ttu-id="ba11e-124">İlke içeri Aktarıcı yanı sıra özellikleri bağlama hakkında özel ilke onaylamalarını arama onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba11e-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba11e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba11e-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="ba11e-126">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ba11e-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="ba11e-127">İstemciler</span><span class="sxs-lookup"><span data-stu-id="ba11e-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
