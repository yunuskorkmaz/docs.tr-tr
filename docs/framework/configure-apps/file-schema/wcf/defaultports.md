---
description: 'Hakkında daha fazla bilgi edinin: <defaultPorts>'
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 7cd0635568bf80734900f5e54f918150ea657322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803912"
---
# \<defaultPorts>

<span data-ttu-id="31802-102">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="31802-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="31802-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="31802-103">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31802-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31802-104">Attributes and Elements</span></span>  

 <span data-ttu-id="31802-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31802-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31802-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31802-106">Attributes</span></span>  

 <span data-ttu-id="31802-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="31802-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31802-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31802-108">Child Elements</span></span>  
  
|<span data-ttu-id="31802-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="31802-109">Element</span></span>|<span data-ttu-id="31802-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31802-110">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31802-111">\<add> durumunu \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="31802-111">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="31802-112">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="31802-112">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31802-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31802-113">Parent Elements</span></span>  
  
|<span data-ttu-id="31802-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="31802-114">Element</span></span>|<span data-ttu-id="31802-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31802-115">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="31802-116">Varsayılan bağlantı noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="31802-116">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31802-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31802-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
