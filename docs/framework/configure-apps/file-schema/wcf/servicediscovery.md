---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399635"
---
# <a name="servicediscovery"></a><span data-ttu-id="c83c1-101">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c83c1-101">\<serviceDiscovery></span></span>
<span data-ttu-id="c83c1-102">Hizmet uç noktalarının bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c83c1-102">Specifies the discoverability of service endpoints.</span></span>  
  
<span data-ttu-id="c83c1-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c83c1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c83c1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c83c1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c83c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c83c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="c83c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83c1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c83c1-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c83c1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c83c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c83c1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c83c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c83c1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c83c1-112">Attributes</span></span>  
 <span data-ttu-id="c83c1-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="c83c1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c83c1-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c83c1-114">Child Elements</span></span>  
  
|<span data-ttu-id="c83c1-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c83c1-115">Element</span></span>|<span data-ttu-id="c83c1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c83c1-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c83c1-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="c83c1-117">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="c83c1-118">Duyuru uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c83c1-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="c83c1-119">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="c83c1-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="c83c1-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="c83c1-120">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="c83c1-121">Bulma uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c83c1-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="c83c1-122">Bulma iletilerinin dinleyeceği uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="c83c1-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c83c1-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c83c1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c83c1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c83c1-124">Element</span></span>|<span data-ttu-id="c83c1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c83c1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c83c1-126">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c83c1-126">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c83c1-127">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c83c1-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c83c1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c83c1-128">Remarks</span></span>  
 <span data-ttu-id="c83c1-129">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bu hizmetin tüm uç noktalarını bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c83c1-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="c83c1-130">Bu uç noktaların bulma özelliklerini, [ \<DiscoveryEndpoint >](discoveryendpoint.md) veya [ \<AnnouncementEndpoint >](announcementendpoint.md) alt öğelerini kullanarak daha ayrıntılı bir şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c83c1-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="c83c1-131">Hizmet duyuruları göndermek için kullanılacak uç nokta yapılandırmasını belirterek duyuruları yapılandırmak için [ AnnouncementEndpoint>bölümünükullanın(çevrimiçi/Merhabaveçevrimdışı/bye).\<](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-131">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="c83c1-132">Bulma iletilerinin dinleyeceği uç noktayı el ile belirtmek için [ DiscoveryEndpoint>bölümünükullanın.\<](discoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="c83c1-132">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c83c1-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="c83c1-133">Example</span></span>  
 <span data-ttu-id="c83c1-134">Aşağıdaki yapılandırma örneği, Hesaplatorservice 'in keşfedilecek olduğunu belirtir ve isteğe bağlı olarak kullanılacak duyuru uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c83c1-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="c83c1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c83c1-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
