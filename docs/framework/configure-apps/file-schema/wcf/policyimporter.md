---
description: 'Hakkında daha fazla bilgi edinin: <policyImporter>'
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 2103c424aef081b72fa822ed207537195b8fdea9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683521"
---
# \<policyImporter>

<span data-ttu-id="77b03-102">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen bir ilke İçeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="77b03-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="77b03-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="77b03-103">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77b03-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="77b03-104">Attributes and Elements</span></span>  

 <span data-ttu-id="77b03-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77b03-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77b03-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="77b03-106">Attributes</span></span>  
  
|<span data-ttu-id="77b03-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="77b03-107">Attribute</span></span>|<span data-ttu-id="77b03-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77b03-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="77b03-109">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="77b03-109">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77b03-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="77b03-110">Child Elements</span></span>  

 <span data-ttu-id="77b03-111">Yok</span><span class="sxs-lookup"><span data-stu-id="77b03-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77b03-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="77b03-112">Parent Elements</span></span>  
  
|<span data-ttu-id="77b03-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="77b03-113">Element</span></span>|<span data-ttu-id="77b03-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77b03-114">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="77b03-115">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="77b03-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77b03-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77b03-116">Remarks</span></span>  

 <span data-ttu-id="77b03-117">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77b03-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b03-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77b03-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="77b03-119">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="77b03-119">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="77b03-120">İstemciler</span><span class="sxs-lookup"><span data-stu-id="77b03-120">Clients</span></span>](../../../wcf/feature-details/clients.md)
