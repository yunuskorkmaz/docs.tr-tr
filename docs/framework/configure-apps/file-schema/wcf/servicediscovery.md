---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: b38496b77d80fcb66b1b48485a9eef6abfd72299
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198827"
---
# \<serviceDiscovery>

<span data-ttu-id="d4d7f-101">Hizmet uç noktalarının bulunabilirliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="d4d7f-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4d7f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4d7f-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4d7f-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d4d7f-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4d7f-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4d7f-105">Attributes</span></span>  

 <span data-ttu-id="d4d7f-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4d7f-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4d7f-107">Child Elements</span></span>  
  
|<span data-ttu-id="d4d7f-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4d7f-108">Element</span></span>|<span data-ttu-id="d4d7f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4d7f-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="d4d7f-110">Duyuru uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="d4d7f-111">Duyuru iletileri göndermek için kullanılacak uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="d4d7f-112">Bulma uç noktaları koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="d4d7f-113">Bulma iletilerinin dinleyeceği uç noktaları belirtmek için bu bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4d7f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4d7f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d4d7f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4d7f-115">Element</span></span>|<span data-ttu-id="d4d7f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4d7f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d4d7f-117">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4d7f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4d7f-118">Remarks</span></span>  

 <span data-ttu-id="d4d7f-119">Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi bu hizmetin tüm uç noktalarını bulunabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="d4d7f-120">[\<discoveryEndpoint>](discoveryendpoint.md)Veya alt öğelerini kullanarak bu uç noktaların bulma özelliklerini daha fazla yapılandırabilirsiniz [\<announcementEndpoint>](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="d4d7f-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="d4d7f-121">[\<announcementEndpoint>](announcementendpoint.md)Hizmet duyuruları göndermek için kullanılacak uç nokta yapılandırmasını belirterek duyuruları yapılandırmak için bölümünü kullanın (çevrimiçi/Merhaba ve çevrimdışı/bye).</span><span class="sxs-lookup"><span data-stu-id="d4d7f-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="d4d7f-122">[\<discoveryEndpoint>](discoveryendpoint.md)Bulma iletilerinin dinleyeceği uç noktayı el ile belirtmek için bölümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4d7f-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4d7f-123">Example</span></span>  

 <span data-ttu-id="d4d7f-124">Aşağıdaki yapılandırma örneği, Hesaplatorservice 'in keşfedilecek olduğunu belirtir ve isteğe bağlı olarak kullanılacak duyuru uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4d7f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d7f-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
