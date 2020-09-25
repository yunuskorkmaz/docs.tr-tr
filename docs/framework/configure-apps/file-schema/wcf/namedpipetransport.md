---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 4582066098feaf50b33b083de56bcb8c3e04df0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204625"
---
# \<namedPipeTransport>

<span data-ttu-id="4102d-101">Bir kanalın özel bir bağlamaya dahil edildiğinde adlandırılmış kanalları kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="4102d-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="4102d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4102d-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4102d-103">Attributes and Elements</span></span>  

<span data-ttu-id="4102d-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4102d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4102d-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4102d-105">Attributes</span></span>  

<span data-ttu-id="4102d-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="4102d-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4102d-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4102d-107">Child Elements</span></span>  
  
|<span data-ttu-id="4102d-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="4102d-108">Element</span></span>|<span data-ttu-id="4102d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4102d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4102d-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="4102d-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="4102d-111"><xref:System.TimeSpan>Bir kanalın kesilmeden önce başlatma durumunda olabilecek en uzun süreyi belirleyen bir değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="4102d-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="4102d-112">ConnectionBufferSize</span></span>|<span data-ttu-id="4102d-113">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="4102d-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4102d-114">hostNameComparisonMode</span></span>|<span data-ttu-id="4102d-115">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="4102d-116">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="4102d-116">manualAddressing</span></span>|<span data-ttu-id="4102d-117">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="4102d-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4102d-118">maxBufferPoolSize</span></span>|<span data-ttu-id="4102d-119">Taşıma tarafından kullanılan arabellek havuzlarının en büyük boyutunu bayt cinsinden alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="4102d-120">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="4102d-120">maxBufferSize</span></span>|<span data-ttu-id="4102d-121">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="4102d-122">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4102d-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="4102d-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="4102d-123">maxOutputDelay</span></span>|<span data-ttu-id="4102d-124">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="4102d-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="4102d-125">maxPendingAccepts</span></span>|<span data-ttu-id="4102d-126">Bir hizmetin hizmete gelen bağlantıları işlemeye yönelik bir dinleyici üzerinde bekleyebilen en fazla kanal sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="4102d-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4102d-127">maxPendingConnections</span></span>|<span data-ttu-id="4102d-128">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="4102d-129">Değerini</span><span class="sxs-lookup"><span data-stu-id="4102d-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="4102d-130">Alınabilecek izin verilen en büyük ileti boyutunu bayt cinsinden alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="4102d-131">transferMode</span><span class="sxs-lookup"><span data-stu-id="4102d-131">transferMode</span></span>|<span data-ttu-id="4102d-132">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="4102d-133">\<connectionPoolSettings> durumunu \<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="4102d-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="4102d-134">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4102d-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4102d-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4102d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4102d-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="4102d-136">Element</span></span>|<span data-ttu-id="4102d-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4102d-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4102d-138">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4102d-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4102d-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4102d-139">Remarks</span></span>  

<span data-ttu-id="4102d-140">Bu aktarım, "net. pipe:/hostname/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4102d-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="4102d-141">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4102d-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="4102d-142">`namedPipeTransport`Öğesi, adlandırılmış kanallar aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="4102d-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="4102d-143">Bu aktarım, makine içi Windows Communication Foundation (WCF)-WCF iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4102d-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4102d-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4102d-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4102d-145">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="4102d-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="4102d-146">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="4102d-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4102d-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4102d-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4102d-148">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4102d-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4102d-149">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4102d-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
