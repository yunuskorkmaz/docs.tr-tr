---
title: '&lt;Connectionpoolsettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f534bab962e83f76dab7e411cc3c2ca14779df9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lttcptransportgt"></a><span data-ttu-id="15832-102">&lt;Connectionpoolsettings&gt;</span><span class="sxs-lookup"><span data-stu-id="15832-102">&lt;tcpTransport&gt;</span></span>
<span data-ttu-id="15832-103">Özel bağlama için bir kanalı aktarımları iletileri tarafından kullanılabilecek bir TCP taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="15832-103">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
 <span data-ttu-id="15832-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="15832-104">\<system.serviceModel></span></span>  
<span data-ttu-id="15832-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="15832-105">\<bindings></span></span>  
<span data-ttu-id="15832-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="15832-106">\<customBinding></span></span>  
<span data-ttu-id="15832-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="15832-107">\<binding></span></span>  
<span data-ttu-id="15832-108">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="15832-108">\<tcpTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15832-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15832-109">Syntax</span></span>  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15832-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15832-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15832-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15832-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15832-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15832-112">Attributes</span></span>  
  
|<span data-ttu-id="15832-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="15832-113">Attribute</span></span>|<span data-ttu-id="15832-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15832-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15832-115">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="15832-115">channelInitializationTimeout</span></span>|<span data-ttu-id="15832-116">Alır veya kabul edilmesi için bir kanal başlatma zaman sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-116">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="15832-117">En uzun süreyi saniye cinsinden kesilmeden önce bir kanal başlatma durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="15832-117">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="15832-118">Bu kota bir TCP bağlantısı .net kullanarak kendi kimliğini doğrulamak için atabileceğiniz saati içeren ileti çerçeveleme protokolü.</span><span class="sxs-lookup"><span data-stu-id="15832-118">This quota includes the time a TCP connection can take to authenticate itself using the .Net Message Framing protocol.</span></span> <span data-ttu-id="15832-119">Bir istemci, sunucu kimlik doğrulaması gerçekleştirmek için yeterli bilgiye sahip bazı ilk veri göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="15832-119">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="15832-120">Varsayılan değer 30 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="15832-120">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="15832-121">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="15832-121">connectionBufferSize</span></span>|<span data-ttu-id="15832-122">Alır veya ayarlar istemci veya hizmet hattan serileştirilmiş iletide öbeğini iletmek için kullanılan arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="15832-122">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="15832-123">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="15832-123">hostNameComparisonMode</span></span>|<span data-ttu-id="15832-124">Alır veya ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-124">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="15832-125">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="15832-125">listenBacklog</span></span>|<span data-ttu-id="15832-126">Bekleyen sıraya alınan bağlantı isteği sayısının bir Web hizmeti.</span><span class="sxs-lookup"><span data-stu-id="15832-126">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="15832-127">`connectionLeaseTimeout` Öznitelik, istemci bağlantı özel durumuyla atmadan önce bağlanması için bekleyeceği süreyi sınırlar.</span><span class="sxs-lookup"><span data-stu-id="15832-127">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="15832-128">Bu bekleyen sıraya alınan bağlantı isteği sayısının denetleyen bir yuva düzeyi özelliktir Web hizmeti.</span><span class="sxs-lookup"><span data-stu-id="15832-128">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="15832-129">ListenBacklog çok düşük olduğunda, WCF istekleri kabul etmeyi ve sunucu bazı varolan sıraya alınan bağlantıları kabul edene kadar bu nedenle yeni bağlantıları bırakın. 16 varsayılandır * işlemcilerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="15832-129">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections .The default is 16 * number of processors.</span></span>|  
|<span data-ttu-id="15832-130">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="15832-130">manualAddressing</span></span>|<span data-ttu-id="15832-131">Alır veya el ile ileti adresleme gerekip gerekmediğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-131">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="15832-132">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="15832-132">maxBufferPoolSize</span></span>|<span data-ttu-id="15832-133">Alır veya ayarlar aktarım tarafından kullanılan arabellek havuzlarını en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="15832-133">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="15832-134">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="15832-134">maxBufferSize</span></span>|<span data-ttu-id="15832-135">Alır veya ayarlar kullanılacak arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="15832-135">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="15832-136">Akış iletileri için bu değer arabelleğe alınan modunda okuma ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15832-136">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="15832-137">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="15832-137">maxOutputDelay</span></span>|<span data-ttu-id="15832-138">Alır veya üst aralığı gönderilmeden önce bir ileti veya tam bir ileti öbeğini bellekte arabelleğe alınan kalabileceği süreyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-138">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="15832-139">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="15832-139">maxPendingAccepts</span></span>|<span data-ttu-id="15832-140">Alır veya ayarlar en fazla bekleyen zaman uyumsuz işleme gelen bağlantılar hizmeti için kullanılabilen işlemleri kabul edin.</span><span class="sxs-lookup"><span data-stu-id="15832-140">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="15832-141">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="15832-141">maxPendingConnections</span></span>|<span data-ttu-id="15832-142">Alır veya gönderme hizmeti üzerinde bekleyen bağlantı sayısının üst sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-142">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="15832-143">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="15832-143">maxReceivedMessageSize</span></span>|<span data-ttu-id="15832-144">Alır ve alınabilmesi için izin verilen maksimum ileti boyutu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-144">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="15832-145">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="15832-145">portSharingEnabled</span></span>|<span data-ttu-id="15832-146">Bu bağlantı için TCP bağlantı noktası paylaşma etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="15832-146">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="15832-147">Bu ise `false`, her bağlama kendi özel bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="15832-147">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="15832-148">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="15832-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="15832-149">Bu ayar yalnızca Hizmetleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="15832-149">This setting is relevant only to services.</span></span> <span data-ttu-id="15832-150">İstemcileri etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="15832-150">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="15832-151">Bu ayarı kullanarak Windows Communication Foundation (WCF) TCP bağlantı noktası Paylaşımı hizmeti başlangıç türünü el ile veya otomatik olarak değiştirerek etkinleştirme gerektirir</span><span class="sxs-lookup"><span data-stu-id="15832-151">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="15832-152">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="15832-152">teredoEnabled</span></span>|<span data-ttu-id="15832-153">Teredo (güvenlik duvarının arkasındaki adresleme istemciler için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="15832-153">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="15832-154">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="15832-154">The default is `false`.</span></span><br /><br /> <span data-ttu-id="15832-155">Bu özellik, temel alınan TCP yuva için Teredo etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="15832-155">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="15832-156">Daha fazla bilgi için bkz: [Teredo genel bakış](http://go.microsoft.com/fwlink/?LinkId=95339).</span><span class="sxs-lookup"><span data-stu-id="15832-156">For more information, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span><br /><br /> <span data-ttu-id="15832-157">Bu özellik yalnızca geçerli [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] ve [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15832-157">This property is applicable only on [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] and [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)].</span></span> [!INCLUDE[wv](../../../../../includes/wv-md.md)]<span data-ttu-id="15832-158">Teredo için bir makine genelinde yapılandırma seçeneği vardır şekilde Vista çalıştırırken, bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="15832-158"> has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="15832-159">Teredo, hizmet ve istemci makineleri yüklenip Teredo kullanımı için yapılandırıldığını Microsoft IPv6 yığını sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="15832-159">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span> <span data-ttu-id="15832-160">Teredo yapılandırma hakkında daha fazla bilgi için bkz: [Teredo genel bakış](http://go.microsoft.com/fwlink/?LinkId=95339).</span><span class="sxs-lookup"><span data-stu-id="15832-160">For more information about configuring Teredo, see [Teredo Overview](http://go.microsoft.com/fwlink/?LinkId=95339).</span></span> <span data-ttu-id="15832-161">Daha fazla bilgi için bkz: [Windows Server 2003 teknolojisi merkezleri](http://go.microsoft.com/fwlink/?LinkId=49888).</span><span class="sxs-lookup"><span data-stu-id="15832-161">For more information, see [Windows Server 2003 Technology Centers](http://go.microsoft.com/fwlink/?LinkId=49888).</span></span>|  
|<span data-ttu-id="15832-162">transferMode</span><span class="sxs-lookup"><span data-stu-id="15832-162">transferMode</span></span>|<span data-ttu-id="15832-163">Alır veya iletilerin ara belleğe veya ile bağlantı yönelimli aktarma akışı olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15832-163">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="15832-164">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="15832-164">connectionPoolSettings</span></span>|<span data-ttu-id="15832-165">Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="15832-165">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15832-166">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15832-166">Child Elements</span></span>  
 <span data-ttu-id="15832-167">Yok.</span><span class="sxs-lookup"><span data-stu-id="15832-167">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15832-168">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15832-168">Parent Elements</span></span>  
  
|<span data-ttu-id="15832-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="15832-169">Element</span></span>|<span data-ttu-id="15832-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15832-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15832-171">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="15832-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="15832-172">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="15832-172">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15832-173">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15832-173">Remarks</span></span>  
 <span data-ttu-id="15832-174">URI biçiminde bu aktarım kullanır "net.tcp://hostname: bağlantı noktası/yol".</span><span class="sxs-lookup"><span data-stu-id="15832-174">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="15832-175">URI bileşenlerle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="15832-175">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="15832-176">`tcpTransport` Öğesidir başlangıç noktası için bir özel, bağlama oluşturma TCP aktarım protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="15832-176">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="15832-177">Bu aktarım WCF WCF iletişimi için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="15832-177">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15832-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15832-178">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="15832-179">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="15832-179">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="15832-180">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="15832-180">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="15832-181">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="15832-181">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="15832-182">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="15832-182">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="15832-183">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="15832-183">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="15832-184">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="15832-184">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
