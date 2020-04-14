---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: f799f3b6968f31472acc7752846bab34351648db
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278905"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="77cbf-102">Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="77cbf-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="77cbf-103">WSE 3.0 TCP Birlikte Çalışabilirlik Taşıma örneği, özel bir Windows Communication Foundation (WCF) aktarımı olarak Bir TCP çift yönlü oturumun nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="77cbf-104">Ayrıca, kanal katmanının genişletilebilirliğini, varolan konuşlanmış sistemlerle kablo üzerinde arabirim yapmak için nasıl kullanabileceğinizi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="77cbf-105">Aşağıdaki adımlar, bu özel WCF aktarımını nasıl oluşturabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="77cbf-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="77cbf-106">Bir TCP soketiyle başlayarak, ileti <xref:System.ServiceModel.Channels.IDuplexSessionChannel> sınırlarını nida lamak için DIME Çerçeveleme'yi kullanan istemci ve sunucu uygulamalarını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="77cbf-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="77cbf-107">WSE TCP hizmetine bağlanan ve istemcinin <xref:System.ServiceModel.Channels.IDuplexSessionChannel>üzerinden çerçeveli iletiler gönderen bir kanal fabrikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="77cbf-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="77cbf-108">Gelen TCP bağlantılarını kabul etmek ve ilgili kanalları üretmek için bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="77cbf-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="77cbf-109">Ağa özgü özel özel durumların uygun türemiş sınıfa normalleştirildiğinden emin <xref:System.ServiceModel.CommunicationException>olun.</span><span class="sxs-lookup"><span data-stu-id="77cbf-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="77cbf-110">Kanal yığınına özel aktarım ekleyen bağlayıcı bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77cbf-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="77cbf-111">Daha fazla bilgi için bkz: [Bağlama Öğesi Ekleme].</span><span class="sxs-lookup"><span data-stu-id="77cbf-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="77cbf-112">IDuplexSessionChannel oluşturma</span><span class="sxs-lookup"><span data-stu-id="77cbf-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="77cbf-113">WSE 3.0 TCP Birlikte Çalışabilirlik Taşımacılığı'nı <xref:System.ServiceModel.Channels.IDuplexSessionChannel> yazmanın ilk adımı, <xref:System.Net.Sockets.Socket>bir .</span><span class="sxs-lookup"><span data-stu-id="77cbf-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="77cbf-114">`WseTcpDuplexSessionChannel`<xref:System.ServiceModel.Channels.ChannelBase>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="77cbf-115">İleti gönderme mantığı iki ana parçadan oluşur: (1) İletiyi baytlara kodlamak ve (2) bu baytları çerçeveleme ve tel üzerinde gönderme.</span><span class="sxs-lookup"><span data-stu-id="77cbf-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="77cbf-116">Buna ek olarak, Send() çağrılarının IDuplexSessionChannel sıralı garantisini koruması ve böylece alttaki sokete yapılan çağrıların doğru şekilde eşitlemesi için bir kilit alınır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="77cbf-117">`WseTcpDuplexSessionChannel`a <xref:System.ServiceModel.Channels.Message> <xref:System.ServiceModel.Channels.MessageEncoder> ve byte çevirmek için kullanır[].</span><span class="sxs-lookup"><span data-stu-id="77cbf-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="77cbf-118">Bu bir aktarım `WseTcpDuplexSessionChannel` olduğundan, kanalın birlikte yapılandırıldığı uzak adresi de uygulamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="77cbf-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="77cbf-119">`EncodeMessage`bu dönüştürme nin mantığını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="77cbf-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="77cbf-120"><xref:System.ServiceModel.Channels.Message> Baytlar halinde kodlandıktan sonra, tel üzerinde iletilmelidir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="77cbf-121">Bu, ileti sınırlarını tanımlamak için bir sistem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="77cbf-122">WSE 3.0 çerçeveleme protokolü olarak [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) bir sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-122">WSE 3.0 uses a version of [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) as its framing protocol.</span></span> <span data-ttu-id="77cbf-123">`WriteData`bir bayt[] dime kayıtları kümesine sarmak için çerçeveleme mantığını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="77cbf-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="77cbf-124">İleti alma mantığı benzer.</span><span class="sxs-lookup"><span data-stu-id="77cbf-124">The logic for receiving messages is similar.</span></span> <span data-ttu-id="77cbf-125">Ana karmaşıklık, bir soket okumasının istenenden daha az bayt döndürebildiği gerçeğini işlemektir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-125">The main complexity is handling the fact that a socket read can return fewer bytes than were requested.</span></span> <span data-ttu-id="77cbf-126">İleti almak için, `WseTcpDuplexSessionChannel` kablodan baytokur, DIME çerçevesini çözer ve <xref:System.ServiceModel.Channels.MessageEncoder> bayt[] bir <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="77cbf-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="77cbf-127">Taban, `WseTcpDuplexSessionChannel` bağlı bir soket aldığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="77cbf-128">Taban sınıf soket kapatma yı işler.</span><span class="sxs-lookup"><span data-stu-id="77cbf-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="77cbf-129">Soket kapatma ile arayüz oluşturan üç yer vardır:</span><span class="sxs-lookup"><span data-stu-id="77cbf-129">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="77cbf-130">OnAbort -- soketi nezaketsiz kapatın (sert yakın).</span><span class="sxs-lookup"><span data-stu-id="77cbf-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="77cbf-131">[Begin]Close -soketi incelikle kapatın (yumuşak yakın).</span><span class="sxs-lookup"><span data-stu-id="77cbf-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="77cbf-132">Oturum. CloseOutputSession -- giden veri akışını kapatın (yarı yakın).</span><span class="sxs-lookup"><span data-stu-id="77cbf-132">session.CloseOutputSession -- shut down the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="77cbf-133">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="77cbf-133">Channel Factory</span></span>  
 <span data-ttu-id="77cbf-134">TCP aktarımını yazarken bir sonraki adım, istemci kanalları için <xref:System.ServiceModel.Channels.IChannelFactory> bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="77cbf-135">`WseTcpChannelFactory`IDuplexSessionChannel> türetilmiştir. <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<</span><span class="sxs-lookup"><span data-stu-id="77cbf-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="77cbf-136">İstemci kanalları üretmek `OnCreateChannel` için geçersiz kılan bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="77cbf-137">`ClientWseTcpDuplexSessionChannel`zamanda bir TCP sunucusuna bağlanmak için tabanına `WseTcpDuplexSessionChannel` mantık ekler. `channel.Open`</span><span class="sxs-lookup"><span data-stu-id="77cbf-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="77cbf-138">Önce ana bilgisayar adı, aşağıdaki kodda gösterildiği gibi bir IP adresine çözülür.</span><span class="sxs-lookup"><span data-stu-id="77cbf-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="77cbf-139">Ardından, ana bilgisayar adı, aşağıdaki kodda gösterildiği gibi, bir döngüdeki ilk kullanılabilir IP adresine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="77cbf-140">Kanal sözleşmesinin bir parçası olarak, etki alanına özgü özel `SocketException` <xref:System.ServiceModel.CommunicationException>özel durumlar , 'deki gibi.</span><span class="sxs-lookup"><span data-stu-id="77cbf-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="77cbf-141">Kanal Dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="77cbf-141">Channel Listener</span></span>  
 <span data-ttu-id="77cbf-142">TCP aktarımını yazarken bir sonraki adım, sunucu kanallarını <xref:System.ServiceModel.Channels.IChannelListener> kabul etmek için bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="77cbf-143">`WseTcpChannelListener`iDuplexSessionChannel>'den <xref:System.ServiceModel.Channels.ChannelListenerBase> \<türetilmiştir ve dinleme soketinin ömrünü kontrol etmek için On[Begin]Open ve On[Begin]Close'u geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="77cbf-144">OnOpen'de, IP_ANY dinlemek için bir soket oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77cbf-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="77cbf-145">Daha gelişmiş uygulamalar da IPv6 dinlemek için ikinci bir soket oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77cbf-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="77cbf-146">Ayrıca IP adresinin ana bilgisayar adında belirtilmesine de izin verebilirler.</span><span class="sxs-lookup"><span data-stu-id="77cbf-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="77cbf-147">Yeni bir soket kabul edildiğinde, bu soketle bir sunucu kanalı açılır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="77cbf-148">Tüm giriş ve çıktı zaten taban sınıfta uygulanmıştır, bu nedenle bu kanal soketin başlatılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="77cbf-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="77cbf-149">Bağlama Öğesi Ekleme</span><span class="sxs-lookup"><span data-stu-id="77cbf-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="77cbf-150">Artık fabrikalar ve kanallar inşa edildiklerine göre, bir bağlama yoluyla ServiceModel çalışma süresine maruz kalmalıdırlar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="77cbf-151">Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğeleri topluluğudur.</span><span class="sxs-lookup"><span data-stu-id="77cbf-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="77cbf-152">Yığındaki her öğe bağlayıcı bir öğe yle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="77cbf-153">Örnekte, bağlama öğesi `WseTcpTransportBindingElement`, hangi türetilmiştir <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="77cbf-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="77cbf-154">Bizim <xref:System.ServiceModel.Channels.IDuplexSessionChannel> bağlama ile ilişkili fabrikalar oluşturmak için aşağıdaki yöntemleri destekler ve geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="77cbf-155">Ayrıca klonlama `BindingElement` ve düzeni (wse.tcp) iade üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="77cbf-156">WSE TCP Test Konsolu</span><span class="sxs-lookup"><span data-stu-id="77cbf-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="77cbf-157">Bu örnek aktarım ı kullanmak için test kodu TestCode.cs'da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="77cbf-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="77cbf-158">Aşağıdaki yönergeler WSE `TcpSyncStockService` örneğinin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="77cbf-159">Test kodu, kodlama ve `WseTcpTransport` aktarım olarak MTOM kullanan özel bir bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77cbf-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="77cbf-160">Ayrıca, aşağıdaki kodda gösterildiği gibi Adresleme Sürümü'nü WSE 3.0 ile uyumlu olacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="77cbf-161">İki testten oluşur- bir test WSE 3.0 WSDL oluşturulan kodu kullanarak bir yazılı istemci ayarlar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="77cbf-162">İkinci test, doğrudan kanal API'lerinin üstüne ileti göndererek WCF'yi hem istemci hem de sunucu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="77cbf-163">Örneği çalıştırırken, aşağıdaki çıktı bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="77cbf-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="77cbf-164">İstemci:</span><span class="sxs-lookup"><span data-stu-id="77cbf-164">Client:</span></span>  
  
