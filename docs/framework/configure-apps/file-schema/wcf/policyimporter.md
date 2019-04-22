---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 81f38d2a163163ca7255ca546bbddbbb58fa3a1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094183"
---
# <a name="policyimporter"></a><span data-ttu-id="b501e-101">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="b501e-101">\<policyImporter></span></span>
<span data-ttu-id="b501e-102">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen bir ilke içeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b501e-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="b501e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b501e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b501e-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="b501e-104">\<client></span></span>  
<span data-ttu-id="b501e-105">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="b501e-105">\<metadata></span></span>  
<span data-ttu-id="b501e-106">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="b501e-106">\<policyImporters></span></span>  
<span data-ttu-id="b501e-107">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="b501e-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b501e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b501e-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b501e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b501e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b501e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b501e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b501e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b501e-111">Attributes</span></span>  
  
|<span data-ttu-id="b501e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b501e-112">Attribute</span></span>|<span data-ttu-id="b501e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b501e-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b501e-114">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="b501e-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b501e-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b501e-115">Child Elements</span></span>  
 <span data-ttu-id="b501e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="b501e-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b501e-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b501e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b501e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b501e-118">Element</span></span>|<span data-ttu-id="b501e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b501e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b501e-120">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="b501e-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="b501e-121">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="b501e-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b501e-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b501e-122">Remarks</span></span>  
 <span data-ttu-id="b501e-123">İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b501e-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b501e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b501e-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="b501e-125">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="b501e-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b501e-126">İstemciler</span><span class="sxs-lookup"><span data-stu-id="b501e-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
