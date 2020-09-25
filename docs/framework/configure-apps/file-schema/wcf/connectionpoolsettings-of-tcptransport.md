---
title: <connectionPoolSettings> / <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 53523fd550ecad931bfb2af5eb9beb71c60d44f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176012"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="2c977-102">\<connectionPoolSettings> / \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="2c977-102">\<connectionPoolSettings> of \<tcpTransport></span></span>

<span data-ttu-id="2c977-103">TCP aktarımı için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c977-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="2c977-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c977-104">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c977-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c977-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2c977-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c977-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c977-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c977-107">Attributes</span></span>  
  
|<span data-ttu-id="2c977-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c977-108">Attribute</span></span>|<span data-ttu-id="2c977-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c977-109">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="2c977-110">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="2c977-110">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="2c977-111">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2c977-111">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="2c977-112">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="2c977-112">The default is a "default" string.</span></span> <span data-ttu-id="2c977-113">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c977-113">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="2c977-114"><xref:System.TimeSpan>Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="2c977-114">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="2c977-115">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2c977-115">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="2c977-116"><xref:System.TimeSpan>Etkin bir bağlantının kapatıldığı zamanı belirten bir.</span><span class="sxs-lookup"><span data-stu-id="2c977-116">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="2c977-117">Varsayılan değer 00:05:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2c977-117">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="2c977-118">Bağlantı, etkin iletim sırasında değil bağlantı önbelleğine döndürülmeden sonra kapatılır.</span><span class="sxs-lookup"><span data-stu-id="2c977-118">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="2c977-119">TCP aktarımı tarafından kullanılan bağlantı önbelleği, her bir uç nokta için gerektiği şekilde, tarafından ayarlanan önbellek sınırına kadar yeni bağlantılar oluşturur. `maxOutboundConnectionsPerEndpoint.`</span><span class="sxs-lookup"><span data-stu-id="2c977-119">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="2c977-120">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2c977-120">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="2c977-121">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="2c977-121">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="2c977-122">`idleTimeout`Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="2c977-122">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="2c977-123">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="2c977-123">The default is 10.</span></span><br /><br /> <span data-ttu-id="2c977-124">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="2c977-124">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="2c977-125">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2c977-125">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="2c977-126">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c977-126">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c977-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c977-127">Child Elements</span></span>  

 <span data-ttu-id="2c977-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c977-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c977-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2c977-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2c977-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c977-130">Element</span></span>|<span data-ttu-id="2c977-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c977-131">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="2c977-132">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c977-132">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c977-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c977-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2c977-134">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="2c977-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="2c977-135">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="2c977-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="2c977-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2c977-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2c977-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2c977-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2c977-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2c977-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
