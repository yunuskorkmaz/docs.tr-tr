---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1886f6efdfaa8f4105e6ef16ad72093867e0f3fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="b4a64-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="b4a64-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="b4a64-103">İstemci uygulaması dinlediği varsayılan iletişim uç noktalarını listeleme varsayılan bağlantı noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b4a64-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="b4a64-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b4a64-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b4a64-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="b4a64-105">\<behaviors></span></span>  
<span data-ttu-id="b4a64-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b4a64-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b4a64-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b4a64-107">\<behavior></span></span>  
<span data-ttu-id="b4a64-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="b4a64-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="b4a64-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="b4a64-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a64-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4a64-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4a64-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4a64-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b4a64-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4a64-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4a64-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b4a64-113">Attributes</span></span>  
 <span data-ttu-id="b4a64-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="b4a64-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4a64-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4a64-115">Child Elements</span></span>  
  
|<span data-ttu-id="b4a64-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4a64-116">Element</span></span>|<span data-ttu-id="b4a64-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4a64-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4a64-118">\<Ekle >, \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="b4a64-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="b4a64-119">İstemci uygulaması dinlediği bir varsayılan iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="b4a64-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4a64-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b4a64-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b4a64-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="b4a64-121">Element</span></span>|<span data-ttu-id="b4a64-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4a64-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4a64-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="b4a64-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="b4a64-124">Varsayılan bağlantı noktaları listesi.</span><span class="sxs-lookup"><span data-stu-id="b4a64-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4a64-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4a64-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
