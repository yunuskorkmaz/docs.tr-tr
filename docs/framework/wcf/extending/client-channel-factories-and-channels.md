---
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3f045f56f7b73c5416e7a21a3afde29d22212d68
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182443"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="e9ee2-102">İstemci: Kanal Fabrikaları ve Kanallar</span><span class="sxs-lookup"><span data-stu-id="e9ee2-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="e9ee2-103">Bu konu, kanal fabrikaları ve kanallar oluşturulmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="e9ee2-104">Kanal fabrikaları ve kanallar</span><span class="sxs-lookup"><span data-stu-id="e9ee2-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="e9ee2-105">Kanal fabrikaları kanallar oluşturmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="e9ee2-106">Kanal fabrikaları tarafından oluşturulan Kanallar, ileti göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="e9ee2-107">Bu Kanallar, katmandan ileti alma, gerekli işlemleri gerçekleştirip ve ardından katmana ileti gönderilirken sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="e9ee2-108">Aşağıdaki grafikte, bu işlemi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="e9ee2-109">![İstemci fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="e9ee2-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="e9ee2-110">Kanal fabrikası kanalı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="e9ee2-111">Kapatıldığında, kanal fabrikaları henüz kapatılmadı oluşturdukları tüm kanalları kapatma için sorumlu olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="e9ee2-112">Bir kanal dinleyicisi kapalı olduğunda, yalnızca yeni kanallar ancak iletiler almaya devam edebilmesi için mevcut kanallar açın leaves kabul etme işlemini durdurur olduğundan model burada asimetrik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="e9ee2-113">WCF bu işlem için temel sınıfı Yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="e9ee2-114">(Bu konuda tartışılan kanal yardımcı sınıfları diyagramı için bkz: [kanal modeline genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="e9ee2-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="e9ee2-115"><xref:System.ServiceModel.Channels.CommunicationObject> Sınıfının Implements <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda açıklanan Durum makinesi uygular [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="e9ee2-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="e9ee2-116"><xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir temel sınıf için <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e9ee2-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
-   <span data-ttu-id="e9ee2-118"><xref:System.ServiceModel.Channels.ChannelFactoryBase> Sınıfının Implements <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` aşırı birine `OnCreateChannel` soyut yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
-   <span data-ttu-id="e9ee2-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfının Implements <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="e9ee2-120">Bu temel durum yönetimini üstlenir.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="e9ee2-121">Aşağıdaki tartışma temel aldığı [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="e9ee2-122">Kanal fabrikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9ee2-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="e9ee2-123">`UdpChannelFactory` Türetildiği <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="e9ee2-124">Örnek geçersiz kılmalar <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümüne erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="e9ee2-125">Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> bizim örneğini kaldırmak için <xref:System.ServiceModel.Channels.BufferManager> durum makinesinin zaman geçer.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="e9ee2-126">UDP Çıkış kanalı</span><span class="sxs-lookup"><span data-stu-id="e9ee2-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="e9ee2-127">`UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="e9ee2-128">Oluşturucu bağımsız değişkenlerini doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesnesini temel alan <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="e9ee2-129">Geçersiz kılmasını <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> için ileti göndermek için kullanılan bir yuva oluşturur <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="e9ee2-130">Kanal ungracefully ya da düzgün biçimde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="e9ee2-131">Kanal düzgün bir şekilde kapanırsa yuva kapatıldı ve temel sınıf için bir çağrı yapılır `OnClose` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="e9ee2-132">Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlenir.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="e9ee2-133">Uygulama `Send()` ve `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="e9ee2-134">Bu iki ana bölüme ayırır.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-134">This breaks down into two main sections.</span></span> <span data-ttu-id="e9ee2-135">İlk iletinin bir bayt dizisine okunamayacak seri hale getirme:</span><span class="sxs-lookup"><span data-stu-id="e9ee2-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="e9ee2-136">Sonra elde edilen veriler kablo gönderin:</span><span class="sxs-lookup"><span data-stu-id="e9ee2-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9ee2-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ee2-137">See Also</span></span>  
 [<span data-ttu-id="e9ee2-138">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="e9ee2-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)
