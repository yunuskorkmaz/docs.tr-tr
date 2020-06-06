---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736513"
---
# \<peerTransport>
<span data-ttu-id="14a47-101">Özel bağlama için bir eş taşıma tanımlar.</span><span class="sxs-lookup"><span data-stu-id="14a47-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="14a47-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14a47-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14a47-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14a47-103">Attributes and Elements</span></span>  
 <span data-ttu-id="14a47-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14a47-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14a47-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14a47-105">Attributes</span></span>  
  
|<span data-ttu-id="14a47-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14a47-106">Attribute</span></span>|<span data-ttu-id="14a47-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14a47-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14a47-108">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="14a47-108">listenIpAddress</span></span>|<span data-ttu-id="14a47-109">Eş düğümün TCP iletilerini dinleyeceği bir IP adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="14a47-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="14a47-110">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="14a47-110">The default is `null`.</span></span>|  
|<span data-ttu-id="14a47-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="14a47-111">maxBufferPoolSize</span></span>|<span data-ttu-id="14a47-112">Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="14a47-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="14a47-113">Varsayılan değer 524288 ' dir.</span><span class="sxs-lookup"><span data-stu-id="14a47-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="14a47-114">WCF 'in birçok bölümü arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="14a47-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="14a47-115">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="14a47-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="14a47-116">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a47-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="14a47-117">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="14a47-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="14a47-118">Değerini</span><span class="sxs-lookup"><span data-stu-id="14a47-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="14a47-119">Üst bilgiler dahil olmak üzere en büyük ileti boyutunu bayt cinsinden tanımlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="14a47-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="14a47-120">İletiyi gönderen ileti alıcı için çok büyük olduğunda bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="14a47-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="14a47-121">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="14a47-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="14a47-122">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="14a47-122">The default is 65536.</span></span>|  
|<span data-ttu-id="14a47-123">port</span><span class="sxs-lookup"><span data-stu-id="14a47-123">port</span></span>|<span data-ttu-id="14a47-124">Bu bağlamanın eş kanal TCP iletilerini işleyecağı ağ arabirimi bağlantı noktasını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="14a47-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="14a47-125">Bu değer ve arasında olmalıdır <xref:System.Net.IPEndPoint.MinPort> <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="14a47-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="14a47-126">Varsayılan değer, 0'dur.</span><span class="sxs-lookup"><span data-stu-id="14a47-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14a47-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14a47-127">Child Elements</span></span>  
  
|<span data-ttu-id="14a47-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="14a47-128">Element</span></span>|<span data-ttu-id="14a47-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14a47-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="14a47-130">Bu taşımanın güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="14a47-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="14a47-131">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="14a47-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14a47-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14a47-132">Parent Elements</span></span>  
  
|<span data-ttu-id="14a47-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="14a47-133">Element</span></span>|<span data-ttu-id="14a47-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14a47-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="14a47-135">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="14a47-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14a47-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14a47-136">Remarks</span></span>  
 <span data-ttu-id="14a47-137">Bu taşıma, istek/yanıt işlemleri olan sözleşmelerle kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="14a47-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a47-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14a47-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="14a47-139">Taşımalar</span><span class="sxs-lookup"><span data-stu-id="14a47-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="14a47-140">Taşıma Seçme</span><span class="sxs-lookup"><span data-stu-id="14a47-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="14a47-141">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="14a47-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="14a47-142">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="14a47-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="14a47-143">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="14a47-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
