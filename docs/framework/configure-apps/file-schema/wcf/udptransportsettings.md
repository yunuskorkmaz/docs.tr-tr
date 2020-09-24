---
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: ed59a139ac21e7cfb4400d17f1fc6a0fa3096641
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183682"
---
# \<udpTransportSettings>

<span data-ttu-id="71568-101">Bu yapılandırma öğesi için UDP taşıma ayarlarını gösterir [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="71568-101">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="71568-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="71568-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71568-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="71568-103">Attributes and Elements</span></span>  

 <span data-ttu-id="71568-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71568-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71568-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71568-105">Attributes</span></span>  
  
|<span data-ttu-id="71568-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="71568-106">Attribute</span></span>|<span data-ttu-id="71568-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71568-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71568-108">Duplicatemessagegeçmişini uzunluğu</span><span class="sxs-lookup"><span data-stu-id="71568-108">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="71568-109">Yinelenen iletileri tanımlamak için taşıma tarafından kullanılan en fazla ileti karması sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71568-109">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="71568-110">Yinelenen algılama işlemi, TransportManager düzeyinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="71568-110">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="71568-111">Bu özelliğin 0 olarak ayarlanması yinelenen algılamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="71568-111">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="71568-112">Bu öznitelik, sistem yöneticilerinin veya geliştiricilerin yinelenen ileti algılama algoritmalarını kapatmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="71568-112">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="71568-113">Kendi yinelenen algılama algoritmanızı uygulamak istiyorsanız bu işlem istenebilir.</span><span class="sxs-lookup"><span data-stu-id="71568-113">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="71568-114">Varsayılan değer 4112 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71568-114">The default is 4112.</span></span>|  
|<span data-ttu-id="71568-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="71568-115">maxBufferPoolSize</span></span>|<span data-ttu-id="71568-116">Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71568-116">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="71568-117">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="71568-117">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="71568-118">İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).</span><span class="sxs-lookup"><span data-stu-id="71568-118">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="71568-119">Varsayılan değer 2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71568-119">The default is 2.</span></span>|  
|<span data-ttu-id="71568-120">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="71568-120">maxPendingMessageCount</span></span>|<span data-ttu-id="71568-121">Tek bir kanal örneği için InputQueue öğesinden alınmış ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71568-121">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="71568-122">InputQueue, bekleyen ileti sayısı sınırına ulaşmışsa ileti bırakılır.</span><span class="sxs-lookup"><span data-stu-id="71568-122">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="71568-123">Varsayılan değer 32 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71568-123">The default is 32.</span></span>|  
|<span data-ttu-id="71568-124">Değerini</span><span class="sxs-lookup"><span data-stu-id="71568-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="71568-125">Bağlama tarafından işlenebilecek bir iletinin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71568-125">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="71568-126">Varsayılan değer 65507 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71568-126">The default value is 65507.</span></span>|  
|<span data-ttu-id="71568-127">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="71568-127">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="71568-128">İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).</span><span class="sxs-lookup"><span data-stu-id="71568-128">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="71568-129">İleti bir tek noktaya yayın adresine gönderilirse ve karşılık gelen bir RelatesTo üstbilgisiyle yanıt iletisi alındığında, yeniden iletim erken sonlandırılabilir (yapılandırılan sayıda yeniden gönderilmeden önce).</span><span class="sxs-lookup"><span data-stu-id="71568-129">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="71568-130">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="71568-130">The default value is 1.</span></span>|  
|<span data-ttu-id="71568-131">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="71568-131">multicastInterfaceId</span></span>|<span data-ttu-id="71568-132">Çoklu bilgisayarlı makinelerde çok noktaya yayın trafiği gönderirken ve alırken kullanılması gereken ağ bağdaştırıcısını benzersiz şekilde tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="71568-132">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="71568-133">Çalışma zamanında, aktarım bu öznitelik değerini, daha sonra `IP_MULTICAST_IF` ve yuva seçeneklerini ayarlamak için kullanılan arabirim dizinini aramak için kullanır `IPV6_MULTICAST_IF` .</span><span class="sxs-lookup"><span data-stu-id="71568-133">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="71568-134">Varsa, çok noktaya yayın grubuna katılırken de aynı arabirim dizini kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="71568-134">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="71568-135">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="71568-135">The default value is `null`.</span></span>|  
|<span data-ttu-id="71568-136">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="71568-136">socketReceiveBufferSize</span></span>|<span data-ttu-id="71568-137">Temeldeki WinSock yuvasında Alım arabelleği boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71568-137">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="71568-138">Alma kanalının bir kullanıcısı, verileri alırken sistemin nasıl davranacağını denetlemek için bağlama üzerinde bu özniteliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="71568-138">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="71568-139">Örneğin, bu öznitelik için daha yüksek bir değere sahip gelen WCF iletilerini kullanan bir uygulama, iletilerin, uygulamanın onları işlemesini beklerken WinSock arabelleğine yığmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="71568-139">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="71568-140">Aynı durumda daha düşük bir değer kullanılması, iletilerin bırakılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="71568-140">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="71568-141">Bu öznitelik, temeldeki WinSock `SO_RCVBUF` yuva seçeneğini gösterir. Bu öznitelik değeri en az boyut olmalıdır `maxReceivedMessageSize` .</span><span class="sxs-lookup"><span data-stu-id="71568-141">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="71568-142">Değerinden küçük bir değere ayarlanması, `maxReceivedMessageSize` çalışma zamanı özel durumuna neden olur.</span><span class="sxs-lookup"><span data-stu-id="71568-142">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="71568-143">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="71568-143">The default value is 65536.</span></span>|  
|<span data-ttu-id="71568-144">timeToLive</span><span class="sxs-lookup"><span data-stu-id="71568-144">timeToLive</span></span>|<span data-ttu-id="71568-145">Çok noktaya yayın paketinin geçebileceğine yönelik ağ segmenti atlamalarının sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71568-145">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="71568-146">Bu öznitelik, `IP_MULTICAST_TTL` ve yuva seçenekleriyle ilişkili işlevselliği gösterir `IP_TTL` .</span><span class="sxs-lookup"><span data-stu-id="71568-146">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="71568-147">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="71568-147">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71568-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="71568-148">Child Elements</span></span>  

 <span data-ttu-id="71568-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="71568-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71568-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="71568-150">Parent Elements</span></span>  
  
|<span data-ttu-id="71568-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="71568-151">Element</span></span>|<span data-ttu-id="71568-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71568-152">Description</span></span>|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="71568-153">Sabit bulma sözleşmesi ve UDP aktarım bağlama içeren standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="71568-153">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71568-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71568-154">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
