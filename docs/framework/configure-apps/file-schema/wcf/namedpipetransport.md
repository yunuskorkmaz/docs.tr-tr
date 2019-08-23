---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933202"
---
# <a name="namedpipetransport"></a><span data-ttu-id="bf1a2-101">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-101">\<namedPipeTransport></span></span>
<span data-ttu-id="bf1a2-102">Bir kanalın özel bir bağlamaya dahil edildiğinde adlandırılmış kanalları kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="bf1a2-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bf1a2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bf1a2-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-104">\<bindings></span></span>  
<span data-ttu-id="bf1a2-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-105">\<customBinding></span></span>  
<span data-ttu-id="bf1a2-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-106">\<binding></span></span>  
<span data-ttu-id="bf1a2-107">\<Namepıetransport ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf1a2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf1a2-108">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf1a2-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf1a2-109">Attributes and Elements</span></span>  
<span data-ttu-id="bf1a2-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf1a2-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1a2-111">Attributes</span></span>  
<span data-ttu-id="bf1a2-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf1a2-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf1a2-113">Child Elements</span></span>  
  
|<span data-ttu-id="bf1a2-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf1a2-114">Element</span></span>|<span data-ttu-id="bf1a2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf1a2-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf1a2-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="bf1a2-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="bf1a2-117">Bir kanalın kesilmeden önce <xref:System.TimeSpan> başlatma durumunda olabilecek en uzun süreyi belirleyen bir değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="bf1a2-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="bf1a2-118">ConnectionBufferSize</span></span>|<span data-ttu-id="bf1a2-119">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="bf1a2-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="bf1a2-120">hostNameComparisonMode</span></span>|<span data-ttu-id="bf1a2-121">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="bf1a2-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="bf1a2-122">manualAddressing</span></span>|<span data-ttu-id="bf1a2-123">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="bf1a2-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bf1a2-124">maxBufferPoolSize</span></span>|<span data-ttu-id="bf1a2-125">Taşıma tarafından kullanılan arabellek havuzlarının en büyük boyutunu bayt cinsinden alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="bf1a2-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="bf1a2-126">maxBufferSize</span></span>|<span data-ttu-id="bf1a2-127">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="bf1a2-128">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="bf1a2-129">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="bf1a2-129">maxOutputDelay</span></span>|<span data-ttu-id="bf1a2-130">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="bf1a2-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="bf1a2-131">maxPendingAccepts</span></span>|<span data-ttu-id="bf1a2-132">Bir hizmetin hizmete gelen bağlantıları işlemeye yönelik bir dinleyici üzerinde bekleyebilen en fazla kanal sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="bf1a2-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="bf1a2-133">maxPendingConnections</span></span>|<span data-ttu-id="bf1a2-134">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="bf1a2-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bf1a2-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="bf1a2-136">Alınabilecek izin verilen en büyük ileti boyutunu bayt cinsinden alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="bf1a2-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="bf1a2-137">transferMode</span></span>|<span data-ttu-id="bf1a2-138">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="bf1a2-139">\<\<namedPipeTransport > ConnectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="bf1a2-140">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf1a2-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf1a2-141">Parent Elements</span></span>  
  
|<span data-ttu-id="bf1a2-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf1a2-142">Element</span></span>|<span data-ttu-id="bf1a2-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf1a2-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf1a2-144">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="bf1a2-145">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf1a2-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf1a2-146">Remarks</span></span>  
<span data-ttu-id="bf1a2-147">Bu aktarım, "net. pipe:/hostname/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="bf1a2-148">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="bf1a2-149">`namedPipeTransport` Öğesi, adlandırılmış kanallar aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="bf1a2-150">Bu aktarım, makine içi Windows Communication Foundation (WCF)-WCF iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1a2-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf1a2-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bf1a2-152">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="bf1a2-152">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="bf1a2-153">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="bf1a2-153">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bf1a2-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bf1a2-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bf1a2-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="bf1a2-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bf1a2-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bf1a2-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bf1a2-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bf1a2-157">\<customBinding></span></span>](custombinding.md)
