---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 7e661570f8b94b979595a615b3f6819d41ed5e35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="acebe-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="acebe-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="acebe-103">Meta veri adresi istek iletisi üst bilgilerinden alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="acebe-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="acebe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="acebe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="acebe-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="acebe-105">\<behaviors></span></span>  
<span data-ttu-id="acebe-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="acebe-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="acebe-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="acebe-107">\<behavior></span></span>  
<span data-ttu-id="acebe-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="acebe-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acebe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acebe-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acebe-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="acebe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="acebe-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="acebe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acebe-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="acebe-112">Attributes</span></span>  
 <span data-ttu-id="acebe-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="acebe-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="acebe-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="acebe-114">Child Elements</span></span>  
  
|<span data-ttu-id="acebe-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="acebe-115">Element</span></span>|<span data-ttu-id="acebe-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acebe-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acebe-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="acebe-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="acebe-118">İstemci uygulaması dinlediği varsayılan iletişim uç noktalarını listeleme varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="acebe-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acebe-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="acebe-119">Parent Elements</span></span>  
  
|<span data-ttu-id="acebe-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="acebe-120">Element</span></span>|<span data-ttu-id="acebe-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acebe-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acebe-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="acebe-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="acebe-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="acebe-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acebe-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acebe-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
