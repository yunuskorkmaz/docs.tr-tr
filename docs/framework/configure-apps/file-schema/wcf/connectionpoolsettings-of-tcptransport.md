---
title: '&lt;tcpTransport&gt; &lt;connectionPoolSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 1fbc4e179fa5f59a903dad51728638a1e182b23e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a><span data-ttu-id="b22d5-102">&lt;tcpTransport&gt; &lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="b22d5-102">&lt;connectionPoolSettings&gt; of &lt;tcpTransport&gt;</span></span>
<span data-ttu-id="b22d5-103">Bir TCP taşıma için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="b22d5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b22d5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b22d5-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="b22d5-105">\<bindings></span></span>  
<span data-ttu-id="b22d5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b22d5-106">\<customBinding></span></span>  
<span data-ttu-id="b22d5-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="b22d5-107">\<binding></span></span>  
<span data-ttu-id="b22d5-108">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="b22d5-108">\<tcpTransport></span></span>  
<span data-ttu-id="b22d5-109">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="b22d5-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22d5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b22d5-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b22d5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b22d5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b22d5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b22d5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b22d5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b22d5-113">Attributes</span></span>  
  
|<span data-ttu-id="b22d5-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b22d5-114">Attribute</span></span>|<span data-ttu-id="b22d5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b22d5-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="b22d5-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="b22d5-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="b22d5-117">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="b22d5-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="b22d5-118">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-118">The default is a "default" string.</span></span> <span data-ttu-id="b22d5-119">Belirli bir istemci bağlantılarında ayrı gruplara ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b22d5-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="b22d5-120">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="b22d5-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="b22d5-122">A <xref:System.TimeSpan> sonra etkin bir bağlantı kapalı süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="b22d5-123">Varsayılan değer 00:05:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="b22d5-124">Bağlantı önbelleğine ve etkin iletim sırasında değil döndürüldü sonra bağlantı kapalı.</span><span class="sxs-lookup"><span data-stu-id="b22d5-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="b22d5-125">Yeni bağlantılar tarafından belirlenen önbellek sınırına kadar her uç noktası için gerekli olarak TCP taşıma tarafından kullanılan bağlantı önbelleği oluşturur `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="b22d5-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="b22d5-126">Bağlantılar hizmeti tarafından başlatılan uzak bir uç nokta için en fazla sayısını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="b22d5-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="b22d5-127">Sınırı aşan bağlantılar, sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="b22d5-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="b22d5-128">`idleTimeout` İçinde bağlantıları kalır sıraya alınmış bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="b22d5-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="b22d5-129">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="b22d5-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="b22d5-130">Bu öznitelik, belirli bir hizmet uç noktası istemciden eşzamanlı etkin bağlantı sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="b22d5-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="b22d5-131">Bu değer daha etkin istemci bağlantıları sağlayarak aşılırsa hizmeti istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="b22d5-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="b22d5-132">Bu durumda, bu değer belirli bir uç beklenen eşzamanlı istemci bağlantılarının üst sınırını aşan ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="b22d5-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b22d5-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b22d5-133">Child Elements</span></span>  
 <span data-ttu-id="b22d5-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="b22d5-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b22d5-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b22d5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b22d5-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="b22d5-136">Element</span></span>|<span data-ttu-id="b22d5-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b22d5-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b22d5-138">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="b22d5-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="b22d5-139">Adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b22d5-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b22d5-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b22d5-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b22d5-141">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="b22d5-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="b22d5-142">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="b22d5-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="b22d5-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b22d5-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b22d5-144">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="b22d5-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b22d5-145">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="b22d5-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b22d5-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b22d5-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