```console  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="77cbf-165">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="77cbf-165">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="77cbf-166">Örneği ayarlama, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="77cbf-166">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="77cbf-167">Bu örneği çalıştırmak için [Microsoft .NET için Web Hizmetleri Geliştirmeleri (WSE) 3.0](https://www.microsoft.com/download/details.aspx?id=14089) ve WSE `TcpSyncStockService` örneğinin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-167">To run this sample, you must have [Web Services Enhancements (WSE) 3.0 for Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) and the WSE `TcpSyncStockService` sample installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="77cbf-168">WSE 3.0 Windows Server 2008'de desteklenmediği `TcpSyncStockService` için, örneği bu işletim sistemine yükleyemezsiniz veya çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="77cbf-168">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="77cbf-169">Örneği yükledikten `TcpSyncStockService` sonra aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="77cbf-169">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="77cbf-170">Visual `TcpSyncStockService` Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="77cbf-170">Open the `TcpSyncStockService` in Visual Studio.</span></span> <span data-ttu-id="77cbf-171">(TcpSyncStockService örneği WSE 3.0 ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-171">(The TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="77cbf-172">Bu, bu örneğin kodunun bir parçası değildir.)</span><span class="sxs-lookup"><span data-stu-id="77cbf-172">It is not part of this sample's code.)</span></span>  
  
    2. <span data-ttu-id="77cbf-173">StockService projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="77cbf-173">Set the StockService project as the start-up project.</span></span>  
  
    3. <span data-ttu-id="77cbf-174">StockService projesinde StockService.cs açın ve sınıfla ilgili [İlke] özniteliğini `StockService` yorumla.</span><span class="sxs-lookup"><span data-stu-id="77cbf-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="77cbf-175">Bu, örnekteki güvenliği devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="77cbf-175">This disables security from the sample.</span></span> <span data-ttu-id="77cbf-176">WCF WSE 3.0 güvenli uç noktaları ile birlikte çalışabilirken, bu örneği özel TCP taşımasına odaklamak için güvenlik devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="77cbf-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="77cbf-177">Başlatmak için F5 `TcpSyncStockService`tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="77cbf-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="77cbf-178">Hizmet yeni bir konsol penceresinde başlar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-178">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="77cbf-179">Bu TCP taşıma örneğini Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="77cbf-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="77cbf-180">"Hostname" değişkenini TestCode.cs'da çalıştıran `TcpSyncStockService`makine adıyla eşleştirmek için güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="77cbf-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="77cbf-181">TCP taşıma örneğini başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="77cbf-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="77cbf-182">TCP aktarım testi istemcisi yeni bir konsolda başlar.</span><span class="sxs-lookup"><span data-stu-id="77cbf-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="77cbf-183">İstemci hizmetten stok teklifleri ister ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77cbf-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
