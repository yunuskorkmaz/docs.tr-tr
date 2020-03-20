---
title: 'İstemci: Kanal Fabrikaları ve Kanallar'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185688"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="6f489-102">İstemci: Kanal Fabrikaları ve Kanallar</span><span class="sxs-lookup"><span data-stu-id="6f489-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="6f489-103">Bu konu kanal fabrikaları ve kanalların oluşturulması nı tartışır.</span><span class="sxs-lookup"><span data-stu-id="6f489-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="6f489-104">Kanal Fabrikaları ve Kanallar</span><span class="sxs-lookup"><span data-stu-id="6f489-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="6f489-105">Kanal fabrikaları kanal oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="6f489-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="6f489-106">Kanal fabrikaları tarafından oluşturulan kanallar ileti göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f489-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="6f489-107">Bu kanallar, yukarıdaki katmandan iletiyi almak, gerekli olan işlemleri gerçekleştirmek ve ardından mesajı aşağıdaki katmana göndermekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="6f489-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="6f489-108">Aşağıdaki grafik bu işlemi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6f489-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="6f489-109">![Müşteri Fabrikaları ve Kanalları](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="6f489-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="6f489-110">Kanal fabrikası kanallar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f489-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="6f489-111">Kapandığında, kanal fabrikaları oluşturmuşve henüz kapatılmayan kanalların kapatılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="6f489-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="6f489-112">Bir kanal dinleyicisi kapatıldığında, yalnızca yeni kanalları kabul etmeyi durdurur, ancak ileti almaya devam edebilmeleri için varolan kanalları açık bırakır, çünkü modelin burada asimetrik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f489-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="6f489-113">WCF bu işlem için taban sınıf yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f489-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="6f489-114">(Bu konuda tartışılan kanal yardımcı sınıflarının diyagramı için [Kanal Modeline Genel Bakış](channel-model-overview.md)bölümüne bakın.)</span><span class="sxs-lookup"><span data-stu-id="6f489-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="6f489-115">Sınıf, <xref:System.ServiceModel.Channels.CommunicationObject> <xref:System.ServiceModel.ICommunicationObject> [Gelişen Kanallar'ın](developing-channels.md)2.</span><span class="sxs-lookup"><span data-stu-id="6f489-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="6f489-116">Sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> uygular <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir taban <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>sınıfı sağlar ve.</span><span class="sxs-lookup"><span data-stu-id="6f489-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6f489-117">Sınıf, <xref:System.ServiceModel.Channels.ChannelManagerBase> uygulayan bir <xref:System.ServiceModel.Channels.ChannelBase>taban sınıf olan ile <xref:System.ServiceModel.Channels.IChannel>birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="6f489-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="6f489-118">Sınıf, <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` aşırı yüklemeleri tek bir `OnCreateChannel` soyut yöntemde uygular ve birleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f489-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="6f489-119">Sınıf <xref:System.ServiceModel.Channels.ChannelListenerBase> uygular. <xref:System.ServiceModel.Channels.IChannelListener></span><span class="sxs-lookup"><span data-stu-id="6f489-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="6f489-120">Temel devlet yönetimini hallediyor.</span><span class="sxs-lookup"><span data-stu-id="6f489-120">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="6f489-121">Aşağıdaki tartışma [Transport: UDP](../samples/transport-udp.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f489-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="6f489-122">Kanal Fabrikası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f489-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="6f489-123"><xref:System.ServiceModel.Channels.ChannelFactoryBase>Türetilmiştir. `UdpChannelFactory`</span><span class="sxs-lookup"><span data-stu-id="6f489-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="6f489-124">Örnek, ileti <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> kodlayıcısının ileti sürümüne erişim sağlamak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6f489-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="6f489-125">Örnek aynı zamanda <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> durum makine <xref:System.ServiceModel.Channels.BufferManager> geçişleri bizim örnek yıkmak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6f489-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="6f489-126">UDP Çıkış Kanalı</span><span class="sxs-lookup"><span data-stu-id="6f489-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="6f489-127">Uygular `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="6f489-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="6f489-128">Oluşturucu bağımsız değişkenleri doğrular ve <xref:System.Net.EndPoint> geçirilene <xref:System.ServiceModel.EndpointAddress> göre bir hedef nesnesi inşa eder.</span><span class="sxs-lookup"><span data-stu-id="6f489-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="6f489-129">Geçersiz kılma, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> bu <xref:System.Net.EndPoint>ileti göndermek için kullanılan bir soket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6f489-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="6f489-130">Kanal zarif veya zarif bir şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f489-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="6f489-131">Kanal incelikle kapatılırsa soket kapatılır ve taban sınıf `OnClose` yöntemine çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="6f489-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="6f489-132">Bu bir özel durum oluşturursa, altyapı kanalının temizlenmesini sağlamak için çağırır. `Abort`</span><span class="sxs-lookup"><span data-stu-id="6f489-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="6f489-133">Uygula `Send()` `BeginSend()` / `EndSend()`ve .</span><span class="sxs-lookup"><span data-stu-id="6f489-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="6f489-134">Bu iki ana bölüme ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6f489-134">This breaks down into two main sections.</span></span> <span data-ttu-id="6f489-135">Önce iletiyi bayt dizilimi halinde serihale getirin:</span><span class="sxs-lookup"><span data-stu-id="6f489-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="6f489-136">Ardından, elde edilen verileri kabloya gönderin:</span><span class="sxs-lookup"><span data-stu-id="6f489-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f489-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f489-137">See also</span></span>

- [<span data-ttu-id="6f489-138">Geliştirme Kanalları</span><span class="sxs-lookup"><span data-stu-id="6f489-138">Developing Channels</span></span>](developing-channels.md)
