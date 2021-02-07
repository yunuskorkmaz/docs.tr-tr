---
description: 'Hakkında daha fazla bilgi edinin: <udpAnnouncementEndpoint>'
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: f59e3e5365666835e910249e2cb37c2ce0e465e4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749265"
---
# \<udpAnnouncementEndpoint>

<span data-ttu-id="a92ad-102">Bu yapılandırma öğesi, bir UDP bağlaması üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a92ad-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="a92ad-103">Bu, sabit bir sözleşmeye sahiptir ve iki keşif sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="a92ad-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="a92ad-104">Ayrıca, bir sabit UDP bağlaması ve WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery sürüm 1,1) belirtilen şekilde varsayılan bir adres değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="a92ad-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="a92ad-105">Duyuru iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a92ad-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a92ad-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a92ad-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a92ad-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a92ad-107">Attributes and Elements</span></span>  

 <span data-ttu-id="a92ad-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a92ad-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a92ad-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a92ad-109">Attributes</span></span>  
  
|<span data-ttu-id="a92ad-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a92ad-110">Attribute</span></span>|<span data-ttu-id="a92ad-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a92ad-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a92ad-112">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="a92ad-112">discoveryVersion</span></span>|<span data-ttu-id="a92ad-113">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a92ad-113">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="a92ad-114">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="a92ad-114">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="a92ad-115">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="a92ad-115">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="a92ad-116">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="a92ad-116">maxAnnouncementDelay</span></span>|<span data-ttu-id="a92ad-117">Bulma protokolünün bir Merhaba ileti göndermeden önce bekleyeceği en büyük değeri belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="a92ad-117">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="a92ad-118">İletiler, gönderilmeden önce 0 ile bu özniteliğin değeri arasında rastgele bir zaman değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="a92ad-118">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="a92ad-119">Bu öznitelik, ağ fırtınalarını 'yi engellemek için küçük, rastgele bir gecikme ayarlamak için kullanılır ve tüm hizmetler aynı anda yeniden çevrimiçi duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="a92ad-119">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="a92ad-120">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="a92ad-120">multicastAddress</span></span>|<span data-ttu-id="a92ad-121">Bulma iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="a92ad-121">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="a92ad-122">Varsayılan değer, protokol belirtimine uyumlu olan çok noktaya yayın adresidir.</span><span class="sxs-lookup"><span data-stu-id="a92ad-122">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="a92ad-123">name</span><span class="sxs-lookup"><span data-stu-id="a92ad-123">name</span></span>|<span data-ttu-id="a92ad-124">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a92ad-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="a92ad-125">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a92ad-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a92ad-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a92ad-126">Child Elements</span></span>  
  
|<span data-ttu-id="a92ad-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="a92ad-127">Element</span></span>|<span data-ttu-id="a92ad-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a92ad-128">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="a92ad-129">UDP uç noktası için UDP aktarımını yapılandırmanıza izin veren ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a92ad-129">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a92ad-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a92ad-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a92ad-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="a92ad-131">Element</span></span>|<span data-ttu-id="a92ad-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a92ad-132">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a92ad-133">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a92ad-133">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a92ad-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="a92ad-134">Example</span></span>  

 <span data-ttu-id="a92ad-135">Aşağıdaki örnek, varsayılan çok noktaya yayın adresiyle bir UDP çok noktaya yayın aktarımı üzerinden duyuruyu dinleyen bir istemciyi ve belirtilen çok noktaya yayın adresiyle UDP çok noktaya yayın aktarımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a92ad-135">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="a92ad-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a92ad-136">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
