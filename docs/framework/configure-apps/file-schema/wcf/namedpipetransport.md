---
title: '&lt;Connectionpoolsettings&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: bf9229411143345847247f36de07b5c014d3f259
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149606"
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="82418-102">&lt;Connectionpoolsettings&gt;</span><span class="sxs-lookup"><span data-stu-id="82418-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="82418-103">Özel bir bağlamaya dahil olduğunda Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82418-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="82418-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="82418-104">\<system.serviceModel></span></span>  
<span data-ttu-id="82418-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="82418-105">\<bindings></span></span>  
<span data-ttu-id="82418-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="82418-106">\<customBinding></span></span>  
<span data-ttu-id="82418-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="82418-107">\<binding></span></span>  
<span data-ttu-id="82418-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="82418-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82418-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82418-109">Syntax</span></span>  
  
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
                          maxOutboundConnectionsPerEndpopint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82418-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="82418-110">Attributes and Elements</span></span>  
<span data-ttu-id="82418-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="82418-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82418-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="82418-112">Attributes</span></span>  
<span data-ttu-id="82418-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="82418-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="82418-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="82418-114">Child Elements</span></span>  
  
|<span data-ttu-id="82418-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="82418-115">Element</span></span>|<span data-ttu-id="82418-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82418-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82418-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="82418-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="82418-118">Alır veya ayarlar bir <xref:System.TimeSpan> kesilmeden önce bir kanal başlatma durumu olabilir en uzun süreyi belirler.</span><span class="sxs-lookup"><span data-stu-id="82418-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="82418-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="82418-119">ConnectionBufferSize</span></span>|<span data-ttu-id="82418-120">Alır veya ayarlar istemci veya hizmet serileştirilmiş ileti öbeğini iletmek için kullanılan arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="82418-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="82418-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="82418-121">hostNameComparisonMode</span></span>|<span data-ttu-id="82418-122">Alır veya ayarlar üzerinde URI'yi eşleştirirken hizmete erişmek için ana bilgisayar adının kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="82418-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="82418-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="82418-123">manualAddressing</span></span>|<span data-ttu-id="82418-124">Alır veya iletinin el ile adresleme gerekli olup olmadığını gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82418-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="82418-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="82418-125">maxBufferPoolSize</span></span>|<span data-ttu-id="82418-126">Alır veya taşıma tarafından kullanılan herhangi bir arabellek havuzu bayt cinsinden en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82418-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="82418-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="82418-127">maxBufferSize</span></span>|<span data-ttu-id="82418-128">Alır veya kullanılacak arabelleğin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82418-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="82418-129">Akış iletileri için bu değer, arabelleğe alınmış modda okuma ait ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="82418-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="82418-130">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="82418-130">maxOutputDelay</span></span>|<span data-ttu-id="82418-131">Alır veya gönderilmeden önce ileti veya tam bir ileti bir öbek bellekte arabelleğe alınan kalabileceği süreyi en uzun aralığı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82418-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="82418-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="82418-132">maxPendingAccepts</span></span>|<span data-ttu-id="82418-133">Alır veya ayarlar hizmetine gelen bağlantıları işlemek için bir Dinleyicide bekleyen bir hizmetin olabilir kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="82418-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="82418-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="82418-134">maxPendingConnections</span></span>|<span data-ttu-id="82418-135">Alır veya ayarlar gönderme hizmetinde bekleyen bağlantıları sayısı.</span><span class="sxs-lookup"><span data-stu-id="82418-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="82418-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="82418-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="82418-137">Alır ve izin verilen maksimum ileti boyutu, alınan bayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82418-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="82418-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="82418-138">transferMode</span></span>|<span data-ttu-id="82418-139">Alır veya iletileri ara belleğe veya akışa ile bağlantı sağlamaya yönelik aktarım gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82418-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="82418-140">\<Tcptransport >, \<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="82418-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="82418-141">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="82418-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82418-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="82418-142">Parent Elements</span></span>  
  
|<span data-ttu-id="82418-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="82418-143">Element</span></span>|<span data-ttu-id="82418-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82418-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82418-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="82418-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="82418-146">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="82418-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82418-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82418-147">Remarks</span></span>  
<span data-ttu-id="82418-148">Bu aktarım "net.pipe://hostname/path" biçiminin bir URI'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="82418-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="82418-149">Diğer URI bileşenlerini isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="82418-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="82418-150">`namedPipeTransport` Öğesi, başlangıç noktası adlandırılmış Aktarım Protokolü uygulayan özel bağlamayı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="82418-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="82418-151">Bu aktarım için makinede Windows Communication Foundation (WCF) - to - WCF iletişim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82418-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82418-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82418-152">See Also</span></span>  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
<span data-ttu-id="82418-153">[Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="82418-153">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="82418-154">[Taşıma seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="82418-154">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="82418-155">[Bağlamaları](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="82418-155">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="82418-156">[Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="82418-156">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="82418-157">[Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="82418-157">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="82418-158">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="82418-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
