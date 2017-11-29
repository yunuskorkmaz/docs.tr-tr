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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="05042-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="05042-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="05042-103">Meta veri adresi istek iletisi üst bilgilerinden alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="05042-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="05042-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="05042-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="05042-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="05042-105">\<behaviors></span></span>  
<span data-ttu-id="05042-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="05042-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="05042-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="05042-107">\<behavior></span></span>  
<span data-ttu-id="05042-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="05042-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05042-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05042-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05042-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="05042-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05042-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05042-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05042-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="05042-112">Attributes</span></span>  
 <span data-ttu-id="05042-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="05042-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05042-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="05042-114">Child Elements</span></span>  
  
|<span data-ttu-id="05042-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="05042-115">Element</span></span>|<span data-ttu-id="05042-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05042-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05042-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="05042-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="05042-118">İstemci uygulaması dinlediği varsayılan iletişim uç noktalarını listeleme varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="05042-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05042-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="05042-119">Parent Elements</span></span>  
  
|<span data-ttu-id="05042-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="05042-120">Element</span></span>|<span data-ttu-id="05042-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05042-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05042-122">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="05042-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="05042-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="05042-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05042-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05042-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
