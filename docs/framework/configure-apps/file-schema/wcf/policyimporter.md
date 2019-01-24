---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4075f7fcb1c65da3d9e2e5e5dab52452ca2c9b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632172"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="e4870-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="e4870-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="e4870-103">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen bir ilke içeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4870-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="e4870-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4870-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4870-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e4870-105">\<client></span></span>  
<span data-ttu-id="e4870-106">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="e4870-106">\<metadata></span></span>  
<span data-ttu-id="e4870-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="e4870-107">\<policyImporters></span></span>  
<span data-ttu-id="e4870-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="e4870-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4870-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4870-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4870-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4870-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e4870-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4870-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4870-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4870-112">Attributes</span></span>  
  
|<span data-ttu-id="e4870-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e4870-113">Attribute</span></span>|<span data-ttu-id="e4870-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4870-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e4870-115">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="e4870-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4870-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4870-116">Child Elements</span></span>  
 <span data-ttu-id="e4870-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="e4870-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4870-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4870-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e4870-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4870-119">Element</span></span>|<span data-ttu-id="e4870-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4870-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4870-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="e4870-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="e4870-122">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4870-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4870-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4870-123">Remarks</span></span>  
 <span data-ttu-id="e4870-124">İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4870-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4870-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4870-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="e4870-126">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e4870-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e4870-127">İstemciler</span><span class="sxs-lookup"><span data-stu-id="e4870-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
