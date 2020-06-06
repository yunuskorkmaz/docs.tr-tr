---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398067"
---
# \<defaultPorts>
<span data-ttu-id="561a2-101">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="561a2-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="561a2-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="561a2-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="561a2-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="561a2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="561a2-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="561a2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="561a2-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="561a2-105">Attributes</span></span>  
 <span data-ttu-id="561a2-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="561a2-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="561a2-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="561a2-107">Child Elements</span></span>  
  
|<span data-ttu-id="561a2-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="561a2-108">Element</span></span>|<span data-ttu-id="561a2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="561a2-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="561a2-110">\<add>durumunu\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="561a2-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="561a2-111">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="561a2-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="561a2-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="561a2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="561a2-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="561a2-113">Element</span></span>|<span data-ttu-id="561a2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="561a2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="561a2-115">Varsayılan bağlantı noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="561a2-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="561a2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="561a2-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
