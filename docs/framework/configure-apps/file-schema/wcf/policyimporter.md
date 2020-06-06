---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855056"
---
# \<policyImporter>
<span data-ttu-id="d880f-101">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen bir ilke İçeri Aktarıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d880f-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="d880f-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d880f-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d880f-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d880f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d880f-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d880f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d880f-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d880f-105">Attributes</span></span>  
  
|<span data-ttu-id="d880f-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d880f-106">Attribute</span></span>|<span data-ttu-id="d880f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d880f-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d880f-108">Bu öğenin türü.</span><span class="sxs-lookup"><span data-stu-id="d880f-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d880f-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d880f-109">Child Elements</span></span>  
 <span data-ttu-id="d880f-110">Yok</span><span class="sxs-lookup"><span data-stu-id="d880f-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d880f-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d880f-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d880f-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="d880f-112">Element</span></span>|<span data-ttu-id="d880f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d880f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="d880f-114">Bağlamalarla ilgili özel ilke onaylarının içeri aktarılacağını denetleyen tüm ilke içe aktarımlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d880f-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d880f-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d880f-115">Remarks</span></span>  
 <span data-ttu-id="d880f-116">İlke İçeri Aktarıcı, bağlama özellikleriyle ilgili özel ilke onaylamalarını aramak ve onaylama için gereken özellikleri uygulayan özel bir bağlama öğesi eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d880f-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d880f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d880f-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="d880f-118">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d880f-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="d880f-119">İstemciler</span><span class="sxs-lookup"><span data-stu-id="d880f-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
