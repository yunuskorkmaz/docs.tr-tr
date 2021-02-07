---
description: 'Hakkında daha fazla bilgi edinin: <udpTransportSettings>'
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: bfd862009401fef160939fb9acaa66fc9ca23ddb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749161"
---
# \<udpTransportSettings>

<span data-ttu-id="f5288-102">Bu yapılandırma öğesi için UDP taşıma ayarlarını gösterir [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="f5288-102">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="f5288-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5288-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5288-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5288-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f5288-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5288-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5288-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f5288-106">Attributes</span></span>  
  
|<span data-ttu-id="f5288-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f5288-107">Attribute</span></span>|<span data-ttu-id="f5288-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5288-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5288-109">Duplicatemessagegeçmişini uzunluğu</span><span class="sxs-lookup"><span data-stu-id="f5288-109">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="f5288-110">Yinelenen iletileri tanımlamak için taşıma tarafından kullanılan en fazla ileti karması sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f5288-110">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="f5288-111">Yinelenen algılama işlemi, TransportManager düzeyinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="f5288-111">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="f5288-112">Bu özelliğin 0 olarak ayarlanması yinelenen algılamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f5288-112">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="f5288-113">Bu öznitelik, sistem yöneticilerinin veya geliştiricilerin yinelenen ileti algılama algoritmalarını kapatmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f5288-113">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="f5288-114">Kendi yinelenen algılama algoritmanızı uygulamak istiyorsanız bu işlem istenebilir.</span><span class="sxs-lookup"><span data-stu-id="f5288-114">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="f5288-115">Varsayılan değer 4112 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-115">The default is 4112.</span></span>|  
|<span data-ttu-id="f5288-116">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f5288-116">maxBufferPoolSize</span></span>|<span data-ttu-id="f5288-117">Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f5288-117">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="f5288-118">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="f5288-118">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="f5288-119">İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).</span><span class="sxs-lookup"><span data-stu-id="f5288-119">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="f5288-120">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-120">The default is 2.</span></span>|  
|<span data-ttu-id="f5288-121">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="f5288-121">maxPendingMessageCount</span></span>|<span data-ttu-id="f5288-122">Tek bir kanal örneği için InputQueue öğesinden alınmış ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f5288-122">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="f5288-123">InputQueue, bekleyen ileti sayısı sınırına ulaşmışsa ileti bırakılır.</span><span class="sxs-lookup"><span data-stu-id="f5288-123">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="f5288-124">Varsayılan değer 32 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-124">The default is 32.</span></span>|  
|<span data-ttu-id="f5288-125">Değerini</span><span class="sxs-lookup"><span data-stu-id="f5288-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="f5288-126">Bağlama tarafından işlenebilecek bir iletinin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f5288-126">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="f5288-127">Varsayılan değer 65507 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-127">The default value is 65507.</span></span>|  
|<span data-ttu-id="f5288-128">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="f5288-128">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="f5288-129">İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).</span><span class="sxs-lookup"><span data-stu-id="f5288-129">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="f5288-130">İleti bir tek noktaya yayın adresine gönderilirse ve karşılık gelen bir RelatesTo üstbilgisiyle yanıt iletisi alındığında, yeniden iletim erken sonlandırılabilir (yapılandırılan sayıda yeniden gönderilmeden önce).</span><span class="sxs-lookup"><span data-stu-id="f5288-130">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="f5288-131">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-131">The default value is 1.</span></span>|  
|<span data-ttu-id="f5288-132">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="f5288-132">multicastInterfaceId</span></span>|<span data-ttu-id="f5288-133">Çoklu bilgisayarlı makinelerde çok noktaya yayın trafiği gönderirken ve alırken kullanılması gereken ağ bağdaştırıcısını benzersiz şekilde tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="f5288-133">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="f5288-134">Çalışma zamanında, aktarım bu öznitelik değerini, daha sonra `IP_MULTICAST_IF` ve yuva seçeneklerini ayarlamak için kullanılan arabirim dizinini aramak için kullanır `IPV6_MULTICAST_IF` .</span><span class="sxs-lookup"><span data-stu-id="f5288-134">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="f5288-135">Varsa, çok noktaya yayın grubuna katılırken de aynı arabirim dizini kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f5288-135">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="f5288-136">`null` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f5288-136">The default value is `null`.</span></span>|  
|<span data-ttu-id="f5288-137">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="f5288-137">socketReceiveBufferSize</span></span>|<span data-ttu-id="f5288-138">Temeldeki WinSock yuvasında Alım arabelleği boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f5288-138">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="f5288-139">Alma kanalının bir kullanıcısı, verileri alırken sistemin nasıl davranacağını denetlemek için bağlama üzerinde bu özniteliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f5288-139">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="f5288-140">Örneğin, bu öznitelik için daha yüksek bir değere sahip gelen WCF iletilerini kullanan bir uygulama, iletilerin, uygulamanın onları işlemesini beklerken WinSock arabelleğine yığmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5288-140">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="f5288-141">Aynı durumda daha düşük bir değer kullanılması, iletilerin bırakılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5288-141">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="f5288-142">Bu öznitelik, temeldeki WinSock `SO_RCVBUF` yuva seçeneğini gösterir. Bu öznitelik değeri en az boyut olmalıdır `maxReceivedMessageSize` .</span><span class="sxs-lookup"><span data-stu-id="f5288-142">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="f5288-143">Değerinden küçük bir değere ayarlanması, `maxReceivedMessageSize` çalışma zamanı özel durumuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="f5288-143">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="f5288-144">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-144">The default value is 65536.</span></span>|  
|<span data-ttu-id="f5288-145">timeToLive</span><span class="sxs-lookup"><span data-stu-id="f5288-145">timeToLive</span></span>|<span data-ttu-id="f5288-146">Çok noktaya yayın paketinin geçebileceğine yönelik ağ segmenti atlamalarının sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f5288-146">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="f5288-147">Bu öznitelik, `IP_MULTICAST_TTL` ve yuva seçenekleriyle ilişkili işlevselliği gösterir `IP_TTL` .</span><span class="sxs-lookup"><span data-stu-id="f5288-147">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="f5288-148">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="f5288-148">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5288-149">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5288-149">Child Elements</span></span>  

 <span data-ttu-id="f5288-150">Yok.</span><span class="sxs-lookup"><span data-stu-id="f5288-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5288-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f5288-151">Parent Elements</span></span>  
  
|<span data-ttu-id="f5288-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="f5288-152">Element</span></span>|<span data-ttu-id="f5288-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5288-153">Description</span></span>|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="f5288-154">Sabit bulma sözleşmesi ve UDP aktarım bağlama içeren standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="f5288-154">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5288-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5288-155">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
