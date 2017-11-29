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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99bb7c6be02bad85792dfce9de1f6ef8ba1dcd17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="668d7-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="668d7-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="668d7-103">Özel ilke onaylamalarını bağlamaları hakkında alma denetimleri bir ilke alma belirtir.</span><span class="sxs-lookup"><span data-stu-id="668d7-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="668d7-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="668d7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="668d7-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="668d7-105">\<client></span></span>  
<span data-ttu-id="668d7-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="668d7-106">\<metadata></span></span>  
<span data-ttu-id="668d7-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="668d7-107">\<policyImporters></span></span>  
<span data-ttu-id="668d7-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="668d7-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668d7-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="668d7-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="668d7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="668d7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="668d7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="668d7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="668d7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="668d7-112">Attributes</span></span>  
  
|<span data-ttu-id="668d7-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="668d7-113">Attribute</span></span>|<span data-ttu-id="668d7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="668d7-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="668d7-115">Bu öğe türü.</span><span class="sxs-lookup"><span data-stu-id="668d7-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="668d7-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="668d7-116">Child Elements</span></span>  
 <span data-ttu-id="668d7-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="668d7-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="668d7-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="668d7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="668d7-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="668d7-119">Element</span></span>|<span data-ttu-id="668d7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="668d7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="668d7-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="668d7-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="668d7-122">Özel ilke onaylamalarını bağlamaları hakkında alma Denetim İlkesi ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="668d7-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="668d7-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="668d7-123">Remarks</span></span>  
 <span data-ttu-id="668d7-124">İlke içeri Aktarıcı yanı sıra özellikleri bağlama hakkında özel ilke onaylamalarını arama onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="668d7-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668d7-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="668d7-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="668d7-126">WCF istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="668d7-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="668d7-127">İstemciler</span><span class="sxs-lookup"><span data-stu-id="668d7-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
