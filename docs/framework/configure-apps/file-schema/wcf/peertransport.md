---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 6765259f290047a4199a422b4ad0cced2ffee9ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783357"
---
# <a name="peertransport"></a><span data-ttu-id="bd343-101">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="bd343-101">\<peerTransport></span></span>
<span data-ttu-id="bd343-102">Özel bağlama için bir eş tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd343-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="bd343-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bd343-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bd343-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bd343-104">\<bindings></span></span>  
<span data-ttu-id="bd343-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bd343-105">\<customBinding></span></span>  
<span data-ttu-id="bd343-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bd343-106">\<binding></span></span>  
<span data-ttu-id="bd343-107">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="bd343-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd343-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd343-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd343-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd343-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bd343-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd343-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd343-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd343-111">Attributes</span></span>  
  
|<span data-ttu-id="bd343-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd343-112">Attribute</span></span>|<span data-ttu-id="bd343-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd343-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd343-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="bd343-114">listenIpAddress</span></span>|<span data-ttu-id="bd343-115">Eş düğüm TCP iletileri için dinleyeceği bir IP adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bd343-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="bd343-116">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bd343-116">The default is `null`.</span></span>|  
|<span data-ttu-id="bd343-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="bd343-117">maxBufferPoolSize</span></span>|<span data-ttu-id="bd343-118">Arabellek havuzu en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bd343-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="bd343-119">524288 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bd343-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="bd343-120">WCF pek çok bölümünün arabellekler kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd343-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="bd343-121">Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="bd343-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="bd343-122">Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün.</span><span class="sxs-lookup"><span data-stu-id="bd343-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="bd343-123">Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="bd343-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="bd343-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="bd343-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="bd343-125">En büyük ileti boyutu üst bilgiler dahil bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bd343-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="bd343-126">İleti alıcısı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır.</span><span class="sxs-lookup"><span data-stu-id="bd343-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="bd343-127">Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd343-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="bd343-128">65536 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bd343-128">The default is 65536.</span></span>|  
|<span data-ttu-id="bd343-129">bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="bd343-129">port</span></span>|<span data-ttu-id="bd343-130">Eş kanl TCP iletilerini işleyecek Bu bağlama üzerinde ağ arabirim katmanı bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bd343-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="bd343-131">Bu değer arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> ve <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="bd343-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="bd343-132">Varsayılan değer 0'dır.</span><span class="sxs-lookup"><span data-stu-id="bd343-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd343-133">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd343-133">Child Elements</span></span>  
  
|<span data-ttu-id="bd343-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd343-134">Element</span></span>|<span data-ttu-id="bd343-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd343-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd343-136">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bd343-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="bd343-137">Bu aktarım için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd343-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="bd343-138">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="bd343-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd343-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd343-139">Parent Elements</span></span>  
  
|<span data-ttu-id="bd343-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd343-140">Element</span></span>|<span data-ttu-id="bd343-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd343-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd343-142">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bd343-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bd343-143">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd343-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd343-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd343-144">Remarks</span></span>  
 <span data-ttu-id="bd343-145">Bu aktarım işlemleri istek/yanıt sözleşmeleriyle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bd343-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd343-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd343-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="bd343-147">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="bd343-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="bd343-148">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="bd343-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="bd343-149">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bd343-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bd343-150">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="bd343-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bd343-151">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bd343-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bd343-152">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bd343-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
