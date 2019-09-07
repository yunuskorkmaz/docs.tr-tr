---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: d896953a7ed31fdaf5f357a8721c7d085d50bc56
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400063"
---
# <a name="peertransport"></a><span data-ttu-id="48b7a-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="48b7a-101">\<peerTransport></span></span>
<span data-ttu-id="48b7a-102">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48b7a-102">Defines a peer transport for a custom binding.</span></span>  
  
<span data-ttu-id="48b7a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48b7a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48b7a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="48b7a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="48b7a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="48b7a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="48b7a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="48b7a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="48b7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="48b7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="48b7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**</span><span class="sxs-lookup"><span data-stu-id="48b7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b7a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48b7a-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48b7a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="48b7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="48b7a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48b7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48b7a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48b7a-112">Attributes</span></span>  
  
|<span data-ttu-id="48b7a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="48b7a-113">Attribute</span></span>|<span data-ttu-id="48b7a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48b7a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48b7a-115">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="48b7a-115">listenIpAddress</span></span>|<span data-ttu-id="48b7a-116">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="48b7a-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="48b7a-117">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="48b7a-117">The default is `null`.</span></span>|  
|<span data-ttu-id="48b7a-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="48b7a-118">maxBufferPoolSize</span></span>|<span data-ttu-id="48b7a-119">Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="48b7a-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="48b7a-120">Varsayılan değer 524288 ' dir.</span><span class="sxs-lookup"><span data-stu-id="48b7a-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="48b7a-121">WCF 'in birçok bölümü arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="48b7a-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="48b7a-122">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="48b7a-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="48b7a-123">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48b7a-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="48b7a-124">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="48b7a-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="48b7a-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="48b7a-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="48b7a-126">Üst bilgiler dahil olmak üzere en büyük ileti boyutunu bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="48b7a-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="48b7a-127">İletiyi gönderen ileti alıcı için çok büyük olduğunda bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="48b7a-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="48b7a-128">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48b7a-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="48b7a-129">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="48b7a-129">The default is 65536.</span></span>|  
|<span data-ttu-id="48b7a-130">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="48b7a-130">port</span></span>|<span data-ttu-id="48b7a-131">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="48b7a-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="48b7a-132">Bu değer ve <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort>arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48b7a-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="48b7a-133">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="48b7a-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48b7a-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="48b7a-134">Child Elements</span></span>  
  
|<span data-ttu-id="48b7a-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="48b7a-135">Element</span></span>|<span data-ttu-id="48b7a-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48b7a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48b7a-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="48b7a-137">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="48b7a-138">Bu taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48b7a-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="48b7a-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="48b7a-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48b7a-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="48b7a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="48b7a-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="48b7a-141">Element</span></span>|<span data-ttu-id="48b7a-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="48b7a-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48b7a-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="48b7a-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="48b7a-144">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48b7a-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48b7a-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48b7a-145">Remarks</span></span>  
 <span data-ttu-id="48b7a-146">Bu taşıma, istek/yanıt işlemleri olan sözleşmelerle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="48b7a-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b7a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48b7a-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="48b7a-148">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="48b7a-148">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="48b7a-149">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="48b7a-149">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="48b7a-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48b7a-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48b7a-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="48b7a-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="48b7a-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="48b7a-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="48b7a-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="48b7a-153">\<customBinding></span></span>](custombinding.md)
