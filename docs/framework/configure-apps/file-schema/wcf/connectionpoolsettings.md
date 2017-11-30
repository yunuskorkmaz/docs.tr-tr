---
title: '&lt;Tcptransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43b2719606321fe77bb9b017c6a4304ba02f7a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="515f0-102">&lt;Tcptransport&gt;</span><span class="sxs-lookup"><span data-stu-id="515f0-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="515f0-103">Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="515f0-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="515f0-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="515f0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="515f0-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="515f0-105">\<bindings></span></span>  
<span data-ttu-id="515f0-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="515f0-106">\<customBinding></span></span>  
<span data-ttu-id="515f0-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="515f0-107">\<binding></span></span>  
<span data-ttu-id="515f0-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="515f0-108">\<namePipeTransport></span></span>  
<span data-ttu-id="515f0-109">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="515f0-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="515f0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="515f0-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="515f0-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="515f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="515f0-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="515f0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="515f0-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="515f0-113">Attributes</span></span>  
  
|<span data-ttu-id="515f0-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="515f0-114">Attribute</span></span>|<span data-ttu-id="515f0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="515f0-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="515f0-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="515f0-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="515f0-117">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="515f0-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="515f0-118">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="515f0-118">The default is a "default" string.</span></span> <span data-ttu-id="515f0-119">Belirli bir istemci bağlantılarında ayrı gruplara ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="515f0-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="515f0-120">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="515f0-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="515f0-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="515f0-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="515f0-122">Bağlantılar hizmeti tarafından başlatılan uzak bir uç nokta için en fazla sayısını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="515f0-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="515f0-123">Sınırı aşan bağlantılar, sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="515f0-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="515f0-124">`idleTimeout` İçinde bağlantıları kalır sıraya alınmış bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="515f0-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="515f0-125">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="515f0-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="515f0-126">Bu öznitelik, belirli bir hizmet uç noktası istemciden eşzamanlı etkin bağlantı sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="515f0-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="515f0-127">Bu değer daha etkin istemci bağlantıları sağlayarak aşılırsa hizmeti istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="515f0-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="515f0-128">Bu durumda, bu değer belirli bir uç beklenen eşzamanlı istemci bağlantılarının üst sınırını aşan ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="515f0-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="515f0-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="515f0-129">Child Elements</span></span>  
 <span data-ttu-id="515f0-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="515f0-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="515f0-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="515f0-131">Parent Elements</span></span>  
  
|<span data-ttu-id="515f0-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="515f0-132">Element</span></span>|<span data-ttu-id="515f0-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="515f0-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="515f0-134">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="515f0-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="515f0-135">Adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="515f0-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="515f0-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="515f0-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="515f0-137">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="515f0-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="515f0-138">Taşıma seçme</span><span class="sxs-lookup"><span data-stu-id="515f0-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="515f0-139">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="515f0-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="515f0-140">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="515f0-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="515f0-141">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="515f0-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="515f0-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="515f0-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
