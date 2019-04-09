---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 6765259f290047a4199a422b4ad0cced2ffee9ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179836"
---
# <a name="peertransport"></a><span data-ttu-id="2b80e-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="2b80e-101">\<peerTransport></span></span>
<span data-ttu-id="2b80e-102">Özel bağlama için bir eş tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b80e-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="2b80e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2b80e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2b80e-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="2b80e-104">\<bindings></span></span>  
<span data-ttu-id="2b80e-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b80e-105">\<customBinding></span></span>  
<span data-ttu-id="2b80e-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2b80e-106">\<binding></span></span>  
<span data-ttu-id="2b80e-107">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="2b80e-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b80e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b80e-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b80e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b80e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2b80e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b80e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b80e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b80e-111">Attributes</span></span>  
  
|<span data-ttu-id="2b80e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b80e-112">Attribute</span></span>|<span data-ttu-id="2b80e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b80e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b80e-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="2b80e-114">listenIpAddress</span></span>|<span data-ttu-id="2b80e-115">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b80e-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="2b80e-116">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="2b80e-116">The default is `null`.</span></span>|  
|<span data-ttu-id="2b80e-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2b80e-117">maxBufferPoolSize</span></span>|<span data-ttu-id="2b80e-118">Arabellek havuzu en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2b80e-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="2b80e-119">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="2b80e-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="2b80e-120">WCF pek çok bölümünün arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b80e-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="2b80e-121">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b80e-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="2b80e-122">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="2b80e-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="2b80e-123">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="2b80e-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="2b80e-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2b80e-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="2b80e-125">En büyük ileti boyutu üst bilgiler dahil bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2b80e-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="2b80e-126">İleti alıcısı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="2b80e-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="2b80e-127">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b80e-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="2b80e-128">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="2b80e-128">The default is 65536.</span></span>|  
|<span data-ttu-id="2b80e-129">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="2b80e-129">port</span></span>|<span data-ttu-id="2b80e-130">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2b80e-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="2b80e-131">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="2b80e-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="2b80e-132">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="2b80e-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b80e-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b80e-133">Child Elements</span></span>  
  
|<span data-ttu-id="2b80e-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b80e-134">Element</span></span>|<span data-ttu-id="2b80e-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b80e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b80e-136">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="2b80e-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="2b80e-137">Bu aktarım için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b80e-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="2b80e-138">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2b80e-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b80e-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b80e-139">Parent Elements</span></span>  
  
|<span data-ttu-id="2b80e-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b80e-140">Element</span></span>|<span data-ttu-id="2b80e-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b80e-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b80e-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="2b80e-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2b80e-143">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b80e-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b80e-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b80e-144">Remarks</span></span>  
 <span data-ttu-id="2b80e-145">Bu aktarım işlemleri istek/yanıt sözleşmeleriyle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2b80e-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b80e-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b80e-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2b80e-147">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="2b80e-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="2b80e-148">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="2b80e-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="2b80e-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2b80e-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2b80e-150">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="2b80e-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2b80e-151">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="2b80e-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2b80e-152">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b80e-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
