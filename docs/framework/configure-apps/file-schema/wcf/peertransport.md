---
title: '&lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: df192c6a602aa073f48fab4229b4be3fbeb2349d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748626"
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="a8bfd-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="a8bfd-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="a8bfd-103">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="a8bfd-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a8bfd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a8bfd-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-105">\<bindings></span></span>  
<span data-ttu-id="a8bfd-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-106">\<customBinding></span></span>  
<span data-ttu-id="a8bfd-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-107">\<binding></span></span>  
<span data-ttu-id="a8bfd-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8bfd-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8bfd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8bfd-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8bfd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a8bfd-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8bfd-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8bfd-112">Attributes</span></span>  
  
|<span data-ttu-id="a8bfd-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8bfd-113">Attribute</span></span>|<span data-ttu-id="a8bfd-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8bfd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8bfd-115">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="a8bfd-115">listenIpAddress</span></span>|<span data-ttu-id="a8bfd-116">Eş düğüm için TCP iletileri dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="a8bfd-117">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-117">The default is `null`.</span></span>|  
|<span data-ttu-id="a8bfd-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a8bfd-118">maxBufferPoolSize</span></span>|<span data-ttu-id="a8bfd-119">Arabellek havuzu boyutunun üst sınırını belirtir pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="a8bfd-120">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="a8bfd-121">WCF pek çok bölümü arabellekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="a8bfd-122">Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="a8bfd-123">Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="a8bfd-124">Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="a8bfd-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a8bfd-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="a8bfd-126">Üst bilgileri de dahil olmak üzere bayt cinsinden maksimum ileti boyutu tanımlar pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="a8bfd-127">İleti alıcı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="a8bfd-128">Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="a8bfd-129">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-129">The default is 65536.</span></span>|  
|<span data-ttu-id="a8bfd-130">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="a8bfd-130">port</span></span>|<span data-ttu-id="a8bfd-131">Bu bağlama eş kanal TCP iletilerini işleyecek ağ arabirim bağlantı noktası belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="a8bfd-132">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="a8bfd-133">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8bfd-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8bfd-134">Child Elements</span></span>  
  
|<span data-ttu-id="a8bfd-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8bfd-135">Element</span></span>|<span data-ttu-id="a8bfd-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8bfd-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8bfd-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="a8bfd-138">Bu aktarım için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="a8bfd-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8bfd-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8bfd-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a8bfd-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8bfd-141">Element</span></span>|<span data-ttu-id="a8bfd-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8bfd-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8bfd-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a8bfd-144">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8bfd-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8bfd-145">Remarks</span></span>  
 <span data-ttu-id="a8bfd-146">Bu aktarım istek/yanıt işlemleri sahip sözleşmeleri ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8bfd-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8bfd-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a8bfd-148">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="a8bfd-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="a8bfd-149">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="a8bfd-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="a8bfd-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a8bfd-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a8bfd-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a8bfd-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a8bfd-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a8bfd-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a8bfd-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a8bfd-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
