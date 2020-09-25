---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: a323e6da0eb173e303d70cc3b7309b898a805573
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172820"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="0ebd2-101">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0ebd2-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="0ebd2-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ebd2-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ebd2-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ebd2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0ebd2-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ebd2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ebd2-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ebd2-105">Attributes</span></span>  

 <span data-ttu-id="0ebd2-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="0ebd2-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ebd2-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ebd2-107">Child Elements</span></span>  
  
|<span data-ttu-id="0ebd2-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ebd2-108">Element</span></span>|<span data-ttu-id="0ebd2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebd2-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="0ebd2-110">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="0ebd2-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ebd2-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0ebd2-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0ebd2-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="0ebd2-112">Element</span></span>|<span data-ttu-id="0ebd2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ebd2-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0ebd2-114">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0ebd2-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ebd2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ebd2-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
