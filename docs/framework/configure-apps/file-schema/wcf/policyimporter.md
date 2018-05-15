---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 7483a95accef0a4bc956d919087379363b4762ca
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="d6216-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="d6216-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="d6216-103">Özel ilke onaylamalarını bağlamaları hakkında alma denetimleri bir ilke alma belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6216-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="d6216-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6216-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6216-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="d6216-105">\<client></span></span>  
<span data-ttu-id="d6216-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="d6216-106">\<metadata></span></span>  
<span data-ttu-id="d6216-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="d6216-107">\<policyImporters></span></span>  
<span data-ttu-id="d6216-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="d6216-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6216-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6216-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6216-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6216-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d6216-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6216-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6216-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d6216-112">Attributes</span></span>  
  
|<span data-ttu-id="d6216-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d6216-113">Attribute</span></span>|<span data-ttu-id="d6216-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6216-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d6216-115">Bu öğe türü.</span><span class="sxs-lookup"><span data-stu-id="d6216-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6216-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6216-116">Child Elements</span></span>  
 <span data-ttu-id="d6216-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d6216-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6216-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d6216-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d6216-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d6216-119">Element</span></span>|<span data-ttu-id="d6216-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6216-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6216-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="d6216-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="d6216-122">Özel ilke onaylamalarını bağlamaları hakkında alma Denetim İlkesi ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6216-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6216-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6216-123">Remarks</span></span>  
 <span data-ttu-id="d6216-124">İlke içeri Aktarıcı yanı sıra özellikleri bağlama hakkında özel ilke onaylamalarını arama onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d6216-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6216-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6216-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="d6216-126">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d6216-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="d6216-127">İstemciler</span><span class="sxs-lookup"><span data-stu-id="d6216-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
