---
title: "&lt;udpAnnouncementEndpoint&gt; için &lt;udpTransportSettings&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a5de8d55d34c2db0d0b1efd5a05024f1dbc4f42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudptransportsettingsgt-of-ltudpannouncementendpointgt"></a><span data-ttu-id="e9ac3-102">&lt;udpAnnouncementEndpoint&gt; için &lt;udpTransportSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="e9ac3-102">&lt;udpTransportSettings&gt; of &lt;udpAnnouncementEndpoint&gt;</span></span>
<span data-ttu-id="e9ac3-103">Bu yapılandırma öğesi için UDP taşıma ayarları gösteren [ \<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md).</span><span class="sxs-lookup"><span data-stu-id="e9ac3-103">This configuration element exposes UDP transport settings for [\<udpAnnoucementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md).</span></span>  
  
<span data-ttu-id="e9ac3-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e9ac3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9ac3-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e9ac3-105">\<standardEndpoints></span></span>  
<span data-ttu-id="e9ac3-106">\<Udptransportsettings ></span><span class="sxs-lookup"><span data-stu-id="e9ac3-106">\<udpAnnouncementEndpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ac3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9ac3-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpAnnouncementEndpoint>
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
    </udpAnnouncementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9ac3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9ac3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e9ac3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9ac3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e9ac3-110">Attributes</span></span>  
  
|<span data-ttu-id="e9ac3-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e9ac3-111">Attribute</span></span>|<span data-ttu-id="e9ac3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9ac3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9ac3-113">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="e9ac3-113">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="e9ac3-114">Yinelenen iletileri tanımlamak için aktarım tarafından kullanılan ileti karmaları en fazla sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-114">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="e9ac3-115">Yinelenen algılama TransportManager düzeyinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-115">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="e9ac3-116">Bu özellik 0 olarak ayarlanması yinelenen algılama devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-116">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="e9ac3-117">Bu öznitelik, sistem yöneticileri veya yinelenen ileti algılama algoritmalarını devre dışı bırakma geliştiriciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-117">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="e9ac3-118">Bu, kendi yinelenen algılama algoritması uygulamak istiyorsanız tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-118">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="e9ac3-119">4112 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-119">The default is 4112.</span></span>|  
|<span data-ttu-id="e9ac3-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e9ac3-120">maxBufferPoolSize</span></span>|<span data-ttu-id="e9ac3-121">Arabellek havuzlarını aktarım tarafından kullanılan en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-121">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="e9ac3-122">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="e9ac3-122">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="e9ac3-123">En fazla kaç kez ileti (ilk gönderme ek olarak) iletilmelidir belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-123">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="e9ac3-124">Varsayılan değer 2'dir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-124">The default is 2.</span></span>|  
|<span data-ttu-id="e9ac3-125">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="e9ac3-125">maxPendingMessageCount</span></span>|<span data-ttu-id="e9ac3-126">Aldı, ancak henüz bir tek kanal örneğinin InputQueue kaldırıldı iletilerinin sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-126">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="e9ac3-127">InputQueue bekleyen ileti sayısı sınırına erişti, ileti bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-127">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="e9ac3-128">Varsayılan değer 32'dir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-128">The default is 32.</span></span>|  
|<span data-ttu-id="e9ac3-129">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e9ac3-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="e9ac3-130">Bağlama tarafından işlenebilen bir ileti boyutu üst sınırı belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-130">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="e9ac3-131">65507 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-131">The default value is 65507.</span></span>|  
|<span data-ttu-id="e9ac3-132">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="e9ac3-132">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="e9ac3-133">En fazla kaç kez ileti (ilk gönderme ek olarak) iletilmelidir belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-133">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="e9ac3-134">İleti bir tek noktaya yayın adresine gönderilir ve karşılık gelen bir RelatesTo üstbilgiyle bir yanıt iletisi aldı, aktarım erken (yapılandırılmış kaç kez yeniden göndermeden önce) sonlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-134">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="e9ac3-135">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-135">The default value is 1.</span></span>|  
|<span data-ttu-id="e9ac3-136">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="e9ac3-136">multicastInterfaceId</span></span>|<span data-ttu-id="e9ac3-137">Çok noktaya yayın trafiğine çok ana bilgisayarlı makinelerdeki gönderilip alınırken kullanılması gereken ağ bağdaştırıcısı benzersiz olarak tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-137">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="e9ac3-138">Çalışma zamanında, daha sonra ayarlamak için kullanılan arabirim dizinini aramak için bu öznitelik değeri aktarımını kullanacak `IP_MULTICAST_IF` ve `IPV6_MULTICAST_IF` yuva seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-138">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="e9ac3-139">Aynı arabirim dizinini çok noktaya yayın grubu eklerken varsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-139">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="e9ac3-140">Varsayılan değer `null` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-140">The default value is `null`.</span></span>|  
|<span data-ttu-id="e9ac3-141">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="e9ac3-141">socketReceiveBufferSize</span></span>|<span data-ttu-id="e9ac3-142">Temel alınan WinSock yuvası üzerinde alış arabelleği boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-142">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="e9ac3-143">Bir kullanıcı bir alıcı kanalının bu öznitelik veri aldığında sistem nasıl davranacağını denetlemek için bağlamada kullanın.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-143">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="e9ac3-144">Örneğin, gelen WCF iletileri maksimum eşik kullanan bir uygulama göz önüne alındığında, bu öznitelik için daha yüksek bir değer kullanarak uygulamayı bunları işleyebilmesi için beklenirken WinSock arabellekte yığın iletileri olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-144">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="e9ac3-145">Daha düşük bir değere aynı durumda kullanarak kesiliyor iletilerinde neden olur. Bu öznitelik temel WinSock gösterir `SO_RCVBUF` yuva seçeneği. Bu öznitelik değeri boyutu en az olmalıdır `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-145">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="e9ac3-146">Bir değere küçüktür ayarlamak `maxReceivedMessageSize` çalışma zamanı özel durumuna neden.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-146">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="e9ac3-147">Varsayılan değer 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-147">The default value is 65536.</span></span>|  
|<span data-ttu-id="e9ac3-148">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="e9ac3-148">timeToLive</span></span>|<span data-ttu-id="e9ac3-149">Çok noktaya yayın paketinin erişebilen ağ kesimi durak sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-149">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="e9ac3-150">Bu öznitelik ile ilişkili işlevselliği kullanıma sunan `IP_MULTICAST_TTL` ve `IP_TTL` yuva seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-150">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="e9ac3-151">Varsayılan değer 1’dir.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-151">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9ac3-152">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9ac3-152">Child Elements</span></span>  
 <span data-ttu-id="e9ac3-153">Yok.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9ac3-154">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e9ac3-154">Parent Elements</span></span>  
  
|<span data-ttu-id="e9ac3-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="e9ac3-155">Element</span></span>|<span data-ttu-id="e9ac3-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9ac3-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9ac3-157">\<udpAnnoucementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="e9ac3-157">\<udpAnnoucementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|<span data-ttu-id="e9ac3-158">Sözleşme ve UDP bağlama aktarım duyuru sabit sahip standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-158">A standard endpoint that has fixed announcement contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9ac3-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ac3-159">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
