---
description: 'Istemci: kanal fabrikaları ve kanallar hakkında daha fazla bilgi edinin'
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: b61c37743899b8ba74ec18cc84397e4521e7bde7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803041"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="53bce-103">İstemci: Kanal Fabrikaları ve Kanallar</span><span class="sxs-lookup"><span data-stu-id="53bce-103">Client: Channel Factories and Channels</span></span>

<span data-ttu-id="53bce-104">Bu konuda, kanal fabrikaları ve kanallarının oluşturulması ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53bce-104">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="53bce-105">Kanal Fabrikaları ve Kanallar</span><span class="sxs-lookup"><span data-stu-id="53bce-105">Channel Factories and Channels</span></span>  

 <span data-ttu-id="53bce-106">Kanal fabrikaları kanalların oluşturulmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="53bce-106">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="53bce-107">Kanal fabrikaları tarafından oluşturulan kanallar, ileti göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53bce-107">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="53bce-108">Bu kanallar, yukarıdaki katmandan ileti alma, gerekli her türlü işlemi gerçekleştirme ve sonra iletiyi aşağıdaki katmana gönderme sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="53bce-108">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="53bce-109">Aşağıdaki grafik bu süreci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="53bce-109">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="53bce-110">![İstemci fabrikaları ve kanallar](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="53bce-110">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="53bce-111">Kanal fabrikası kanallar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53bce-111">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="53bce-112">Kapalı olduğunda, kanal fabrikaları, henüz kapanmamış oluşturdukları kanalları kapatmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="53bce-112">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="53bce-113">Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanalları kabul etmeyi ve mevcut kanalları açık bırakır, böylece ileti almaya devam edebilmek için modelin burada asimetrik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="53bce-113">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="53bce-114">WCF bu işlem için temel sınıf yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="53bce-114">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="53bce-115">(Bu konuda tartışılan kanal Yardımcısı sınıflarının bir diyagramı için bkz. [Kanal modeline genel bakış](channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="53bce-115">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="53bce-116"><xref:System.ServiceModel.Channels.CommunicationObject>Sınıfı, <xref:System.ServiceModel.ICommunicationObject> [Kanal geliştirme](developing-channels.md)ve adım 2 ' de açıklanan durum makinesini uygular ve uygular.</span><span class="sxs-lookup"><span data-stu-id="53bce-116">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="53bce-117"><xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı, <xref:System.ServiceModel.Channels.CommunicationObject> ve için Birleşik bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="53bce-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="53bce-118"><xref:System.ServiceModel.Channels.ChannelManagerBase>Sınıfı ile birlikte çalışarak <xref:System.ServiceModel.Channels.ChannelBase> , uygulayan bir temel sınıf olan <xref:System.ServiceModel.Channels.IChannel> .</span><span class="sxs-lookup"><span data-stu-id="53bce-118">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="53bce-119"><xref:System.ServiceModel.Channels.ChannelFactoryBase>Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` yüklerini tek bir soyut yöntemde uygular ve birleştirir `OnCreateChannel` .</span><span class="sxs-lookup"><span data-stu-id="53bce-119">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="53bce-120"><xref:System.ServiceModel.Channels.ChannelListenerBase>Sınıfı uygular <xref:System.ServiceModel.Channels.IChannelListener> .</span><span class="sxs-lookup"><span data-stu-id="53bce-120">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="53bce-121">Temel durum yönetiminden çok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="53bce-121">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="53bce-122">Aşağıdaki tartışma, [taşıma: UDP](../samples/transport-udp.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="53bce-122">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="53bce-123">Kanal fabrikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="53bce-123">Creating a Channel Factory</span></span>  

 <span data-ttu-id="53bce-124">`UdpChannelFactory`Öğesinden türetilir <xref:System.ServiceModel.Channels.ChannelFactoryBase> .</span><span class="sxs-lookup"><span data-stu-id="53bce-124">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="53bce-125">Örnek, <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti kodlayıcının ileti sürümüne erişim sağlamak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="53bce-125">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="53bce-126">Örnek ayrıca <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> <xref:System.ServiceModel.Channels.BufferManager> durum makinesi geçişi sırasında örneğimizi kaldırmak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="53bce-126">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="53bce-127">UDP çıkış kanalı</span><span class="sxs-lookup"><span data-stu-id="53bce-127">The UDP Output Channel</span></span>  

 <span data-ttu-id="53bce-128">`UdpOutputChannel`Uygular <xref:System.ServiceModel.Channels.IOutputChannel> .</span><span class="sxs-lookup"><span data-stu-id="53bce-128">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="53bce-129">Oluşturucu bağımsız değişkenleri doğrular ve geçirilen öğesine bağlı olarak bir hedef <xref:System.Net.EndPoint> nesnesi oluşturur <xref:System.ServiceModel.EndpointAddress> .</span><span class="sxs-lookup"><span data-stu-id="53bce-129">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="53bce-130">Geçersiz kılma, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> Bu iletiye ileti göndermek için kullanılan bir yuva oluşturur <xref:System.Net.EndPoint> .</span><span class="sxs-lookup"><span data-stu-id="53bce-130">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="53bce-131">Kanal düzgün şekilde kapatılabilir veya düzgün şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="53bce-131">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="53bce-132">Kanal kapalıysa, yuva kapanır ve temel sınıf yöntemine bir çağrı yapılır `OnClose` .</span><span class="sxs-lookup"><span data-stu-id="53bce-132">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="53bce-133">Bu, bir özel durum oluşturursa, `Abort` kanalın temizlendiğinden emin olmak için altyapı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="53bce-133">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="53bce-134">`Send()`Ve uygulayın `BeginSend()` / `EndSend()` .</span><span class="sxs-lookup"><span data-stu-id="53bce-134">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="53bce-135">Bu, iki ana bölümde kesilir.</span><span class="sxs-lookup"><span data-stu-id="53bce-135">This breaks down into two main sections.</span></span> <span data-ttu-id="53bce-136">İlk olarak iletiyi bir bayt dizisine seri hale getirme:</span><span class="sxs-lookup"><span data-stu-id="53bce-136">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="53bce-137">Sonra elde edilen verileri tel gönderin:</span><span class="sxs-lookup"><span data-stu-id="53bce-137">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="53bce-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53bce-138">See also</span></span>

- [<span data-ttu-id="53bce-139">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="53bce-139">Developing Channels</span></span>](developing-channels.md)
