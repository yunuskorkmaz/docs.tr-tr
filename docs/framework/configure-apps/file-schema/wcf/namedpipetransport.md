---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: cdb2863ff376a92f7c4b679f4812b895ac3f2234
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518845"
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="3aa4d-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="3aa4d-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="3aa4d-103">Özel bir bağlamaya dahil olduğunda Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="3aa4d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3aa4d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3aa4d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3aa4d-105">\<bindings></span></span>  
<span data-ttu-id="3aa4d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3aa4d-106">\<customBinding></span></span>  
<span data-ttu-id="3aa4d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3aa4d-107">\<binding></span></span>  
<span data-ttu-id="3aa4d-108">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="3aa4d-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa4d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aa4d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3aa4d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aa4d-110">Attributes and Elements</span></span>  
<span data-ttu-id="3aa4d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3aa4d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3aa4d-112">Attributes</span></span>  
<span data-ttu-id="3aa4d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3aa4d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aa4d-114">Child Elements</span></span>  
  
|<span data-ttu-id="3aa4d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="3aa4d-115">Element</span></span>|<span data-ttu-id="3aa4d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aa4d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3aa4d-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="3aa4d-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="3aa4d-118">Alır veya ayarlar bir <xref:System.TimeSpan> kesilmeden önce bir kanal başlatma durumu olabilir en uzun süreyi belirler.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="3aa4d-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="3aa4d-119">ConnectionBufferSize</span></span>|<span data-ttu-id="3aa4d-120">Alır veya ayarlar istemci veya hizmet serileştirilmiş ileti öbeğini iletmek için kullanılan arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="3aa4d-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="3aa4d-121">hostNameComparisonMode</span></span>|<span data-ttu-id="3aa4d-122">Alır veya ayarlar üzerinde URI'yi eşleştirirken hizmete erişmek için ana bilgisayar adının kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="3aa4d-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="3aa4d-123">manualAddressing</span></span>|<span data-ttu-id="3aa4d-124">Alır veya iletinin el ile adresleme gerekli olup olmadığını gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="3aa4d-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="3aa4d-125">maxBufferPoolSize</span></span>|<span data-ttu-id="3aa4d-126">Alır veya taşıma tarafından kullanılan herhangi bir arabellek havuzu bayt cinsinden en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="3aa4d-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="3aa4d-127">maxBufferSize</span></span>|<span data-ttu-id="3aa4d-128">Alır veya kullanılacak arabelleğin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="3aa4d-129">Akış iletileri için bu değer, arabelleğe alınmış modda okuma ait ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="3aa4d-130">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="3aa4d-130">maxOutputDelay</span></span>|<span data-ttu-id="3aa4d-131">Alır veya gönderilmeden önce ileti veya tam bir ileti bir öbek bellekte arabelleğe alınan kalabileceği süreyi en uzun aralığı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="3aa4d-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="3aa4d-132">maxPendingAccepts</span></span>|<span data-ttu-id="3aa4d-133">Alır veya ayarlar hizmetine gelen bağlantıları işlemek için bir Dinleyicide bekleyen bir hizmetin olabilir kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="3aa4d-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="3aa4d-134">maxPendingConnections</span></span>|<span data-ttu-id="3aa4d-135">Alır veya ayarlar gönderme hizmetinde bekleyen bağlantıları sayısı.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="3aa4d-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="3aa4d-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="3aa4d-137">Alır ve izin verilen maksimum ileti boyutu, alınan bayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="3aa4d-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="3aa4d-138">transferMode</span></span>|<span data-ttu-id="3aa4d-139">Alır veya iletileri ara belleğe veya akışa ile bağlantı sağlamaya yönelik aktarım gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="3aa4d-140">\<Tcptransport >, \<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="3aa4d-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="3aa4d-141">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3aa4d-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aa4d-142">Parent Elements</span></span>  
  
|<span data-ttu-id="3aa4d-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="3aa4d-143">Element</span></span>|<span data-ttu-id="3aa4d-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aa4d-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aa4d-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3aa4d-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3aa4d-146">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3aa4d-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aa4d-147">Remarks</span></span>  
<span data-ttu-id="3aa4d-148">Bu aktarım "net.pipe://hostname/path" biçiminin bir URI'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="3aa4d-149">Diğer URI bileşenlerini isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="3aa4d-150">`namedPipeTransport` Öğesi, başlangıç noktası adlandırılmış Aktarım Protokolü uygulayan özel bağlamayı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="3aa4d-151">Bu aktarım için makinede Windows Communication Foundation (WCF) - to - WCF iletişim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa4d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aa4d-152">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3aa4d-153">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="3aa4d-153">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="3aa4d-154">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="3aa4d-154">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3aa4d-155">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3aa4d-155">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3aa4d-156">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3aa4d-156">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3aa4d-157">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3aa4d-157">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3aa4d-158">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3aa4d-158">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
