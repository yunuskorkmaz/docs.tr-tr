---
description: 'Hakkında daha fazla bilgi edinin: <serviceDiscovery>'
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: d6df5b8d51763429829c2ea3c2593003720b7179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682858"
---
# \<serviceDiscovery>

<span data-ttu-id="b3c73-102">Hizmet uç noktalarının bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3c73-102">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="b3c73-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3c73-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3c73-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3c73-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b3c73-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3c73-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3c73-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b3c73-106">Attributes</span></span>  

 <span data-ttu-id="b3c73-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="b3c73-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b3c73-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3c73-108">Child Elements</span></span>  
  
|<span data-ttu-id="b3c73-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="b3c73-109">Element</span></span>|<span data-ttu-id="b3c73-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3c73-110">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="b3c73-111">Duyuru uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b3c73-111">A collection of announcement endpoints.</span></span> <span data-ttu-id="b3c73-112">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3c73-112">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="b3c73-113">Bulma uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b3c73-113">A collection of discovery endpoints.</span></span> <span data-ttu-id="b3c73-114">Bulma iletilerinin dinleyeceği uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3c73-114">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3c73-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b3c73-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b3c73-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="b3c73-116">Element</span></span>|<span data-ttu-id="b3c73-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3c73-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b3c73-118">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3c73-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c73-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3c73-119">Remarks</span></span>  

 <span data-ttu-id="b3c73-120">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bu hizmetin tüm uç noktalarını bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b3c73-120">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="b3c73-121">[\<discoveryEndpoint>](discoveryendpoint.md)Veya alt öğelerini kullanarak bu uç noktaların bulma özelliklerini daha fazla yapılandırabilirsiniz [\<announcementEndpoint>](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="b3c73-121">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="b3c73-122">[\<announcementEndpoint>](announcementendpoint.md)Hizmet duyuruları göndermek için kullanılacak uç nokta yapılandırmasını belirterek duyuruları yapılandırmak için bölümünü kullanın (çevrimiçi/Merhaba ve çevrimdışı/bye).</span><span class="sxs-lookup"><span data-stu-id="b3c73-122">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="b3c73-123">[\<discoveryEndpoint>](discoveryendpoint.md)Bulma iletilerinin dinleyeceği uç noktayı el ile belirtmek için bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3c73-123">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3c73-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3c73-124">Example</span></span>  

 <span data-ttu-id="b3c73-125">Aşağıdaki yapılandırma örneği, Hesaplatorservice 'in keşfedilecek olduğunu belirtir ve isteğe bağlı olarak kullanılacak duyuru uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3c73-125">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3c73-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3c73-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
