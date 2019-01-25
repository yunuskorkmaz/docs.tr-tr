---
title: '&lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: c8ca9f37b799087337f7dff6be48744f4f9dea6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703633"
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="4ffd5-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="4ffd5-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="4ffd5-103">Özel bağlama için bir eş tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="4ffd5-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4ffd5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4ffd5-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-105">\<bindings></span></span>  
<span data-ttu-id="4ffd5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-106">\<customBinding></span></span>  
<span data-ttu-id="4ffd5-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-107">\<binding></span></span>  
<span data-ttu-id="4ffd5-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ffd5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ffd5-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ffd5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ffd5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4ffd5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ffd5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4ffd5-112">Attributes</span></span>  
  
|<span data-ttu-id="4ffd5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4ffd5-113">Attribute</span></span>|<span data-ttu-id="4ffd5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ffd5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4ffd5-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="4ffd5-115">listenIpAddress</span></span>|<span data-ttu-id="4ffd5-116">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="4ffd5-117">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-117">The default is `null`.</span></span>|  
|<span data-ttu-id="4ffd5-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4ffd5-118">maxBufferPoolSize</span></span>|<span data-ttu-id="4ffd5-119">Arabellek havuzu en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="4ffd5-120">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="4ffd5-121">WCF pek çok bölümünün arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="4ffd5-122">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4ffd5-123">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4ffd5-124">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4ffd5-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4ffd5-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="4ffd5-126">En büyük ileti boyutu üst bilgiler dahil bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="4ffd5-127">İleti alıcısı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="4ffd5-128">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4ffd5-129">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-129">The default is 65536.</span></span>|  
|<span data-ttu-id="4ffd5-130">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="4ffd5-130">port</span></span>|<span data-ttu-id="4ffd5-131">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="4ffd5-132">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="4ffd5-133">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ffd5-134">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ffd5-134">Child Elements</span></span>  
  
|<span data-ttu-id="4ffd5-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ffd5-135">Element</span></span>|<span data-ttu-id="4ffd5-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ffd5-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ffd5-137">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="4ffd5-138">Bu aktarım için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="4ffd5-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ffd5-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4ffd5-140">Parent Elements</span></span>  
  
|<span data-ttu-id="4ffd5-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="4ffd5-141">Element</span></span>|<span data-ttu-id="4ffd5-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ffd5-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ffd5-143">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4ffd5-144">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ffd5-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ffd5-145">Remarks</span></span>  
 <span data-ttu-id="4ffd5-146">Bu aktarım işlemleri istek/yanıt sözleşmeleriyle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffd5-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ffd5-147">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4ffd5-148">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="4ffd5-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="4ffd5-149">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="4ffd5-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4ffd5-150">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4ffd5-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4ffd5-151">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="4ffd5-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4ffd5-152">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4ffd5-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4ffd5-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4ffd5-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
