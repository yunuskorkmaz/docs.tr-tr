---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 76b8a0feaf51b39c9c988d853db7e3bf96244905
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284589"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="351b9-101">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="351b9-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="351b9-102">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="351b9-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="351b9-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="351b9-103">\<system.serviceModel></span></span>  
<span data-ttu-id="351b9-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="351b9-104">\<bindings></span></span>  
<span data-ttu-id="351b9-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="351b9-105">\<customBinding></span></span>  
<span data-ttu-id="351b9-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="351b9-106">\<binding></span></span>  
<span data-ttu-id="351b9-107">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="351b9-107">\<namePipeTransport></span></span>  
<span data-ttu-id="351b9-108">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="351b9-108">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="351b9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="351b9-109">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="351b9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="351b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="351b9-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="351b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="351b9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="351b9-112">Attributes</span></span>  
  
|<span data-ttu-id="351b9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="351b9-113">Attribute</span></span>|<span data-ttu-id="351b9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="351b9-114">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="351b9-115">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="351b9-115">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="351b9-116">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="351b9-116">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="351b9-117">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="351b9-117">The default is a "default" string.</span></span> <span data-ttu-id="351b9-118">Belirli bir istemci bağlantılarını ayrı gruplar halinde ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="351b9-118">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="351b9-119">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="351b9-119">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="351b9-120">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="351b9-120">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="351b9-121">En fazla hizmet tarafından başlatılan bir uzak uç noktasına bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="351b9-121">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="351b9-122">Sınırı aşan bağlantılar, sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="351b9-122">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="351b9-123">`idleTimeout` Hangi bağlantıları kalır sıraya alınan bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="351b9-123">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="351b9-124">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="351b9-124">The default is 10.</span></span><br /><br /> <span data-ttu-id="351b9-125">Bu öznitelik istemcisi eşzamanlı etkin bağlantılar için belirli hizmet uç noktası sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="351b9-125">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="351b9-126">Bu değer daha etkin istemci bağlantıları sağlayarak aşılıyorsa, hizmetin istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="351b9-126">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="351b9-127">Bu durumda, bu değeri belirli bir uç nokta için beklenen eşzamanlı istemci bağlantısına maksimum sayısını aşmaya ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="351b9-127">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="351b9-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="351b9-128">Child Elements</span></span>  
 <span data-ttu-id="351b9-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="351b9-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="351b9-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="351b9-130">Parent Elements</span></span>  
  
|<span data-ttu-id="351b9-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="351b9-131">Element</span></span>|<span data-ttu-id="351b9-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="351b9-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="351b9-133">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="351b9-133">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="351b9-134">Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="351b9-134">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="351b9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="351b9-135">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="351b9-136">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="351b9-136">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="351b9-137">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="351b9-137">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="351b9-138">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="351b9-138">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="351b9-139">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="351b9-139">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="351b9-140">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="351b9-140">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="351b9-141">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="351b9-141">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
