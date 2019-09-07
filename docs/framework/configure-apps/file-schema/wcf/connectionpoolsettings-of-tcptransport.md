---
title: <connectionPoolSettings> / <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: f9b0fff741c32c1a3d6f9461f478e89acc18114e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398091"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="ab184-102">\<\<TcpTransport > ConnectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="ab184-102">\<connectionPoolSettings> of \<tcpTransport></span></span>
<span data-ttu-id="ab184-103">TCP aktarımı için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ab184-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
<span data-ttu-id="ab184-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab184-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab184-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ab184-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ab184-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ab184-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ab184-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="ab184-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="ab184-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="ab184-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ab184-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tcpTransport >** ](tcptransport.md)</span><span class="sxs-lookup"><span data-stu-id="ab184-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)</span></span>\
<span data-ttu-id="ab184-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="ab184-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab184-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab184-111">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab184-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab184-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ab184-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab184-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab184-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab184-114">Attributes</span></span>  
  
|<span data-ttu-id="ab184-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ab184-115">Attribute</span></span>|<span data-ttu-id="ab184-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab184-116">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="ab184-117">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="ab184-117">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="ab184-118">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ab184-118">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="ab184-119">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="ab184-119">The default is a "default" string.</span></span> <span data-ttu-id="ab184-120">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab184-120">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="ab184-121">Bağlantı kesilmeden <xref:System.TimeSpan> önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="ab184-121">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="ab184-122">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ab184-122">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="ab184-123">Etkin <xref:System.TimeSpan> bir bağlantının kapatıldığı zamanı belirten bir.</span><span class="sxs-lookup"><span data-stu-id="ab184-123">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="ab184-124">Varsayılan değer 00:05:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ab184-124">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="ab184-125">Bağlantı, etkin iletim sırasında değil bağlantı önbelleğine döndürülmeden sonra kapatılır.</span><span class="sxs-lookup"><span data-stu-id="ab184-125">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="ab184-126">TCP aktarımı tarafından kullanılan bağlantı önbelleği, her bir uç nokta için gerektiği şekilde, tarafından ayarlanan önbellek sınırına kadar yeni bağlantılar oluşturur.`maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="ab184-126">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="ab184-127">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ab184-127">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="ab184-128">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="ab184-128">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="ab184-129">Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.`idleTimeout`</span><span class="sxs-lookup"><span data-stu-id="ab184-129">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="ab184-130">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="ab184-130">The default is 10.</span></span><br /><br /> <span data-ttu-id="ab184-131">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="ab184-131">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="ab184-132">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ab184-132">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="ab184-133">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab184-133">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab184-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab184-134">Child Elements</span></span>  
 <span data-ttu-id="ab184-135">Yok.</span><span class="sxs-lookup"><span data-stu-id="ab184-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab184-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab184-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ab184-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab184-137">Element</span></span>|<span data-ttu-id="ab184-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab184-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab184-139">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="ab184-139">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="ab184-140">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ab184-140">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab184-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab184-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ab184-142">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="ab184-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="ab184-143">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="ab184-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ab184-144">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ab184-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ab184-145">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ab184-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ab184-146">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ab184-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ab184-147">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ab184-147">\<customBinding></span></span>](custombinding.md)
