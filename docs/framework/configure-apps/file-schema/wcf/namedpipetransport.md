---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736590"
---
# \<namedPipeTransport>
<span data-ttu-id="aabbf-101">Bir kanalın özel bir bağlamaya dahil edildiğinde adlandırılmış kanalları kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="aabbf-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aabbf-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aabbf-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aabbf-103">Attributes and Elements</span></span>  
<span data-ttu-id="aabbf-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aabbf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aabbf-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aabbf-105">Attributes</span></span>  
<span data-ttu-id="aabbf-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="aabbf-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aabbf-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aabbf-107">Child Elements</span></span>  
  
|<span data-ttu-id="aabbf-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="aabbf-108">Element</span></span>|<span data-ttu-id="aabbf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aabbf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aabbf-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="aabbf-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="aabbf-111"><xref:System.TimeSpan>Bir kanalın kesilmeden önce başlatma durumunda olabilecek en uzun süreyi belirleyen bir değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="aabbf-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="aabbf-112">ConnectionBufferSize</span></span>|<span data-ttu-id="aabbf-113">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="aabbf-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="aabbf-114">hostNameComparisonMode</span></span>|<span data-ttu-id="aabbf-115">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="aabbf-116">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="aabbf-116">manualAddressing</span></span>|<span data-ttu-id="aabbf-117">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="aabbf-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="aabbf-118">maxBufferPoolSize</span></span>|<span data-ttu-id="aabbf-119">Taşıma tarafından kullanılan arabellek havuzlarının en büyük boyutunu bayt cinsinden alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="aabbf-120">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="aabbf-120">maxBufferSize</span></span>|<span data-ttu-id="aabbf-121">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="aabbf-122">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aabbf-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="aabbf-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="aabbf-123">maxOutputDelay</span></span>|<span data-ttu-id="aabbf-124">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="aabbf-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="aabbf-125">maxPendingAccepts</span></span>|<span data-ttu-id="aabbf-126">Bir hizmetin hizmete gelen bağlantıları işlemeye yönelik bir dinleyici üzerinde bekleyebilen en fazla kanal sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="aabbf-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="aabbf-127">maxPendingConnections</span></span>|<span data-ttu-id="aabbf-128">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="aabbf-129">Değerini</span><span class="sxs-lookup"><span data-stu-id="aabbf-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="aabbf-130">Alınabilecek izin verilen en büyük ileti boyutunu bayt cinsinden alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="aabbf-131">transferMode</span><span class="sxs-lookup"><span data-stu-id="aabbf-131">transferMode</span></span>|<span data-ttu-id="aabbf-132">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="aabbf-133">\<connectionPoolSettings>durumunu\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="aabbf-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="aabbf-134">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="aabbf-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aabbf-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aabbf-135">Parent Elements</span></span>  
  
|<span data-ttu-id="aabbf-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="aabbf-136">Element</span></span>|<span data-ttu-id="aabbf-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aabbf-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="aabbf-138">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aabbf-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aabbf-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aabbf-139">Remarks</span></span>  
<span data-ttu-id="aabbf-140">Bu aktarım, "net. pipe:/hostname/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="aabbf-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="aabbf-141">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aabbf-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="aabbf-142">`namedPipeTransport`Öğesi, adlandırılmış kanallar aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="aabbf-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="aabbf-143">Bu aktarım, makine içi Windows Communication Foundation (WCF)-WCF iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aabbf-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aabbf-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aabbf-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="aabbf-145">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="aabbf-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="aabbf-146">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="aabbf-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="aabbf-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aabbf-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aabbf-148">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="aabbf-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="aabbf-149">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aabbf-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
