---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 273bd0d5e68a661c639b82264b440b83d8127427
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933787"
---
# <a name="policyimporter"></a><span data-ttu-id="e8714-101">\<Policyımporter ></span><span class="sxs-lookup"><span data-stu-id="e8714-101">\<policyImporter></span></span>
<span data-ttu-id="e8714-102">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen bir ilke İçeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8714-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="e8714-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e8714-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e8714-104">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e8714-104">\<client></span></span>  
<span data-ttu-id="e8714-105">\<meta veri ></span><span class="sxs-lookup"><span data-stu-id="e8714-105">\<metadata></span></span>  
<span data-ttu-id="e8714-106">\<PolicyImporters ></span><span class="sxs-lookup"><span data-stu-id="e8714-106">\<policyImporters></span></span>  
<span data-ttu-id="e8714-107">\<Policyımporter ></span><span class="sxs-lookup"><span data-stu-id="e8714-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8714-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8714-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8714-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8714-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8714-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8714-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8714-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e8714-111">Attributes</span></span>  
  
|<span data-ttu-id="e8714-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e8714-112">Attribute</span></span>|<span data-ttu-id="e8714-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8714-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e8714-114">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="e8714-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8714-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8714-115">Child Elements</span></span>  
 <span data-ttu-id="e8714-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e8714-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8714-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e8714-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e8714-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e8714-118">Element</span></span>|<span data-ttu-id="e8714-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8714-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8714-120">\<PolicyImporters ></span><span class="sxs-lookup"><span data-stu-id="e8714-120">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="e8714-121">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e8714-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8714-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8714-122">Remarks</span></span>  
 <span data-ttu-id="e8714-123">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8714-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8714-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8714-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="e8714-125">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e8714-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e8714-126">İstemciler</span><span class="sxs-lookup"><span data-stu-id="e8714-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
