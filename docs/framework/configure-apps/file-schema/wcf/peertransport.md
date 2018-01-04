---
title: '&lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb60d901d498c6db194e60a9229c0d5b69eee31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="9f533-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="9f533-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="9f533-103">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f533-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="9f533-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9f533-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9f533-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9f533-105">\<bindings></span></span>  
<span data-ttu-id="9f533-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9f533-106">\<customBinding></span></span>  
<span data-ttu-id="9f533-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9f533-107">\<binding></span></span>  
<span data-ttu-id="9f533-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="9f533-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f533-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f533-109">Syntax</span></span>  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f533-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f533-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9f533-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f533-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f533-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f533-112">Attributes</span></span>  
  
|<span data-ttu-id="9f533-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f533-113">Attribute</span></span>|<span data-ttu-id="9f533-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f533-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f533-115">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="9f533-115">listenIpAddress</span></span>|<span data-ttu-id="9f533-116">Eş düğüm için TCP iletileri dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9f533-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="9f533-117">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="9f533-117">The default is `null`.</span></span>|  
|<span data-ttu-id="9f533-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="9f533-118">maxBufferPoolSize</span></span>|<span data-ttu-id="9f533-119">Arabellek havuzu boyutunun üst sınırını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9f533-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="9f533-120">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9f533-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="9f533-121">WCF pek çok bölümü arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f533-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="9f533-122">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f533-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="9f533-123">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="9f533-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="9f533-124">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="9f533-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="9f533-125">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="9f533-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="9f533-126">Üst bilgileri de dahil olmak üzere bayt cinsinden maksimum ileti boyutu tanımlar pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9f533-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="9f533-127">İleti alıcı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="9f533-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="9f533-128">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f533-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="9f533-129">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9f533-129">The default is 65536.</span></span>|  
|<span data-ttu-id="9f533-130">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="9f533-130">port</span></span>|<span data-ttu-id="9f533-131">Bu bağlama eş kanal TCP iletilerini işleyecek ağ arabirim bağlantı noktası belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9f533-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="9f533-132">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="9f533-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="9f533-133">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="9f533-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f533-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f533-134">Child Elements</span></span>  
  
|<span data-ttu-id="9f533-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f533-135">Element</span></span>|<span data-ttu-id="9f533-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f533-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f533-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9f533-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="9f533-138">Bu aktarım için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f533-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="9f533-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9f533-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f533-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f533-140">Parent Elements</span></span>  
  
|<span data-ttu-id="9f533-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f533-141">Element</span></span>|<span data-ttu-id="9f533-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f533-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f533-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9f533-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9f533-144">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f533-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f533-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f533-145">Remarks</span></span>  
 <span data-ttu-id="9f533-146">Bu aktarım istek/yanıt işlemleri sahip sözleşmeleri ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f533-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f533-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f533-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9f533-148">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="9f533-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="9f533-149">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="9f533-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="9f533-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9f533-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9f533-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9f533-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9f533-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9f533-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9f533-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9f533-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
