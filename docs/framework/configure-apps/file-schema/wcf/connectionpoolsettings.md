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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11500830c7c5fd75a9e2880a5875bd21fb070634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="764af-102">&lt;Tcptransport&gt;</span><span class="sxs-lookup"><span data-stu-id="764af-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="764af-103">Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="764af-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="764af-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="764af-104">\<system.serviceModel></span></span>  
<span data-ttu-id="764af-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="764af-105">\<bindings></span></span>  
<span data-ttu-id="764af-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="764af-106">\<customBinding></span></span>  
<span data-ttu-id="764af-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="764af-107">\<binding></span></span>  
<span data-ttu-id="764af-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="764af-108">\<namePipeTransport></span></span>  
<span data-ttu-id="764af-109">\<Namedpipetransport ></span><span class="sxs-lookup"><span data-stu-id="764af-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764af-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="764af-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="764af-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="764af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="764af-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="764af-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="764af-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="764af-113">Attributes</span></span>  
  
|<span data-ttu-id="764af-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="764af-114">Attribute</span></span>|<span data-ttu-id="764af-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764af-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="764af-116">Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="764af-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="764af-117">Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="764af-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="764af-118">Varsayılan bir "varsayılan" dizesidir.</span><span class="sxs-lookup"><span data-stu-id="764af-118">The default is a "default" string.</span></span> <span data-ttu-id="764af-119">Belirli bir istemci bağlantılarında ayrı gruplara ayırmak için bu değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="764af-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="764af-120">Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="764af-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="764af-121">Varsayılan değer 00:02:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="764af-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="764af-122">Bağlantılar hizmeti tarafından başlatılan uzak bir uç nokta için en fazla sayısını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="764af-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="764af-123">Sınırı aşan bağlantılar, sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır.</span><span class="sxs-lookup"><span data-stu-id="764af-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="764af-124">`idleTimeout` İçinde bağlantıları kalır sıraya alınmış bir özel durum önce süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="764af-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="764af-125">Varsayılan değer 10'dur.</span><span class="sxs-lookup"><span data-stu-id="764af-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="764af-126">Bu öznitelik, belirli bir hizmet uç noktası istemciden eşzamanlı etkin bağlantı sayısını sınırlar.</span><span class="sxs-lookup"><span data-stu-id="764af-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="764af-127">Bu değer daha etkin istemci bağlantıları sağlayarak aşılırsa hizmeti istemciye yanıt vermeyen görünebilir.</span><span class="sxs-lookup"><span data-stu-id="764af-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="764af-128">Bu durumda, bu değer belirli bir uç beklenen eşzamanlı istemci bağlantılarının üst sınırını aşan ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="764af-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="764af-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="764af-129">Child Elements</span></span>  
 <span data-ttu-id="764af-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="764af-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="764af-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="764af-131">Parent Elements</span></span>  
  
|<span data-ttu-id="764af-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="764af-132">Element</span></span>|<span data-ttu-id="764af-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="764af-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="764af-134">\<Connectionpoolsettings ></span><span class="sxs-lookup"><span data-stu-id="764af-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="764af-135">Adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="764af-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="764af-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="764af-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="764af-137">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="764af-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="764af-138">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="764af-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="764af-139">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="764af-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="764af-140">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="764af-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="764af-141">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="764af-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="764af-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="764af-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
