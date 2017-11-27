---
title: '&lt;Connectionpoolsettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d2d4be08012c1d33341ddd17713903782027c31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="2449d-102">&lt;Connectionpoolsettings&gt;</span><span class="sxs-lookup"><span data-stu-id="2449d-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="2449d-103">İçinde özel bağlama eklendiğinde adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="2449d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2449d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2449d-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2449d-105">\<bindings></span></span>  
<span data-ttu-id="2449d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2449d-106">\<customBinding></span></span>  
<span data-ttu-id="2449d-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2449d-107">\<binding></span></span>  
<span data-ttu-id="2449d-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="2449d-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2449d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2449d-109">Syntax</span></span>  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2449d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2449d-110">Attributes and Elements</span></span>  
<span data-ttu-id="2449d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2449d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2449d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2449d-112">Attributes</span></span>  
<span data-ttu-id="2449d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2449d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2449d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2449d-114">Child Elements</span></span>  
  
|<span data-ttu-id="2449d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2449d-115">Element</span></span>|<span data-ttu-id="2449d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2449d-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2449d-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="2449d-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="2449d-118">Alır veya ayarlar bir <xref:System.TimeSpan> kesilmeden önce bir kanal başlatma durumu olabilir en uzun süreyi belirler.</span><span class="sxs-lookup"><span data-stu-id="2449d-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="2449d-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="2449d-119">ConnectionBufferSize</span></span>|<span data-ttu-id="2449d-120">Alır veya ayarlar istemci veya hizmet hattan serileştirilmiş iletide öbeğini iletmek için kullanılan arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="2449d-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="2449d-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="2449d-121">hostNameComparisonMode</span></span>|<span data-ttu-id="2449d-122">Alır veya ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="2449d-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="2449d-123">manualAddressing</span></span>|<span data-ttu-id="2449d-124">Alır veya el ile ileti adresleme gerekip gerekmediğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="2449d-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2449d-125">maxBufferPoolSize</span></span>|<span data-ttu-id="2449d-126">Alır veya taşıma tarafından kullanılan tüm arabellek havuzu bayt cinsinden en büyük boyutu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="2449d-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="2449d-127">maxBufferSize</span></span>|<span data-ttu-id="2449d-128">Alır veya ayarlar kullanılacak arabelleğin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="2449d-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="2449d-129">Akış iletileri için bu değer arabelleğe alınan modunda okuma ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2449d-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="2449d-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="2449d-130">maxOutputDelay</span></span>|<span data-ttu-id="2449d-131">Alır veya üst aralığı gönderilmeden önce bir ileti veya tam bir ileti öbeğini bellekte arabelleğe alınan kalabileceği süreyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="2449d-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="2449d-132">maxPendingAccepts</span></span>|<span data-ttu-id="2449d-133">Alır veya bir hizmetin hizmetine gelen bağlantıları işlemek için bir dinleyici bekliyor olabilir kanalları sayısının üst sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="2449d-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="2449d-134">maxPendingConnections</span></span>|<span data-ttu-id="2449d-135">Alır veya gönderme hizmeti üzerinde bekleyen bağlantı sayısının üst sınırını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="2449d-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2449d-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="2449d-137">Alır ve izin verilen maksimum ileti boyutu alınabileceğini bayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="2449d-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="2449d-138">transferMode</span></span>|<span data-ttu-id="2449d-139">Alır veya iletilerin ara belleğe veya ile bağlantı yönelimli aktarma akışı olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="2449d-140">\<Tcptransport >, \<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="2449d-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="2449d-141">Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2449d-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2449d-142">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2449d-142">Parent Elements</span></span>  
  
|<span data-ttu-id="2449d-143">Öğe</span><span class="sxs-lookup"><span data-stu-id="2449d-143">Element</span></span>|<span data-ttu-id="2449d-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2449d-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2449d-145">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2449d-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2449d-146">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2449d-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2449d-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2449d-147">Remarks</span></span>  
<span data-ttu-id="2449d-148">Bu aktarım "net.pipe://hostname/path" biçiminde URI'ler kullanır.</span><span class="sxs-lookup"><span data-stu-id="2449d-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="2449d-149">URI bileşenlerle isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2449d-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="2449d-150">`namedPipeTransport` Öğesidir başlangıç noktası için bir özel, bağlama oluşturma adlandırılmış kanallar aktarım protokolünü uygular.</span><span class="sxs-lookup"><span data-stu-id="2449d-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="2449d-151">Bu aktarım için makine üzerindeki Windows Communication Foundation (WCF) - to - WCF iletişim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2449d-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2449d-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2449d-152">See Also</span></span>  
<span data-ttu-id="2449d-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span><span class="sxs-lookup"><span data-stu-id="2449d-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span></span>   
<span data-ttu-id="2449d-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="2449d-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span></span>   
<span data-ttu-id="2449d-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="2449d-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span></span>   
<span data-ttu-id="2449d-156"><xref:System.ServiceModel.Channels.CustomBinding></span><span class="sxs-lookup"><span data-stu-id="2449d-156"><xref:System.ServiceModel.Channels.CustomBinding></span></span>   
<span data-ttu-id="2449d-157">[Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="2449d-157">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="2449d-158">[Taşıma seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="2449d-158">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="2449d-159">[Bağlamaları](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="2449d-159">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="2449d-160">[Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="2449d-160">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="2449d-161">[Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="2449d-161">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="2449d-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2449d-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
