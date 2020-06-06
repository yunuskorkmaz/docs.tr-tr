---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854922"
---
# \<udpAnnouncementEndpoint>
<span data-ttu-id="8b1db-101">Bu yapılandırma öğesi, bir UDP bağlaması üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b1db-101">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="8b1db-102">Bu, sabit bir sözleşmeye sahiptir ve iki keşif sürümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="8b1db-102">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="8b1db-103">Buna ek olarak, bir sabit UDP bağlaması ve WS-Discovery belirtimleri (WS-Discovery Nisan 2005 veya WS-Discovery sürüm 1,1) belirtilen varsayılan bir adres değeri vardır.</span><span class="sxs-lookup"><span data-stu-id="8b1db-103">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="8b1db-104">Duyuru iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b1db-104">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="8b1db-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b1db-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b1db-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b1db-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8b1db-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b1db-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b1db-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b1db-108">Attributes</span></span>  
  
|<span data-ttu-id="8b1db-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8b1db-109">Attribute</span></span>|<span data-ttu-id="8b1db-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b1db-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b1db-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="8b1db-111">discoveryVersion</span></span>|<span data-ttu-id="8b1db-112">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8b1db-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="8b1db-113">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="8b1db-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="8b1db-114">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="8b1db-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="8b1db-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="8b1db-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="8b1db-116">Bulma protokolünün bir Merhaba ileti göndermeden önce bekleyeceği en büyük değeri belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="8b1db-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="8b1db-117">İletiler, gönderilmeden önce 0 ile bu özniteliğin değeri arasında rastgele bir zaman değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="8b1db-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="8b1db-118">Bu öznitelik, ağ fırtınalarını 'yi engellemek için küçük, rastgele bir gecikme ayarlamak için kullanılır ve tüm hizmetler aynı anda yeniden çevrimiçi duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="8b1db-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="8b1db-119">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="8b1db-119">multicastAddress</span></span>|<span data-ttu-id="8b1db-120">Bulma iletilerini göndermek ve almak için kullanılacak çok noktaya yayın adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="8b1db-120">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="8b1db-121">Varsayılan değer, protokol belirtimine uyumlu olan çok noktaya yayın adresidir.</span><span class="sxs-lookup"><span data-stu-id="8b1db-121">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="8b1db-122">name</span><span class="sxs-lookup"><span data-stu-id="8b1db-122">name</span></span>|<span data-ttu-id="8b1db-123">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8b1db-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="8b1db-124">Ad, `endpointConfiguration` bir standart uç noktayı yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b1db-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b1db-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b1db-125">Child Elements</span></span>  
  
|<span data-ttu-id="8b1db-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b1db-126">Element</span></span>|<span data-ttu-id="8b1db-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b1db-127">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="8b1db-128">UDP uç noktası için UDP aktarımını yapılandırmanıza izin veren ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8b1db-128">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b1db-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b1db-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8b1db-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b1db-130">Element</span></span>|<span data-ttu-id="8b1db-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b1db-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="8b1db-132">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8b1db-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8b1db-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b1db-133">Example</span></span>  
 <span data-ttu-id="8b1db-134">Aşağıdaki örnek, varsayılan çok noktaya yayın adresiyle bir UDP çok noktaya yayın aktarımı üzerinden duyuruyu dinleyen bir istemciyi ve belirtilen çok noktaya yayın adresiyle UDP çok noktaya yayın aktarımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b1db-134">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b1db-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b1db-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
