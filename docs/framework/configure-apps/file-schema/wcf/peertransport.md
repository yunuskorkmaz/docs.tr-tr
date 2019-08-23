---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 1ad05fd9125ecc8b3d5797e0dd335adbf808db84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933837"
---
# <a name="peertransport"></a><span data-ttu-id="efe2a-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="efe2a-101">\<peerTransport></span></span>
<span data-ttu-id="efe2a-102">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efe2a-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="efe2a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="efe2a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="efe2a-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="efe2a-104">\<bindings></span></span>  
<span data-ttu-id="efe2a-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="efe2a-105">\<customBinding></span></span>  
<span data-ttu-id="efe2a-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="efe2a-106">\<binding></span></span>  
<span data-ttu-id="efe2a-107">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="efe2a-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe2a-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efe2a-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe2a-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efe2a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="efe2a-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efe2a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe2a-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efe2a-111">Attributes</span></span>  
  
|<span data-ttu-id="efe2a-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="efe2a-112">Attribute</span></span>|<span data-ttu-id="efe2a-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efe2a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efe2a-114">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="efe2a-114">listenIpAddress</span></span>|<span data-ttu-id="efe2a-115">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="efe2a-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="efe2a-116">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="efe2a-116">The default is `null`.</span></span>|  
|<span data-ttu-id="efe2a-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="efe2a-117">maxBufferPoolSize</span></span>|<span data-ttu-id="efe2a-118">Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="efe2a-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="efe2a-119">Varsayılan değer 524288 ' dir.</span><span class="sxs-lookup"><span data-stu-id="efe2a-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="efe2a-120">WCF 'in birçok bölümü arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe2a-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="efe2a-121">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="efe2a-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="efe2a-122">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efe2a-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="efe2a-123">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="efe2a-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="efe2a-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="efe2a-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="efe2a-125">Üst bilgiler dahil olmak üzere en büyük ileti boyutunu bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="efe2a-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="efe2a-126">İletiyi gönderen ileti alıcı için çok büyük olduğunda bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="efe2a-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="efe2a-127">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="efe2a-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="efe2a-128">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="efe2a-128">The default is 65536.</span></span>|  
|<span data-ttu-id="efe2a-129">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="efe2a-129">port</span></span>|<span data-ttu-id="efe2a-130">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="efe2a-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="efe2a-131">Bu değer ve <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort>arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efe2a-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="efe2a-132">Varsayılan değer 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="efe2a-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efe2a-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efe2a-133">Child Elements</span></span>  
  
|<span data-ttu-id="efe2a-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="efe2a-134">Element</span></span>|<span data-ttu-id="efe2a-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efe2a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe2a-136">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="efe2a-136">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="efe2a-137">Bu taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efe2a-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="efe2a-138">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="efe2a-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efe2a-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efe2a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="efe2a-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="efe2a-140">Element</span></span>|<span data-ttu-id="efe2a-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efe2a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe2a-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="efe2a-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="efe2a-143">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efe2a-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efe2a-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efe2a-144">Remarks</span></span>  
 <span data-ttu-id="efe2a-145">Bu taşıma, istek/yanıt işlemleri olan sözleşmelerle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="efe2a-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efe2a-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efe2a-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="efe2a-147">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="efe2a-147">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="efe2a-148">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="efe2a-148">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="efe2a-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="efe2a-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="efe2a-150">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="efe2a-150">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="efe2a-151">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="efe2a-151">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="efe2a-152">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="efe2a-152">\<customBinding></span></span>](custombinding.md)
