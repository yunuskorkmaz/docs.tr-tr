---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2f7de066a1b91e9fa22fbe0213e221c6f4bbe617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="f2b33-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="f2b33-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="f2b33-103">İstemci uygulaması dinlediği varsayılan iletişim uç noktalarını listeleme varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f2b33-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="f2b33-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f2b33-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2b33-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f2b33-105">\<behaviors></span></span>  
<span data-ttu-id="f2b33-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f2b33-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f2b33-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f2b33-107">\<behavior></span></span>  
<span data-ttu-id="f2b33-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="f2b33-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="f2b33-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="f2b33-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b33-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2b33-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2b33-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2b33-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f2b33-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2b33-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2b33-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2b33-113">Attributes</span></span>  
 <span data-ttu-id="f2b33-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2b33-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2b33-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2b33-115">Child Elements</span></span>  
  
|<span data-ttu-id="f2b33-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2b33-116">Element</span></span>|<span data-ttu-id="f2b33-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2b33-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2b33-118">\<Ekle >, \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="f2b33-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="f2b33-119">İstemci uygulaması dinlediği bir varsayılan iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="f2b33-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2b33-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2b33-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f2b33-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2b33-121">Element</span></span>|<span data-ttu-id="f2b33-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2b33-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2b33-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="f2b33-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="f2b33-124">Varsayılan bağlantı noktaları listesi.</span><span class="sxs-lookup"><span data-stu-id="f2b33-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2b33-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2b33-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
