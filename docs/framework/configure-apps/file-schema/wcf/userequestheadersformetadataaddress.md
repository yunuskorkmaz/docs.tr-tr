---
description: 'Hakkında daha fazla bilgi edinin: <useRequestHeadersForMetadataAddress>'
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 53636b5890eb54095737e2ed62a75e9b81c1c1f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664437"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="5bb69-102">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5bb69-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="5bb69-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="5bb69-103">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bb69-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bb69-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5bb69-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5bb69-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bb69-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5bb69-106">Attributes</span></span>  

 <span data-ttu-id="5bb69-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="5bb69-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5bb69-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bb69-108">Child Elements</span></span>  
  
|<span data-ttu-id="5bb69-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="5bb69-109">Element</span></span>|<span data-ttu-id="5bb69-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bb69-110">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="5bb69-111">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="5bb69-111">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bb69-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5bb69-112">Parent Elements</span></span>  
  
|<span data-ttu-id="5bb69-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="5bb69-113">Element</span></span>|<span data-ttu-id="5bb69-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bb69-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5bb69-115">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5bb69-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bb69-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bb69-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
