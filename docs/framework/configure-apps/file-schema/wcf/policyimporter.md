---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: ab9193d5974ccffcbfa3e741ac4d32ff357ed372
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269243"
---
# <a name="policyimporter"></a><span data-ttu-id="0ccb1-101">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="0ccb1-101">\<policyImporter></span></span>
<span data-ttu-id="0ccb1-102">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen bir ilke içeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ccb1-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="0ccb1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0ccb1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0ccb1-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="0ccb1-104">\<client></span></span>  
<span data-ttu-id="0ccb1-105">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="0ccb1-105">\<metadata></span></span>  
<span data-ttu-id="0ccb1-106">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="0ccb1-106">\<policyImporters></span></span>  
<span data-ttu-id="0ccb1-107">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="0ccb1-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ccb1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ccb1-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ccb1-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ccb1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0ccb1-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ccb1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ccb1-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ccb1-111">Attributes</span></span>  
  
|<span data-ttu-id="0ccb1-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0ccb1-112">Attribute</span></span>|<span data-ttu-id="0ccb1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ccb1-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="0ccb1-114">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="0ccb1-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ccb1-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ccb1-115">Child Elements</span></span>  
 <span data-ttu-id="0ccb1-116">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="0ccb1-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ccb1-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ccb1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0ccb1-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ccb1-118">Element</span></span>|<span data-ttu-id="0ccb1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ccb1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ccb1-120">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="0ccb1-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="0ccb1-121">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ccb1-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ccb1-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ccb1-122">Remarks</span></span>  
 <span data-ttu-id="0ccb1-123">İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ccb1-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccb1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ccb1-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="0ccb1-125">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="0ccb1-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="0ccb1-126">İstemciler</span><span class="sxs-lookup"><span data-stu-id="0ccb1-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
