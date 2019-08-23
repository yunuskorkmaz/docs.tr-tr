---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926545"
---
# <a name="announcementendpoint"></a><span data-ttu-id="ccd1f-101">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="ccd1f-101">\<announcementEndpoint></span></span>
<span data-ttu-id="ccd1f-102">Bu yapılandırma öğesi, bir sabit duyuru sözleşmesiyle standart uç noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="ccd1f-103">Bir hizmet, isteğe bağlı olarak açık veya kapalı olduğunda bir çevrimiçi ve çevrimdışı duyuru iletisi göndererek kullanılabilirliğini duyurur.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="ccd1f-104">Windows Communication Foundation (WCF) hizmeti, [ \<servicediscovery >](servicediscovery.md) öğesindeki duyuru uç noktalarını belirtir ve duyuruları gerçekleştirmek için AnnouncementClient 'ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="ccd1f-105">Diğer hizmetten gelen duyuruyu dinlemek isteyen bir istemci aslında bir WCF hizmeti olarak davranır; Bu nedenle, [ \<Hizmetler >](services.md) bölümünde söz konusu istemcinin duyuru uç noktalarını yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
<span data-ttu-id="ccd1f-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccd1f-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccd1f-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ccd1f-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd1f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccd1f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccd1f-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccd1f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ccd1f-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccd1f-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ccd1f-111">Attributes</span></span>  
  
|<span data-ttu-id="ccd1f-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ccd1f-112">Attribute</span></span>|<span data-ttu-id="ccd1f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccd1f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccd1f-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="ccd1f-114">discoveryVersion</span></span>|<span data-ttu-id="ccd1f-115">WS-Discovery protokolünün iki sürümünden birini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="ccd1f-116">Geçerli değerler WSDiscovery11 ve WSDiscoveryApril2005.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="ccd1f-117">Bu değer türünde <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="ccd1f-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="ccd1f-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="ccd1f-119">Bulma protokolünün bir Merhaba ileti göndermeden önce bekleyeceği en büyük değeri belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="ccd1f-120">İletiler, gönderilmeden önce 0 ile bu özniteliğin değeri arasında rastgele bir zaman değeri bekler.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="ccd1f-121">Bu öznitelik, ağ fırtınalarını 'yi engellemek için küçük, rastgele bir gecikme ayarlamak için kullanılır ve tüm hizmetler aynı anda yeniden çevrimiçi duruma gelir.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="ccd1f-122">name</span><span class="sxs-lookup"><span data-stu-id="ccd1f-122">name</span></span>|<span data-ttu-id="ccd1f-123">Standart uç nokta yapılandırmasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="ccd1f-124">Ad, bir standart uç noktayı `endpointConfiguration` yapılandırmaya bağlamak için hizmet uç noktasının özniteliğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccd1f-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccd1f-125">Child Elements</span></span>  
 <span data-ttu-id="ccd1f-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccd1f-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccd1f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ccd1f-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ccd1f-128">Element</span></span>|<span data-ttu-id="ccd1f-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccd1f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccd1f-130">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ccd1f-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ccd1f-131">Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ccd1f-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccd1f-132">Example</span></span>  
 <span data-ttu-id="ccd1f-133">Aşağıdaki örnek, http ve PEERNET üzerinden bildiri iletilerini dinleyen bir istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccd1f-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccd1f-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
