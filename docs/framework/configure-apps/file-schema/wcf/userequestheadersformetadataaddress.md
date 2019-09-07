---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399199"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="36989-101">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="36989-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="36989-102">İstek iletisi başlıklarından meta veri adresi bilgilerinin alınmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="36989-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="36989-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="36989-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="36989-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="36989-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="36989-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="36989-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="36989-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="36989-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="36989-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="36989-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="36989-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useRequestHeadersForMetadataAddress >**</span><span class="sxs-lookup"><span data-stu-id="36989-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36989-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36989-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36989-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36989-110">Attributes and Elements</span></span>  
 <span data-ttu-id="36989-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="36989-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36989-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36989-112">Attributes</span></span>  
 <span data-ttu-id="36989-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="36989-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36989-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36989-114">Child Elements</span></span>  
  
|<span data-ttu-id="36989-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="36989-115">Element</span></span>|<span data-ttu-id="36989-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36989-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36989-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="36989-117">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="36989-118">Varsayılan bağlantı noktalarının, istemci uygulamanın dinlediği varsayılan iletişim uç noktalarını listelemesi.</span><span class="sxs-lookup"><span data-stu-id="36989-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36989-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36989-119">Parent Elements</span></span>  
  
|<span data-ttu-id="36989-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="36989-120">Element</span></span>|<span data-ttu-id="36989-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36989-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36989-122">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="36989-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="36989-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="36989-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36989-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36989-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
