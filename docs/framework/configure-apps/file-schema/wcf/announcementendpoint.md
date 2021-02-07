---
description: 'Hakkında daha fazla bilgi edinin: <announcementEndpoint>'
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: d010abb789a4401e9f0591f34edb29ec2036f16e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749928"
---
# \<announcementEndpoint>

<span data-ttu-id="55c36-102">Bu yapılandırma öğesi, bir sabit duyuru sözleşmesiyle standart uç noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55c36-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="55c36-103">Bir hizmet, isteğe bağlı olarak açık veya kapalı olduğunda bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek kullanılabilirliğini duyurur.</span><span class="sxs-lookup"><span data-stu-id="55c36-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="55c36-104">Windows Communication Foundation (WCF) hizmeti, öğesindeki duyuru uç noktalarını belirtir [\<serviceDiscovery>](servicediscovery.md) ve duyuruları gerçekleştirmek Için AnnouncementClient kullanır.</span><span class="sxs-lookup"><span data-stu-id="55c36-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="55c36-105">Diğer hizmetten gelen duyuruyu dinlemek isteyen bir istemci aslında bir WCF hizmeti olarak davranır; Bu nedenle, bölümünde söz konusu istemcinin duyuru uç noktalarını yapılandırmanız gerekir [\<services>](services.md) .</span><span class="sxs-lookup"><span data-stu-id="55c36-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="55c36-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="55c36-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55c36-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c36-107">Attributes and Elements</span></span>  

 <span data-ttu-id="55c36-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55c36-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55c36-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55c36-109">Attributes</span></span>  
  
|<span data-ttu-id="55c36-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55c36-110">Attribute</span></span>|<span data-ttu-id="55c36-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c36-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55c36-112">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="55c36-112">discoveryVersion</span></span>|<span data-ttu-id="55c36-113">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="55c36-113">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="55c36-114">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="55c36-114">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="55c36-115">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="55c36-115">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="55c36-116">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="55c36-116">maxAnnouncementDelay</span></span>|<span data-ttu-id="55c36-117">Bulma protokolünün bir Merhaba ileti göndermeden önce bekleyeceği en büyük değeri belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="55c36-117">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="55c36-118">İletiler, gönderilmeden önce 0 ile bu özniteliğin değeri arasında rastgele bir zaman değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="55c36-118">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="55c36-119">Bu öznitelik, ağ fırtınalarını 'yi engellemek için küçük, rastgele bir gecikme ayarlamak için kullanılır ve tüm hizmetler aynı anda yeniden çevrimiçi duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="55c36-119">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="55c36-120">name</span><span class="sxs-lookup"><span data-stu-id="55c36-120">name</span></span>|<span data-ttu-id="55c36-121">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="55c36-121">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="55c36-122">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55c36-122">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55c36-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c36-123">Child Elements</span></span>  

 <span data-ttu-id="55c36-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="55c36-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55c36-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c36-125">Parent Elements</span></span>  
  
|<span data-ttu-id="55c36-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="55c36-126">Element</span></span>|<span data-ttu-id="55c36-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c36-127">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="55c36-128">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="55c36-128">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="55c36-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="55c36-129">Example</span></span>  

 <span data-ttu-id="55c36-130">Aşağıdaki örnek, http ve PEERNET üzerinden bildiri iletilerini dinleyen bir istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="55c36-130">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="55c36-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55c36-131">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
