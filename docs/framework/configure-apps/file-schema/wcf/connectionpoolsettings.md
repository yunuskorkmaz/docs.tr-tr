---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400476"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="0eeeb-101">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="0eeeb-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="0eeeb-102">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
<span data-ttu-id="0eeeb-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0eeeb-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0eeeb-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0eeeb-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0eeeb-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0eeeb-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0eeeb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="0eeeb-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="0eeeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="0eeeb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="0eeeb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedPipeTransport >** ](namedpipetransport.md)</span><span class="sxs-lookup"><span data-stu-id="0eeeb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)</span></span>\
<span data-ttu-id="0eeeb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="0eeeb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eeeb-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0eeeb-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eeeb-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0eeeb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0eeeb-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eeeb-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0eeeb-113">Attributes</span></span>  
  
|<span data-ttu-id="0eeeb-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0eeeb-114">Attribute</span></span>|<span data-ttu-id="0eeeb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0eeeb-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="0eeeb-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="0eeeb-117">Akışlı modda bağlantılar paylaşılmaz, yani bağlantı havuzunun devre dışı bırakıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="0eeeb-118">Varsayılan değer "default" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-118">The default is a "default" string.</span></span> <span data-ttu-id="0eeeb-119">Belirli bir istemcinin bağlantılarını ayrı gruplar halinde yalıtmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="0eeeb-120">Bağlantı kesilmeden <xref:System.TimeSpan> önce bağlantının boşta kalabileceği en uzun süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="0eeeb-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="0eeeb-122">Hizmet tarafından başlatılan bir uzak uç noktaya bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="0eeeb-123">Sınırın üzerindeki bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="0eeeb-124">Bir özel durum oluşturulmadan önce bağlantıların sırada kalacağı süreyi sınırlandırır.`idleTimeout`</span><span class="sxs-lookup"><span data-stu-id="0eeeb-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="0eeeb-125">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="0eeeb-126">Bu öznitelik, eşzamanlı etkin bağlantı sayısını istemciden belirli bir hizmet uç noktasına sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="0eeeb-127">Bu değer, daha etkin istemci bağlantılarına sahip olacak şekilde aşılırsa, hizmet istemciye yanıt vermemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="0eeeb-128">Bu durumda, bu değerin belirli bir uç nokta ile beklenen eşzamanlı istemci bağlantısı sayısı üst sınırını aşmayacak şekilde ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eeeb-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0eeeb-129">Child Elements</span></span>  
 <span data-ttu-id="0eeeb-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eeeb-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0eeeb-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0eeeb-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="0eeeb-132">Element</span></span>|<span data-ttu-id="0eeeb-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0eeeb-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eeeb-134">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="0eeeb-134">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="0eeeb-135">Bir kanalın adlandırılmış kanallar kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0eeeb-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0eeeb-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0eeeb-137">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="0eeeb-137">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="0eeeb-138">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="0eeeb-138">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="0eeeb-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0eeeb-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0eeeb-140">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="0eeeb-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0eeeb-141">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0eeeb-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0eeeb-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0eeeb-142">\<customBinding></span></span>](custombinding.md)
