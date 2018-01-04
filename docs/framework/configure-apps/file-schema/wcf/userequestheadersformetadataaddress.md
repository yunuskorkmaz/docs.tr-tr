---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94dafcfa68463a0e82696cf16a96abe45632e72a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="20733-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="20733-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="20733-103">Meta veri adresi istek iletisi üst bilgilerinden alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="20733-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="20733-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="20733-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="20733-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="20733-105">\<behaviors></span></span>  
<span data-ttu-id="20733-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="20733-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="20733-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="20733-107">\<behavior></span></span>  
<span data-ttu-id="20733-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="20733-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20733-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20733-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20733-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20733-110">Attributes and Elements</span></span>  
 <span data-ttu-id="20733-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20733-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20733-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20733-112">Attributes</span></span>  
 <span data-ttu-id="20733-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="20733-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20733-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20733-114">Child Elements</span></span>  
  
|<span data-ttu-id="20733-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="20733-115">Element</span></span>|<span data-ttu-id="20733-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20733-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20733-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="20733-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="20733-118">İstemci uygulaması dinlediği varsayılan iletişim uç noktalarını listeleme varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20733-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20733-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20733-119">Parent Elements</span></span>  
  
|<span data-ttu-id="20733-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="20733-120">Element</span></span>|<span data-ttu-id="20733-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20733-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20733-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="20733-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="20733-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="20733-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="20733-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20733-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
