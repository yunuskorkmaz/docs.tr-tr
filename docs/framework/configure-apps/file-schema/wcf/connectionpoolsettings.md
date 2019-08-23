---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925968"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="f458e-101">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="f458e-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="f458e-102">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f458e-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="f458e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f458e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f458e-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f458e-104">\<bindings></span></span>  
<span data-ttu-id="f458e-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f458e-105">\<customBinding></span></span>  
<span data-ttu-id="f458e-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f458e-106">\<binding></span></span>  
<span data-ttu-id="f458e-107">\<Namepıetransport ></span><span class="sxs-lookup"><span data-stu-id="f458e-107">\<namePipeTransport></span></span>  
<span data-ttu-id="f458e-108">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="f458e-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f458e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f458e-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f458e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f458e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f458e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f458e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f458e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f458e-112">Attributes</span></span>  
  
|<span data-ttu-id="f458e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f458e-113">Attribute</span></span>|<span data-ttu-id="f458e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f458e-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="f458e-115">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="f458e-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="f458e-116">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f458e-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="f458e-117">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="f458e-117">The default is a "default" string.</span></span> <span data-ttu-id="f458e-118">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f458e-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="f458e-119">Bağlantı kesilmeden <xref:System.TimeSpan> önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="f458e-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="f458e-120">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f458e-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="f458e-121">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f458e-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="f458e-122">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="f458e-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="f458e-123">Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.`idleTimeout`</span><span class="sxs-lookup"><span data-stu-id="f458e-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="f458e-124">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="f458e-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="f458e-125">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="f458e-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="f458e-126">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f458e-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="f458e-127">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f458e-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f458e-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f458e-128">Child Elements</span></span>  
 <span data-ttu-id="f458e-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="f458e-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f458e-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f458e-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f458e-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="f458e-131">Element</span></span>|<span data-ttu-id="f458e-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f458e-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f458e-133">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="f458e-133">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="f458e-134">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f458e-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f458e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f458e-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f458e-136">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="f458e-136">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="f458e-137">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="f458e-137">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="f458e-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f458e-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f458e-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f458e-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f458e-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f458e-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f458e-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f458e-141">\<customBinding></span></span>](custombinding.md)
