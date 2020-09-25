---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 08ca8a2bfcf5b905152f7e64a45cbae4992a7b78
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192379"
---
# \<defaultPorts>

<span data-ttu-id="6b2cd-101">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="6b2cd-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="6b2cd-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b2cd-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b2cd-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2cd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6b2cd-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b2cd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b2cd-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b2cd-105">Attributes</span></span>  

 <span data-ttu-id="6b2cd-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b2cd-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b2cd-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2cd-107">Child Elements</span></span>  
  
|<span data-ttu-id="6b2cd-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b2cd-108">Element</span></span>|<span data-ttu-id="6b2cd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2cd-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b2cd-110">\<add> durumunu \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="6b2cd-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="6b2cd-111">İstemci uygulamanın dinlediği varsayılan bir iletişim uç noktası.</span><span class="sxs-lookup"><span data-stu-id="6b2cd-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b2cd-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b2cd-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6b2cd-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b2cd-113">Element</span></span>|<span data-ttu-id="6b2cd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b2cd-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="6b2cd-115">Varsayılan bağlantı noktalarının listesi.</span><span class="sxs-lookup"><span data-stu-id="6b2cd-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b2cd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b2cd-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
