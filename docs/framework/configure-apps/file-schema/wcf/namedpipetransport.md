---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e5f1d49e0e3bb5f52c5e18577d556d25539434a9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400158"
---
# <a name="namedpipetransport"></a><span data-ttu-id="4a51d-101">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="4a51d-101">\<namedPipeTransport></span></span>
<span data-ttu-id="4a51d-102">Bir kanalın özel bir bağlamaya dahil edildiğinde adlandırılmış kanalları kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="4a51d-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a51d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4a51d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4a51d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4a51d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4a51d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4a51d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4a51d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="4a51d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="4a51d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4a51d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedPipeTransport >**</span><span class="sxs-lookup"><span data-stu-id="4a51d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a51d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a51d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a51d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a51d-110">Attributes and Elements</span></span>  
<span data-ttu-id="4a51d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a51d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a51d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a51d-112">Attributes</span></span>  
<span data-ttu-id="4a51d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a51d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a51d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a51d-114">Child Elements</span></span>  
  
|<span data-ttu-id="4a51d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a51d-115">Element</span></span>|<span data-ttu-id="4a51d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a51d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a51d-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="4a51d-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="4a51d-118">Bir kanalın kesilmeden önce <xref:System.TimeSpan> başlatma durumunda olabilecek en uzun süreyi belirleyen bir değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="4a51d-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="4a51d-119">ConnectionBufferSize</span></span>|<span data-ttu-id="4a51d-120">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="4a51d-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4a51d-121">hostNameComparisonMode</span></span>|<span data-ttu-id="4a51d-122">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="4a51d-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="4a51d-123">manualAddressing</span></span>|<span data-ttu-id="4a51d-124">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="4a51d-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4a51d-125">maxBufferPoolSize</span></span>|<span data-ttu-id="4a51d-126">Taşıma tarafından kullanılan arabellek havuzlarının en büyük boyutunu bayt cinsinden alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="4a51d-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="4a51d-127">maxBufferSize</span></span>|<span data-ttu-id="4a51d-128">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="4a51d-129">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a51d-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="4a51d-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="4a51d-130">maxOutputDelay</span></span>|<span data-ttu-id="4a51d-131">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="4a51d-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="4a51d-132">maxPendingAccepts</span></span>|<span data-ttu-id="4a51d-133">Bir hizmetin hizmete gelen bağlantıları işlemeye yönelik bir dinleyici üzerinde bekleyebilen en fazla kanal sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="4a51d-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4a51d-134">maxPendingConnections</span></span>|<span data-ttu-id="4a51d-135">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="4a51d-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4a51d-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="4a51d-137">Alınabilecek izin verilen en büyük ileti boyutunu bayt cinsinden alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="4a51d-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="4a51d-138">transferMode</span></span>|<span data-ttu-id="4a51d-139">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="4a51d-140">\<\<namedPipeTransport > ConnectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="4a51d-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="4a51d-141">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a51d-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a51d-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a51d-142">Parent Elements</span></span>  
  
|<span data-ttu-id="4a51d-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a51d-143">Element</span></span>|<span data-ttu-id="4a51d-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a51d-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a51d-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4a51d-145">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4a51d-146">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4a51d-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a51d-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a51d-147">Remarks</span></span>  
<span data-ttu-id="4a51d-148">Bu aktarım, "net. pipe:/hostname/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4a51d-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="4a51d-149">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4a51d-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="4a51d-150">`namedPipeTransport` Öğesi, adlandırılmış kanallar aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="4a51d-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="4a51d-151">Bu aktarım, makine içi Windows Communication Foundation (WCF)-WCF iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a51d-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a51d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a51d-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4a51d-153">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="4a51d-153">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="4a51d-154">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="4a51d-154">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4a51d-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4a51d-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4a51d-156">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4a51d-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4a51d-157">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4a51d-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4a51d-158">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4a51d-158">\<customBinding></span></span>](custombinding.md)
