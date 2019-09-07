---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398067"
---
# <a name="defaultports"></a><span data-ttu-id="72b34-101">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="72b34-101">\<defaultPorts></span></span>
<span data-ttu-id="72b34-102">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="72b34-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="72b34-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="72b34-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72b34-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="72b34-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="72b34-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="72b34-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="72b34-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="72b34-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="72b34-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="72b34-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="72b34-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="72b34-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="72b34-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultPorts >**</span><span class="sxs-lookup"><span data-stu-id="72b34-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b34-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72b34-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72b34-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="72b34-111">Attributes and Elements</span></span>  
 <span data-ttu-id="72b34-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72b34-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72b34-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72b34-113">Attributes</span></span>  
 <span data-ttu-id="72b34-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="72b34-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72b34-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="72b34-115">Child Elements</span></span>  
  
|<span data-ttu-id="72b34-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="72b34-116">Element</span></span>|<span data-ttu-id="72b34-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72b34-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72b34-118">\<\<defaultPort > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="72b34-118">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="72b34-119">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="72b34-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72b34-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="72b34-120">Parent Elements</span></span>  
  
|<span data-ttu-id="72b34-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="72b34-121">Element</span></span>|<span data-ttu-id="72b34-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72b34-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72b34-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="72b34-123">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="72b34-124">Varsayılan bağlantı noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="72b34-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72b34-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72b34-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
