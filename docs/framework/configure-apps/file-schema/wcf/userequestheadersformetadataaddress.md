---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399199"
---
# \<useRequestHeadersForMetadataAddress>
<span data-ttu-id="815b0-101">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="815b0-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="815b0-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="815b0-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="815b0-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="815b0-103">Attributes and Elements</span></span>  
 <span data-ttu-id="815b0-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="815b0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="815b0-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="815b0-105">Attributes</span></span>  
 <span data-ttu-id="815b0-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="815b0-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="815b0-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="815b0-107">Child Elements</span></span>  
  
|<span data-ttu-id="815b0-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="815b0-108">Element</span></span>|<span data-ttu-id="815b0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="815b0-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="815b0-110">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="815b0-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="815b0-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="815b0-111">Parent Elements</span></span>  
  
|<span data-ttu-id="815b0-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="815b0-112">Element</span></span>|<span data-ttu-id="815b0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="815b0-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="815b0-114">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="815b0-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="815b0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="815b0-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
