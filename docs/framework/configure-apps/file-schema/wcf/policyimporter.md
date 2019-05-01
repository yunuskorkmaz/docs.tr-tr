---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 81f38d2a163163ca7255ca546bbddbbb58fa3a1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783194"
---
# <a name="policyimporter"></a><span data-ttu-id="ef847-101">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="ef847-101">\<policyImporter></span></span>
<span data-ttu-id="ef847-102">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen bir ilke içeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef847-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="ef847-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef847-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef847-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="ef847-104">\<client></span></span>  
<span data-ttu-id="ef847-105">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="ef847-105">\<metadata></span></span>  
<span data-ttu-id="ef847-106">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="ef847-106">\<policyImporters></span></span>  
<span data-ttu-id="ef847-107">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="ef847-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef847-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef847-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef847-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef847-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ef847-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef847-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef847-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef847-111">Attributes</span></span>  
  
|<span data-ttu-id="ef847-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ef847-112">Attribute</span></span>|<span data-ttu-id="ef847-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef847-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ef847-114">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="ef847-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef847-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef847-115">Child Elements</span></span>  
 <span data-ttu-id="ef847-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="ef847-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef847-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef847-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ef847-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef847-118">Element</span></span>|<span data-ttu-id="ef847-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef847-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef847-120">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="ef847-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="ef847-121">Bağlamalar hakkında özel ilke onaylamalarını içe denetleyen tüm ilke ımporters belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef847-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef847-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef847-122">Remarks</span></span>  
 <span data-ttu-id="ef847-123">İlke içeri Aktarıcı yanı sıra arama özellikleri bağlama hakkında özel ilke onaylamalarını onay gerektiren özellikleri uygulayan bir özel bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef847-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef847-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef847-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="ef847-125">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ef847-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="ef847-126">İstemciler</span><span class="sxs-lookup"><span data-stu-id="ef847-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
