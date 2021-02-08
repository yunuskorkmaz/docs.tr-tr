---
description: 'Hakkında daha fazla bilgi edinin: <tcpTransport>'
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: b660443ac58e8ed72d70adb5bf9e9e87b060e3af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786622"
---
# \<tcpTransport>

<span data-ttu-id="f3e0b-102">Özel bir bağlama için iletileri aktarmak amacıyla bir kanal tarafından kullanılabilen bir TCP taşıması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-102">Defines a TCP transport that can be used by a channel to transfers messages for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="f3e0b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3e0b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3e0b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3e0b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f3e0b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3e0b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3e0b-106">Attributes</span></span>  
  
|<span data-ttu-id="f3e0b-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f3e0b-107">Attribute</span></span>|<span data-ttu-id="f3e0b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3e0b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3e0b-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="f3e0b-109">channelInitializationTimeout</span></span>|<span data-ttu-id="f3e0b-110">Kabul edilecek bir kanalın başlatılması için zaman sınırını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-110">Gets or sets the time limit for initializing a channel to be accepted.</span></span>  <span data-ttu-id="f3e0b-111">Bir kanalın, saniyeler içinde kesilmeden önce başlatma durumunda olabilecek en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-111">The maximum time a channel can be in the initialization state before being disconnected in seconds.</span></span> <span data-ttu-id="f3e0b-112">Bu kota, bir TCP bağlantısının, .NET Ileti çerçeveleme protokolünü kullanarak kimliğini doğrulamak için zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-112">This quota includes the time a TCP connection can take to authenticate itself using the .NET Message Framing protocol.</span></span> <span data-ttu-id="f3e0b-113">Sunucunun kimlik doğrulamasını gerçekleştirmek için yeterli bilgi olmadan önce bir istemcinin bazı ilk verileri gönderebilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-113">A client needs to send some initial data before the server has enough information to perform authentication.</span></span> <span data-ttu-id="f3e0b-114">Varsayılan değer 30 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-114">The default is 30 seconds.</span></span>|  
|<span data-ttu-id="f3e0b-115">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="f3e0b-115">connectionBufferSize</span></span>|<span data-ttu-id="f3e0b-116">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-116">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="f3e0b-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f3e0b-117">hostNameComparisonMode</span></span>|<span data-ttu-id="f3e0b-118">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-118">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="f3e0b-119">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="f3e0b-119">listenBacklog</span></span>|<span data-ttu-id="f3e0b-120">Bir Web hizmeti için bekleyen sıraya alınmış bağlantı isteği sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-120">The maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="f3e0b-121">`connectionLeaseTimeout`Özniteliği, bir bağlantı özel durumu oluşturmadan önce istemcinin bağlanması için bekleyeceği süreyi sınırlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-121">The `connectionLeaseTimeout` attribute limits the duration the client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="f3e0b-122">Bu, bir Web hizmeti için Beklemede olabilecek en fazla sıraya alınmış bağlantı isteği sayısını denetleyen bir yuva düzeyi özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-122">This is a socket level property which controls the maximum number of queued connection requests that can be pending for a Web service.</span></span> <span data-ttu-id="f3e0b-123">ListenBacklog çok düşük olduğunda, WCF istekleri kabul etmeyi durdurur ve bu nedenle sunucu, mevcut sıraya alınmış bağlantılardan bazılarını yapana kadar yeni bağlantı vermez.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-123">When ListenBacklog is too low, WCF will stop accepting requests and therefore drop new connections until the server acknowledges some of the existing queued connections.</span></span> <span data-ttu-id="f3e0b-124">Varsayılan değer 16 \* işlemci sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-124">The default is 16 \* number of processors.</span></span>|  
|<span data-ttu-id="f3e0b-125">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="f3e0b-125">manualAddressing</span></span>|<span data-ttu-id="f3e0b-126">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-126">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="f3e0b-127">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f3e0b-127">maxBufferPoolSize</span></span>|<span data-ttu-id="f3e0b-128">Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-128">Gets or sets the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="f3e0b-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="f3e0b-129">maxBufferSize</span></span>|<span data-ttu-id="f3e0b-130">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-130">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="f3e0b-131">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-131">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="f3e0b-132">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="f3e0b-132">maxOutputDelay</span></span>|<span data-ttu-id="f3e0b-133">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-133">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="f3e0b-134">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="f3e0b-134">maxPendingAccepts</span></span>|<span data-ttu-id="f3e0b-135">Hizmete gelen bağlantıları işlemek için kullanılabilen bekleyen zaman uyumsuz kabul etme işlemlerinin maksimum sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-135">Gets or sets the maximum number of pending asynchronous accept operations that are available for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="f3e0b-136">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="f3e0b-136">maxPendingConnections</span></span>|<span data-ttu-id="f3e0b-137">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-137">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="f3e0b-138">Değerini</span><span class="sxs-lookup"><span data-stu-id="f3e0b-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="f3e0b-139">Alınabilecek izin verilen en fazla ileti boyutunu alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-139">Gets and sets the maximum allowable message size that can be received.</span></span>|  
|<span data-ttu-id="f3e0b-140">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="f3e0b-140">portSharingEnabled</span></span>|<span data-ttu-id="f3e0b-141">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-141">A Boolean value that specifies if TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="f3e0b-142">Bu ise `false` , her bağlama kendi özel bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-142">If this is `false`, each binding will use its own exclusive port.</span></span> <span data-ttu-id="f3e0b-143">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-143">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f3e0b-144">Bu ayar yalnızca hizmetler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-144">This setting is relevant only to services.</span></span> <span data-ttu-id="f3e0b-145">İstemciler etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-145">Clients are not affected.</span></span><br /><br /> <span data-ttu-id="f3e0b-146">Bu ayarın kullanılması için, başlangıç türünü el Ile veya otomatik olarak değiştirerek Windows Communication Foundation (WCF) TCP bağlantı noktası paylaşım hizmeti 'nin etkinleştirilmesi gerekir</span><span class="sxs-lookup"><span data-stu-id="f3e0b-146">Using this setting requires enabling the Windows Communication Foundation (WCF) TCP Port Sharing Service by changing its Startup Type to Manual or Automatic</span></span>|  
|<span data-ttu-id="f3e0b-147">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="f3e0b-147">teredoEnabled</span></span>|<span data-ttu-id="f3e0b-148">Teredo 'Nun (güvenlik duvarlarının arkasındaki istemcileri adresleme teknolojisinin) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-148">A Boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span> <span data-ttu-id="f3e0b-149">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-149">The default is `false`.</span></span><br /><br /> <span data-ttu-id="f3e0b-150">Bu özellik, temel alınan TCP yuvası için Teredo 'Yu sunar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-150">This property enables Teredo for the underlying TCP socket.</span></span> <span data-ttu-id="f3e0b-151">Daha fazla bilgi için bkz. [Teredo 'Ya genel bakış](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="f3e0b-151">For more information, see [Teredo Overview](/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).</span></span><br /><br /> <span data-ttu-id="f3e0b-152">Bu özellik yalnızca Windows XP SP2 ve Windows Server 2003 ' de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-152">This property is applicable only on Windows XP SP2 and Windows Server 2003.</span></span> <span data-ttu-id="f3e0b-153">Windows Vista Teredo için makine genelinde bir yapılandırma seçeneğine sahiptir, bu nedenle Vista çalıştırılırken bu özellik yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-153">Windows Vista has a machine-wide configuration option for Teredo, so when running Vista, this property is ignored.</span></span> <span data-ttu-id="f3e0b-154">Teredo, istemci ve hizmet makinelerinin hem Microsoft IPv6 yığınının yüklü olmasını hem de Teredo kullanımı için doğru şekilde yapılandırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-154">Teredo requires that the client and service machines both have the Microsoft IPv6 stack installed and correctly configured for Teredo usage.</span></span>|  
|<span data-ttu-id="f3e0b-155">transferMode</span><span class="sxs-lookup"><span data-stu-id="f3e0b-155">transferMode</span></span>|<span data-ttu-id="f3e0b-156">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-156">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|<span data-ttu-id="f3e0b-157">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f3e0b-157">connectionPoolSettings</span></span>|<span data-ttu-id="f3e0b-158">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-158">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3e0b-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3e0b-159">Child Elements</span></span>  

 <span data-ttu-id="f3e0b-160">Yok</span><span class="sxs-lookup"><span data-stu-id="f3e0b-160">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3e0b-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3e0b-161">Parent Elements</span></span>  
  
|<span data-ttu-id="f3e0b-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3e0b-162">Element</span></span>|<span data-ttu-id="f3e0b-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3e0b-163">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f3e0b-164">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-164">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3e0b-165">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3e0b-165">Remarks</span></span>  

 <span data-ttu-id="f3e0b-166">Bu aktarım, "net. TCP:/hostname: Port/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-166">This transport uses URIs of the form "net.tcp://hostname:port/path".</span></span> <span data-ttu-id="f3e0b-167">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-167">Other URI components are optional.</span></span>  
  
 <span data-ttu-id="f3e0b-168">`tcpTransport`Öğesi, TCP aktarma protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-168">The `tcpTransport` element is the starting point for creating a custom binding that implements the TCP transport protocol.</span></span> <span data-ttu-id="f3e0b-169">Bu aktarım, WCF-WCF iletişimi için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-169">This transport is optimized for WCF-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e0b-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3e0b-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f3e0b-171">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="f3e0b-171">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="f3e0b-172">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="f3e0b-172">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="f3e0b-173">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f3e0b-173">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3e0b-174">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f3e0b-174">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f3e0b-175">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f3e0b-175">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
