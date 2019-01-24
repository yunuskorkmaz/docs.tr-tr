---
title: '&lt;Tcptransport&gt;'
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 1e3001f60ae0f18fee88678cae1e9e55d90822c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526775"
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="fcd2f-102">&lt;Tcptransport&gt;</span><span class="sxs-lookup"><span data-stu-id="fcd2f-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="fcd2f-103">Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="fcd2f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fcd2f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fcd2f-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="fcd2f-105">\<bindings></span></span>  
<span data-ttu-id="fcd2f-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fcd2f-106">\<customBinding></span></span>  
<span data-ttu-id="fcd2f-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="fcd2f-107">\<binding></span></span>  
<span data-ttu-id="fcd2f-108">\<namePipeTransport></span><span class="sxs-lookup"><span data-stu-id="fcd2f-108">\<namePipeTransport></span></span>  
<span data-ttu-id="fcd2f-109">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="fcd2f-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd2f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcd2f-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd2f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd2f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fcd2f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd2f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fcd2f-113">Attributes</span></span>  
  
|<span data-ttu-id="fcd2f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fcd2f-114">Attribute</span></span>|<span data-ttu-id="fcd2f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd2f-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="fcd2f-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="fcd2f-117">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="fcd2f-118">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-118">The default is a "default" string.</span></span> <span data-ttu-id="fcd2f-119">Belirli bir istemci bağlantılarını ayrı gruplar halinde ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="fcd2f-120">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="fcd2f-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="fcd2f-122">En fazla hizmet tarafından başlatılan bir uzak uç noktasına bağlantı sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="fcd2f-123">Sınırı aşan bağlantılar, sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="fcd2f-124">`idleTimeout` Hangi bağlantıları kalır sıraya alınan bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="fcd2f-125">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="fcd2f-126">Bu öznitelik istemcisi eşzamanlı etkin bağlantılar için belirli hizmet uç noktası sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="fcd2f-127">Bu değer daha etkin istemci bağlantıları sağlayarak aşılıyorsa, hizmetin istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="fcd2f-128">Bu durumda, bu değeri belirli bir uç nokta için beklenen eşzamanlı istemci bağlantısına maksimum sayısını aşmaya ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcd2f-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd2f-129">Child Elements</span></span>  
 <span data-ttu-id="fcd2f-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd2f-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fcd2f-131">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd2f-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="fcd2f-132">Element</span></span>|<span data-ttu-id="fcd2f-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fcd2f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcd2f-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="fcd2f-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="fcd2f-135">Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcd2f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcd2f-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fcd2f-137">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="fcd2f-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="fcd2f-138">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="fcd2f-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="fcd2f-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fcd2f-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fcd2f-140">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="fcd2f-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="fcd2f-141">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fcd2f-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="fcd2f-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fcd2f-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
