---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: e30fcd5952fadc3b6cf30cb352a3bb51c86cc117
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285937"
---
# <a name="namedpipetransport"></a><span data-ttu-id="34250-101">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="34250-101">\<namedPipeTransport></span></span>
<span data-ttu-id="34250-102">Özel bir bağlamaya dahil olduğunda Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34250-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="34250-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="34250-103">\<system.serviceModel></span></span>  
<span data-ttu-id="34250-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="34250-104">\<bindings></span></span>  
<span data-ttu-id="34250-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="34250-105">\<customBinding></span></span>  
<span data-ttu-id="34250-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34250-106">\<binding></span></span>  
<span data-ttu-id="34250-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="34250-107">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34250-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34250-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34250-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="34250-109">Attributes and Elements</span></span>  
<span data-ttu-id="34250-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="34250-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34250-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="34250-111">Attributes</span></span>  
<span data-ttu-id="34250-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="34250-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34250-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="34250-113">Child Elements</span></span>  
  
|<span data-ttu-id="34250-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="34250-114">Element</span></span>|<span data-ttu-id="34250-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34250-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34250-116">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="34250-116">ChannelInitializationTimeout</span></span>|<span data-ttu-id="34250-117">Alır veya ayarlar bir <xref:System.TimeSpan> kesilmeden önce bir kanal başlatma durumu olabilir en uzun süreyi belirler.</span><span class="sxs-lookup"><span data-stu-id="34250-117">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="34250-118">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="34250-118">ConnectionBufferSize</span></span>|<span data-ttu-id="34250-119">Alır veya ayarlar istemci veya hizmet serileştirilmiş ileti öbeğini iletmek için kullanılan arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="34250-119">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="34250-120">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="34250-120">hostNameComparisonMode</span></span>|<span data-ttu-id="34250-121">Alır veya ayarlar üzerinde URI'yi eşleştirirken hizmete erişmek için ana bilgisayar adının kullanılıp kullanılmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="34250-121">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="34250-122">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="34250-122">manualAddressing</span></span>|<span data-ttu-id="34250-123">Alır veya iletinin el ile adresleme gerekli olup olmadığını gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34250-123">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="34250-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="34250-124">maxBufferPoolSize</span></span>|<span data-ttu-id="34250-125">Alır veya taşıma tarafından kullanılan herhangi bir arabellek havuzu bayt cinsinden en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34250-125">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="34250-126">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="34250-126">maxBufferSize</span></span>|<span data-ttu-id="34250-127">Alır veya kullanılacak arabelleğin en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34250-127">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="34250-128">Akış iletileri için bu değer, arabelleğe alınmış modda okuma ait ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34250-128">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="34250-129">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="34250-129">maxOutputDelay</span></span>|<span data-ttu-id="34250-130">Alır veya gönderilmeden önce ileti veya tam bir ileti bir öbek bellekte arabelleğe alınan kalabileceği süreyi en uzun aralığı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34250-130">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="34250-131">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="34250-131">maxPendingAccepts</span></span>|<span data-ttu-id="34250-132">Alır veya ayarlar hizmetine gelen bağlantıları işlemek için bir Dinleyicide bekleyen bir hizmetin olabilir kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="34250-132">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="34250-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="34250-133">maxPendingConnections</span></span>|<span data-ttu-id="34250-134">Alır veya ayarlar gönderme hizmetinde bekleyen bağlantıları sayısı.</span><span class="sxs-lookup"><span data-stu-id="34250-134">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="34250-135">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="34250-135">maxReceivedMessageSize</span></span>|<span data-ttu-id="34250-136">Alır ve izin verilen maksimum ileti boyutu, alınan bayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34250-136">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="34250-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="34250-137">transferMode</span></span>|<span data-ttu-id="34250-138">Alır veya iletileri ara belleğe veya akışa ile bağlantı sağlamaya yönelik aktarım gösteren bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="34250-138">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="34250-139">\<Tcptransport >, \<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="34250-139">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="34250-140">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34250-140">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34250-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="34250-141">Parent Elements</span></span>  
  
|<span data-ttu-id="34250-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="34250-142">Element</span></span>|<span data-ttu-id="34250-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34250-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34250-144">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="34250-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="34250-145">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34250-145">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34250-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34250-146">Remarks</span></span>  
<span data-ttu-id="34250-147">Bu aktarım "net.pipe://hostname/path" biçiminin bir URI'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="34250-147">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="34250-148">Diğer URI bileşenlerini isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="34250-148">Other URI components are optional.</span></span>  
  
<span data-ttu-id="34250-149">`namedPipeTransport` Öğesi, başlangıç noktası adlandırılmış Aktarım Protokolü uygulayan özel bağlamayı oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="34250-149">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="34250-150">Bu aktarım için makinede Windows Communication Foundation (WCF) - to - WCF iletişim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="34250-150">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34250-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34250-151">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="34250-152">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="34250-152">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="34250-153">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="34250-153">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="34250-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="34250-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="34250-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="34250-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="34250-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="34250-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="34250-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="34250-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
