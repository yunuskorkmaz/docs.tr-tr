---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 6d4302e1840f58e2daad855942493cc96b7d5e34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158675"
---
# \<tcpTransport>

<span data-ttu-id="8b495-101">Özel bir bağlama için iletileri aktarmak amacıyla bir kanal tarafından kullanılabilen bir TCP taşıması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-101">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="8b495-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b495-102">Syntax</span></span>  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
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
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b495-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b495-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8b495-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b495-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b495-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8b495-105">Attributes</span></span>  
  
|<span data-ttu-id="8b495-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8b495-106">Attribute</span></span>|<span data-ttu-id="8b495-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b495-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b495-108">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="8b495-108">channelInitializationTimeout</span></span>|<span data-ttu-id="8b495-109">Kabul edilecek bir kanalın başlatılması için zaman sınırını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-109">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="8b495-110">Bir kanalın, saniyeler içinde kesilmeden önce başlatma durumunda olabilecek en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="8b495-110">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="8b495-111">Bu kota, bir TCP bağlantısının, .NET Ileti çerçeveleme protokolünü kullanarak kimliğini doğrulamak için zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="8b495-111">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="8b495-112">Sunucunun kimlik doğrulamasını gerçekleştirmek için yeterli bilgi olmadan önce bir istemcinin bazı ilk verileri gönderebilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b495-112">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="8b495-113">Varsayılan değer 30 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="8b495-113">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="8b495-114">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="8b495-114">connectionBufferSize</span></span>|<span data-ttu-id="8b495-115">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-115">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="8b495-116">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="8b495-116">hostNameComparisonMode</span></span>|<span data-ttu-id="8b495-117">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-117">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="8b495-118">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="8b495-118">listenBacklog</span></span>|<span data-ttu-id="8b495-119">Bir Web hizmeti için bekleyen sıraya alınmış bağlantı isteği sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="8b495-119">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="8b495-120">`connectionLeaseTimeout`Özniteliği, bir bağlantı özel durumu oluşturmadan önce istemcinin bağlanması için bekleyeceği süreyi sınırlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-120">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="8b495-121">Bu, bir Web hizmeti için Beklemede olabilecek en fazla sıraya alınmış bağlantı isteği sayısını denetleyen bir yuva düzeyi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b495-121">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="8b495-122">ListenBacklog çok düşük olduğunda, WCF istekleri kabul etmeyi durdurur ve bu nedenle sunucu, mevcut sıraya alınmış bağlantılardan bazılarını yapana kadar yeni bağlantı vermez.</span><span class="sxs-lookup"><span data-stu-id="8b495-122">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="8b495-123">Varsayılan değer 16 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="8b495-123">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="8b495-124">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="8b495-124">manualAddressing</span></span>|<span data-ttu-id="8b495-125">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-125">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="8b495-126">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="8b495-126">maxBufferPoolSize</span></span>|<span data-ttu-id="8b495-127">Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-127">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="8b495-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="8b495-128">maxBufferSize</span></span>|<span data-ttu-id="8b495-129">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-129">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="8b495-130">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b495-130">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="8b495-131">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="8b495-131">maxOutputDelay</span></span>|<span data-ttu-id="8b495-132">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-132">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="8b495-133">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="8b495-133">maxPendingAccepts</span></span>|<span data-ttu-id="8b495-134">Hizmete gelen bağlantıları işlemek için kullanılabilen bekleyen zaman uyumsuz kabul etme işlemlerinin maksimum sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-134">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="8b495-135">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="8b495-135">maxPendingConnections</span></span>|<span data-ttu-id="8b495-136">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-136">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="8b495-137">Değerini</span><span class="sxs-lookup"><span data-stu-id="8b495-137">maxReceivedMessageSize</span></span>|<span data-ttu-id="8b495-138">Alınabilecek izin verilen en fazla ileti boyutunu alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-138">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="8b495-139">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="8b495-139">portSharingEnabled</span></span>|<span data-ttu-id="8b495-140">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8b495-140">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="8b495-141">Bu ise `false` , her bağlama kendi özel bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b495-141">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="8b495-142">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8b495-142">The default is `false`.</span></span><br /><br /> <span data-ttu-id="8b495-143">Bu ayar yalnızca hizmetler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8b495-143">This setting is relevant only to services.</span></span> <span data-ttu-id="8b495-144">İstemciler etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="8b495-144">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="8b495-145">Bu ayarın kullanılması için, başlangıç türünü el Ile veya otomatik olarak değiştirerek Windows Communication Foundation (WCF) TCP bağlantı noktası paylaşım hizmeti 'nin etkinleştirilmesi gerekir</span><span class="sxs-lookup"><span data-stu-id="8b495-145">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="8b495-146">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="8b495-146">teredoEnabled</span></span>|<span data-ttu-id="8b495-147">Teredo 'Nun (güvenlik duvarlarının arkasındaki istemcileri adresleme teknolojisinin) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8b495-147">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="8b495-148">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8b495-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="8b495-149">Bu özellik, temel alınan TCP yuvası için Teredo 'Yu sunar.</span><span class="sxs-lookup"><span data-stu-id="8b495-149">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="8b495-150">Daha fazla bilgi için bkz. [Teredo 'Ya genel bakış](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="8b495-150">For more information, see [Teredo Overview](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span></span><br /><br /> <span data-ttu-id="8b495-151">Bu özellik yalnızca Windows XP SP2 ve Windows Server 2003 ' de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8b495-151">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="8b495-152">Windows Vista Teredo için makine genelinde bir yapılandırma seçeneğine sahiptir, bu nedenle Vista çalıştırılırken bu özellik yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="8b495-152">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="8b495-153">Teredo, istemci ve hizmet makinelerinin hem Microsoft IPv6 yığınının yüklü olmasını hem de Teredo kullanımı için doğru şekilde yapılandırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b495-153">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span>|  
|<span data-ttu-id="8b495-154">transferMode</span><span class="sxs-lookup"><span data-stu-id="8b495-154">transferMode</span></span>|<span data-ttu-id="8b495-155">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-155">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="8b495-156">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8b495-156">connectionPoolSettings</span></span>|<span data-ttu-id="8b495-157">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b495-157">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b495-158">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b495-158">Child Elements</span></span>  

 <span data-ttu-id="8b495-159">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="8b495-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b495-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8b495-160">Parent Elements</span></span>  
  
|<span data-ttu-id="8b495-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="8b495-161">Element</span></span>|<span data-ttu-id="8b495-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b495-162">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8b495-163">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b495-163">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b495-164">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b495-164">Remarks</span></span>  

 <span data-ttu-id="8b495-165">Bu aktarım, "net. TCP:/hostname: Port/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b495-165">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="8b495-166">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b495-166">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="8b495-167">`tcpTransport`Öğesi, TCP aktarma protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="8b495-167">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="8b495-168">Bu aktarım, WCF-WCF iletişimi için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b495-168">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b495-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b495-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8b495-170">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="8b495-170">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="8b495-171">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="8b495-171">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="8b495-172">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8b495-172">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8b495-173">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8b495-173">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8b495-174">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8b495-174">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
