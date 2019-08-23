---
title: <connectionPoolSettings> / <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 787b50296b7ed4f6fdceef244a99dffffae63c61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919394"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="3ba22-102">\<\<TcpTransport > ConnectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="3ba22-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="3ba22-103">TCP aktarımı için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
 <span data-ttu-id="3ba22-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ba22-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3ba22-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3ba22-105">\<bindings></span></span>  
<span data-ttu-id="3ba22-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3ba22-106">\<customBinding></span></span>  
<span data-ttu-id="3ba22-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="3ba22-107">\<binding></span></span>  
<span data-ttu-id="3ba22-108">\<tcpTransport ></span><span class="sxs-lookup"><span data-stu-id="3ba22-108">\<tcpTransport></span></span>  
<span data-ttu-id="3ba22-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="3ba22-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba22-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ba22-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ba22-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ba22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3ba22-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ba22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ba22-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ba22-113">Attributes</span></span>  
  
|<span data-ttu-id="3ba22-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3ba22-114">Attribute</span></span>|<span data-ttu-id="3ba22-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ba22-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="3ba22-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="3ba22-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="3ba22-117">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="3ba22-118">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-118">The default is a "default" string.</span></span> <span data-ttu-id="3ba22-119">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ba22-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="3ba22-120">Bağlantı kesilmeden <xref:System.TimeSpan> önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="3ba22-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="3ba22-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-121">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="3ba22-122">Etkin <xref:System.TimeSpan> bir bağlantının kapatıldığı zamanı belirten bir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-122">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="3ba22-123">Varsayılan değer 00:05:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-123">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="3ba22-124">Bağlantı, etkin iletim sırasında değil bağlantı önbelleğine döndürülmeden sonra kapatılır.</span><span class="sxs-lookup"><span data-stu-id="3ba22-124">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="3ba22-125">TCP aktarımı tarafından kullanılan bağlantı önbelleği, her bir uç nokta için gerektiği şekilde, tarafından ayarlanan önbellek sınırına kadar yeni bağlantılar oluşturur.`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="3ba22-125">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="3ba22-126">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="3ba22-126">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="3ba22-127">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="3ba22-127">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="3ba22-128">Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.`idleTimeout`</span><span class="sxs-lookup"><span data-stu-id="3ba22-128">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="3ba22-129">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="3ba22-129">The default is 10.</span></span><br /><br /> <span data-ttu-id="3ba22-130">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="3ba22-130">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="3ba22-131">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-131">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="3ba22-132">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ba22-132">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ba22-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ba22-133">Child Elements</span></span>  
 <span data-ttu-id="3ba22-134">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ba22-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ba22-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ba22-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3ba22-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ba22-136">Element</span></span>|<span data-ttu-id="3ba22-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ba22-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ba22-138">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="3ba22-138">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="3ba22-139">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ba22-139">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ba22-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ba22-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3ba22-141">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="3ba22-141">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="3ba22-142">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="3ba22-142">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3ba22-143">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3ba22-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3ba22-144">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="3ba22-144">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3ba22-145">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3ba22-145">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3ba22-146">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3ba22-146">\<customBinding></span></span>](custombinding.md)
