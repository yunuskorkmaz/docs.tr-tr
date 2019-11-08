---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736513"
---
# <a name="peertransport"></a><span data-ttu-id="513f6-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="513f6-101">\<peerTransport></span></span>
<span data-ttu-id="513f6-102">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="513f6-102">Defines a peer transport for a custom binding.</span></span>  
  
<span data-ttu-id="513f6-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="513f6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="513f6-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="513f6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="513f6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="513f6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="513f6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="513f6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="513f6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="513f6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="513f6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**</span><span class="sxs-lookup"><span data-stu-id="513f6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="513f6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="513f6-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="513f6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="513f6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="513f6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="513f6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="513f6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="513f6-112">Attributes</span></span>  
  
|<span data-ttu-id="513f6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="513f6-113">Attribute</span></span>|<span data-ttu-id="513f6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="513f6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="513f6-115">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="513f6-115">listenIpAddress</span></span>|<span data-ttu-id="513f6-116">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="513f6-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="513f6-117">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="513f6-117">The default is `null`.</span></span>|  
|<span data-ttu-id="513f6-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="513f6-118">maxBufferPoolSize</span></span>|<span data-ttu-id="513f6-119">Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="513f6-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="513f6-120">Varsayılan değer 524288 ' dir.</span><span class="sxs-lookup"><span data-stu-id="513f6-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="513f6-121">WCF 'in birçok bölümü arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="513f6-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="513f6-122">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="513f6-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="513f6-123">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="513f6-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="513f6-124">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="513f6-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="513f6-125">Değerini</span><span class="sxs-lookup"><span data-stu-id="513f6-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="513f6-126">Üst bilgiler dahil olmak üzere en büyük ileti boyutunu bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="513f6-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="513f6-127">İletiyi gönderen ileti alıcı için çok büyük olduğunda bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="513f6-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="513f6-128">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="513f6-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="513f6-129">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="513f6-129">The default is 65536.</span></span>|  
|<span data-ttu-id="513f6-130">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="513f6-130">port</span></span>|<span data-ttu-id="513f6-131">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="513f6-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="513f6-132">Bu değer <xref:System.Net.IPEndPoint.MinPort> ile <xref:System.Net.IPEndPoint.MaxPort>arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="513f6-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="513f6-133">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="513f6-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="513f6-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="513f6-134">Child Elements</span></span>  
  
|<span data-ttu-id="513f6-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="513f6-135">Element</span></span>|<span data-ttu-id="513f6-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="513f6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="513f6-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="513f6-137">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="513f6-138">Bu taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="513f6-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="513f6-139">Bu öğe <xref:System.ServiceModel.Configuration.PeerSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="513f6-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="513f6-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="513f6-140">Parent Elements</span></span>  
  
|<span data-ttu-id="513f6-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="513f6-141">Element</span></span>|<span data-ttu-id="513f6-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="513f6-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="513f6-143">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="513f6-143">\<binding></span></span>](bindings.md)|<span data-ttu-id="513f6-144">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="513f6-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="513f6-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="513f6-145">Remarks</span></span>  
 <span data-ttu-id="513f6-146">Bu taşıma, istek/yanıt işlemleri olan sözleşmelerle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="513f6-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513f6-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="513f6-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="513f6-148">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="513f6-148">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="513f6-149">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="513f6-149">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="513f6-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="513f6-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="513f6-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="513f6-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="513f6-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="513f6-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="513f6-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="513f6-153">\<customBinding></span></span>](custombinding.md)
