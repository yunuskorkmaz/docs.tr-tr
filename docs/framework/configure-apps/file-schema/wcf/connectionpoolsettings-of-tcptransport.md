---
title: <connectionPoolSettings> / <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673244"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="3254f-102">\<Namedpipetransport >, \<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="3254f-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="3254f-103">TCP aktarımı için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3254f-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="3254f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3254f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3254f-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3254f-105">\<bindings></span></span>  
<span data-ttu-id="3254f-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3254f-106">\<customBinding></span></span>  
<span data-ttu-id="3254f-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3254f-107">\<binding></span></span>  
<span data-ttu-id="3254f-108">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="3254f-108">\<tcpTransport></span></span>  
<span data-ttu-id="3254f-109">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="3254f-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3254f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3254f-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3254f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3254f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3254f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3254f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3254f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3254f-113">Attributes</span></span>  
  
|<span data-ttu-id="3254f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3254f-114">Attribute</span></span>|<span data-ttu-id="3254f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3254f-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="3254f-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="3254f-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="3254f-117">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="3254f-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="3254f-118">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="3254f-118">The default is a "default" string.</span></span> <span data-ttu-id="3254f-119">Belirli bir istemci bağlantılarını ayrı gruplar halinde ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3254f-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="3254f-120">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3254f-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="3254f-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3254f-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="3254f-122">A <xref:System.TimeSpan> etkin bir bağlantı kapalı geçecek süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3254f-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="3254f-123">Varsayılan değer 00:05:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3254f-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="3254f-124">Bağlantı önbelleğe ve etkin aktarım sırasında değil döndürüldü sonra bir bağlantı kapalı.</span><span class="sxs-lookup"><span data-stu-id="3254f-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="3254f-125">Yeni bağlantı kümesi tarafından önbellek sınıra kadar her uç nokta için gereken TCP taşıma tarafından kullanılan bağlantı önbelleği oluşturur `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="3254f-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="3254f-126">En fazla hizmet tarafından başlatılan bir uzak uç noktasına bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3254f-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="3254f-127">Sınırı aşan bağlantılar, sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="3254f-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="3254f-128">`idleTimeout` Hangi bağlantıları kalır sıraya alınan bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="3254f-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="3254f-129">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="3254f-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="3254f-130">Bu öznitelik istemcisi eşzamanlı etkin bağlantılar için belirli hizmet uç noktası sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="3254f-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="3254f-131">Bu değer daha etkin istemci bağlantıları sağlayarak aşılıyorsa, hizmetin istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="3254f-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="3254f-132">Bu durumda, bu değeri belirli bir uç nokta için beklenen eşzamanlı istemci bağlantısına maksimum sayısını aşmaya ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="3254f-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3254f-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3254f-133">Child Elements</span></span>  
 <span data-ttu-id="3254f-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="3254f-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3254f-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3254f-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3254f-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3254f-136">Element</span></span>|<span data-ttu-id="3254f-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3254f-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3254f-138">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="3254f-138">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="3254f-139">Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3254f-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3254f-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3254f-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3254f-141">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="3254f-141">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="3254f-142">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="3254f-142">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3254f-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3254f-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3254f-144">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3254f-144">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3254f-145">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3254f-145">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3254f-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3254f-146">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
