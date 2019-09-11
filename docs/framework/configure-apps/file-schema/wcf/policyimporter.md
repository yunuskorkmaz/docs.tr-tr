---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855056"
---
# <a name="policyimporter"></a><span data-ttu-id="9dd0e-101">\<Policyımporter ></span><span class="sxs-lookup"><span data-stu-id="9dd0e-101">\<policyImporter></span></span>
<span data-ttu-id="9dd0e-102">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen bir ilke İçeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
<span data-ttu-id="9dd0e-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9dd0e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9dd0e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9dd0e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9dd0e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="9dd0e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="9dd0e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<meta veri >** ](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="9dd0e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="9dd0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<PolicyImporters >** ](policyimporters.md)</span><span class="sxs-lookup"><span data-stu-id="9dd0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)</span></span>  
<span data-ttu-id="9dd0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Policyımporter >**</span><span class="sxs-lookup"><span data-stu-id="9dd0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd0e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dd0e-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dd0e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dd0e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9dd0e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dd0e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9dd0e-112">Attributes</span></span>  
  
|<span data-ttu-id="9dd0e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9dd0e-113">Attribute</span></span>|<span data-ttu-id="9dd0e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dd0e-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9dd0e-115">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dd0e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dd0e-116">Child Elements</span></span>  
 <span data-ttu-id="9dd0e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9dd0e-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9dd0e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9dd0e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="9dd0e-119">Element</span></span>|<span data-ttu-id="9dd0e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9dd0e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dd0e-121">\<PolicyImporters ></span><span class="sxs-lookup"><span data-stu-id="9dd0e-121">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="9dd0e-122">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dd0e-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dd0e-123">Remarks</span></span>  
 <span data-ttu-id="9dd0e-124">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd0e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd0e-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="9dd0e-126">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9dd0e-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9dd0e-127">İstemciler</span><span class="sxs-lookup"><span data-stu-id="9dd0e-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
