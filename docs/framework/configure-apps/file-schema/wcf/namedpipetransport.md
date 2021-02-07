---
description: 'Hakkında daha fazla bilgi edinin: <namedPipeTransport>'
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 68714404492be92ce789dbde95a39199f5de16d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684106"
---
# \<namedPipeTransport>

<span data-ttu-id="acb97-102">Bir kanalın özel bir bağlamaya dahil edildiğinde adlandırılmış kanalları kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="acb97-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="acb97-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acb97-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="acb97-104">Attributes and Elements</span></span>  

<span data-ttu-id="acb97-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="acb97-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acb97-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="acb97-106">Attributes</span></span>  

<span data-ttu-id="acb97-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="acb97-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="acb97-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="acb97-108">Child Elements</span></span>  
  
|<span data-ttu-id="acb97-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="acb97-109">Element</span></span>|<span data-ttu-id="acb97-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acb97-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="acb97-111">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="acb97-111">ChannelInitializationTimeout</span></span>|<span data-ttu-id="acb97-112"><xref:System.TimeSpan>Bir kanalın kesilmeden önce başlatma durumunda olabilecek en uzun süreyi belirleyen bir değeri alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-112">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="acb97-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="acb97-113">ConnectionBufferSize</span></span>|<span data-ttu-id="acb97-114">İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-114">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="acb97-115">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="acb97-115">hostNameComparisonMode</span></span>|<span data-ttu-id="acb97-116">URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-116">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="acb97-117">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="acb97-117">manualAddressing</span></span>|<span data-ttu-id="acb97-118">İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-118">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="acb97-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="acb97-119">maxBufferPoolSize</span></span>|<span data-ttu-id="acb97-120">Taşıma tarafından kullanılan arabellek havuzlarının en büyük boyutunu bayt cinsinden alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-120">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="acb97-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="acb97-121">maxBufferSize</span></span>|<span data-ttu-id="acb97-122">Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-122">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="acb97-123">Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="acb97-123">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="acb97-124">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="acb97-124">maxOutputDelay</span></span>|<span data-ttu-id="acb97-125">Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-125">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="acb97-126">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="acb97-126">maxPendingAccepts</span></span>|<span data-ttu-id="acb97-127">Bir hizmetin hizmete gelen bağlantıları işlemeye yönelik bir dinleyici üzerinde bekleyebilen en fazla kanal sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-127">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="acb97-128">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="acb97-128">maxPendingConnections</span></span>|<span data-ttu-id="acb97-129">Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-129">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="acb97-130">Değerini</span><span class="sxs-lookup"><span data-stu-id="acb97-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="acb97-131">Alınabilecek izin verilen en büyük ileti boyutunu bayt cinsinden alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-131">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="acb97-132">transferMode</span><span class="sxs-lookup"><span data-stu-id="acb97-132">transferMode</span></span>|<span data-ttu-id="acb97-133">İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-133">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="acb97-134">\<connectionPoolSettings> durumunu \<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="acb97-134">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="acb97-135">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="acb97-135">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acb97-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="acb97-136">Parent Elements</span></span>  
  
|<span data-ttu-id="acb97-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="acb97-137">Element</span></span>|<span data-ttu-id="acb97-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acb97-138">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="acb97-139">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="acb97-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acb97-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acb97-140">Remarks</span></span>  

<span data-ttu-id="acb97-141">Bu aktarım, "net. pipe:/hostname/path" biçimindeki URI 'Leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="acb97-141">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="acb97-142">Diğer URI bileşenleri isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="acb97-142">Other URI components are optional.</span></span>  
  
<span data-ttu-id="acb97-143">`namedPipeTransport`Öğesi, adlandırılmış kanallar aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="acb97-143">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="acb97-144">Bu aktarım, makine içi Windows Communication Foundation (WCF)-WCF iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="acb97-144">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb97-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb97-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="acb97-146">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="acb97-146">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="acb97-147">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="acb97-147">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="acb97-148">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="acb97-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="acb97-149">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="acb97-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="acb97-150">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="acb97-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
