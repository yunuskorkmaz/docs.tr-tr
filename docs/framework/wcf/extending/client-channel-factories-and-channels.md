---
title: "İstemci: Kanal Fabrikaları ve Kanallar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82e42a3dd4fbb29970b8e1a17333b66d85d2887b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="056d0-102">İstemci: Kanal Fabrikaları ve Kanallar</span><span class="sxs-lookup"><span data-stu-id="056d0-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="056d0-103">Bu konu, kanal fabrikaları ve kanallar oluşturulmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="056d0-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="056d0-104">Kanal fabrikaları ve kanallar</span><span class="sxs-lookup"><span data-stu-id="056d0-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="056d0-105">Kanal fabrikaları kanalları oluşturmaktan sorumlu.</span><span class="sxs-lookup"><span data-stu-id="056d0-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="056d0-106">Kanal üreteçleri tarafından oluşturulan kanallar ileti göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="056d0-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="056d0-107">Katmandan ileti alma, gerekli işlemleri gerçekleştirip sonra katmana ileti göndermek için bu kanalları sorumludur.</span><span class="sxs-lookup"><span data-stu-id="056d0-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="056d0-108">Aşağıdaki grafikte bu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="056d0-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="056d0-109">![İstemci fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="056d0-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="056d0-110">Kanal fabrikası kanalları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="056d0-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="056d0-111">Kapatıldığında, henüz kapatılmamış oluşturuldukları kanalları kapatma kanal fabrikaları sorumludur.</span><span class="sxs-lookup"><span data-stu-id="056d0-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="056d0-112">Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanallar ancak iletileri almaya devam edebilmesi için varolan kanalları açmak bırakır kabul durdurduğu olduğundan model burada asimetrik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="056d0-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="056d0-113">Bu işlem için temel sınıfı Yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="056d0-113"> provides base class helpers for this process.</span></span> <span data-ttu-id="056d0-114">(Bu konuda tartışılan kanal yardımcı sınıfları diyagramı için bkz: [kanal modeli genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="056d0-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="056d0-115"><xref:System.ServiceModel.Channels.CommunicationObject> Uygulayan sınıf <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda açıklanan durum makinesinin zorlar [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="056d0-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="056d0-116">''<xref:System.ServiceModel.Channels.ChannelManagerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.CommunicationObject> ve birleştirilmiş bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="056d0-116">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="056d0-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıfı olan <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="056d0-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="056d0-118">''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` overloads birine `OnCreateChannel` soyut yöntemi.</span><span class="sxs-lookup"><span data-stu-id="056d0-118">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="056d0-119">''<xref:System.ServiceModel.Channels.ChannelListenerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="056d0-119">The``<xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="056d0-120">Bu temel durum yönetimini mvc'deki.</span><span class="sxs-lookup"><span data-stu-id="056d0-120">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="056d0-121">Aşağıdaki tartışma temel aldığı [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="056d0-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="056d0-122">Kanal fabrikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="056d0-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="056d0-123">`UdpChannelFactory` Türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="056d0-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="056d0-124">Örnek geçersiz kılmaları <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümü erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="056d0-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="056d0-125">Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> bizim örneğini kesmeden <xref:System.ServiceModel.Channels.BufferManager> zaman durum makinesinin geçer.</span><span class="sxs-lookup"><span data-stu-id="056d0-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="056d0-126">UDP çıktı kanalı</span><span class="sxs-lookup"><span data-stu-id="056d0-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="056d0-127">`UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="056d0-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="056d0-128">Oluşturucu bağımsız değişkenleri doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesne temel alarak <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="056d0-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="056d0-129">Geçersiz kılma <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> için ileti göndermek için kullanılan bir yuva oluşturur <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="056d0-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 <span data-ttu-id="056d0-130">Kanal düzgün biçimde veya ungracefully kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="056d0-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="056d0-131">Kanal düzgün biçimde kapalıysa yuva kapatılır ve taban sınıfı için bir çağrı yapılır `OnClose` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="056d0-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="056d0-132">Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlendi.</span><span class="sxs-lookup"><span data-stu-id="056d0-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="056d0-133">Uygulama `Send()` ve `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="056d0-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="056d0-134">Bu iki ana bölüme parçalara ayırır.</span><span class="sxs-lookup"><span data-stu-id="056d0-134">This breaks down into two main sections.</span></span> <span data-ttu-id="056d0-135">İlk iletinin bir bayt dizisine sıralayın:</span><span class="sxs-lookup"><span data-stu-id="056d0-135">First serialize the message into a byte array:</span></span>  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="056d0-136">Ardından kablo sonuç verileri gönder:</span><span class="sxs-lookup"><span data-stu-id="056d0-136">Then send the resulting data on the wire:</span></span>  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="056d0-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="056d0-137">See Also</span></span>  
 [<span data-ttu-id="056d0-138">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="056d0-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)
