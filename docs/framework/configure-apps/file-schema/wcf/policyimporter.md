---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 72778ce0070d853f8b081a4889ead9524bafd0e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181355"
---
# \<policyImporter>

<span data-ttu-id="91723-101">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen bir ilke İçeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="91723-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="91723-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="91723-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91723-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91723-103">Attributes and Elements</span></span>  

 <span data-ttu-id="91723-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91723-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91723-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91723-105">Attributes</span></span>  
  
|<span data-ttu-id="91723-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="91723-106">Attribute</span></span>|<span data-ttu-id="91723-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91723-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="91723-108">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="91723-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91723-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91723-109">Child Elements</span></span>  

 <span data-ttu-id="91723-110">Yok</span><span class="sxs-lookup"><span data-stu-id="91723-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91723-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91723-111">Parent Elements</span></span>  
  
|<span data-ttu-id="91723-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="91723-112">Element</span></span>|<span data-ttu-id="91723-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91723-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="91723-114">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="91723-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91723-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91723-115">Remarks</span></span>  

 <span data-ttu-id="91723-116">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91723-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91723-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91723-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="91723-118">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="91723-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="91723-119">İstemciler</span><span class="sxs-lookup"><span data-stu-id="91723-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
