---
title: '&lt;tcpTransport&gt; &lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b0bd7303f714847228bcd8bfed7134fe9942c1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="c6432-102">&lt;tcpTransport&gt; &lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="c6432-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="c6432-103">Bir TCP taşıma için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6432-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="c6432-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c6432-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c6432-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c6432-105">\<bindings></span></span>  
<span data-ttu-id="c6432-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6432-106">\<customBinding></span></span>  
<span data-ttu-id="c6432-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c6432-107">\<binding></span></span>  
<span data-ttu-id="c6432-108">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="c6432-108">\<tcpTransport></span></span>  
<span data-ttu-id="c6432-109">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="c6432-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6432-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6432-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6432-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6432-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c6432-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6432-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6432-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6432-113">Attributes</span></span>  
  
|<span data-ttu-id="c6432-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c6432-114">Attribute</span></span>|<span data-ttu-id="c6432-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6432-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="c6432-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="c6432-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="c6432-117">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="c6432-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="c6432-118">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="c6432-118">The default is a "default" string.</span></span> <span data-ttu-id="c6432-119">Belirli bir istemci bağlantılarında ayrı gruplara ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6432-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="c6432-120">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6432-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="c6432-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c6432-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="c6432-122">A <xref:System.TimeSpan> sonra etkin bir bağlantı kapalı süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c6432-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="c6432-123">Varsayılan değer 00:05:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c6432-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="c6432-124">Bağlantı önbelleğine ve etkin iletim sırasında değil döndürüldü sonra bağlantı kapalı.</span><span class="sxs-lookup"><span data-stu-id="c6432-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="c6432-125">Yeni bağlantılar tarafından belirlenen önbellek sınırına kadar her uç noktası için gerekli olarak TCP taşıma tarafından kullanılan bağlantı önbelleği oluşturur`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="c6432-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="c6432-126">Bağlantılar hizmeti tarafından başlatılan uzak bir uç nokta için en fazla sayısını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c6432-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="c6432-127">Sınırı aşan bağlantılar, sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="c6432-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="c6432-128">`idleTimeout` İçinde bağlantıları kalır sıraya alınmış bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="c6432-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="c6432-129">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="c6432-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="c6432-130">Bu öznitelik, belirli bir hizmet uç noktası istemciden eşzamanlı etkin bağlantı sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="c6432-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="c6432-131">Bu değer daha etkin istemci bağlantıları sağlayarak aşılırsa hizmeti istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="c6432-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="c6432-132">Bu durumda, bu değer belirli bir uç beklenen eşzamanlı istemci bağlantılarının üst sınırını aşan ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="c6432-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6432-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6432-133">Child Elements</span></span>  
 <span data-ttu-id="c6432-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6432-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6432-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6432-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c6432-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6432-136">Element</span></span>|<span data-ttu-id="c6432-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6432-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6432-138">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="c6432-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="c6432-139">Adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6432-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6432-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6432-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c6432-141">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="c6432-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="c6432-142">Taşıma seçme</span><span class="sxs-lookup"><span data-stu-id="c6432-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="c6432-143">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="c6432-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c6432-144">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="c6432-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c6432-145">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c6432-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c6432-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c6432-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
