---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 8166e1c378bc745eb8c9f37d6982642e754813cb
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544629"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="9c4a9-102">Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="9c4a9-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="9c4a9-103">WVA3,0 TCP birlikte çalışabilirlik aktarım örneği, bir TCP çift yönlü oturumunun özel Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="9c4a9-104">Ayrıca, mevcut dağıtılan sistemlerle kablo üzerinde arabirim sağlamak için kanal katmanının genişletilebilirliğini nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="9c4a9-105">Aşağıdaki adımlarda, bu özel WCF taşımanın nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9c4a9-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="9c4a9-106">Bir TCP yuvasından başlayarak, ileti sınırlarını belirtmek için DıME Çerçeveleme kullanan <xref:System.ServiceModel.Channels.IDuplexSessionChannel> istemci ve sunucu uygulamaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="9c4a9-107">WSE TCP hizmetine bağlanan ve istemci <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s üzerinden çerçeveli iletiler gönderen bir kanal fabrikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="9c4a9-108">Gelen TCP bağlantılarını kabul etmek ve karşılık gelen kanalları oluşturmak için bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="9c4a9-109">Ağa özgü tüm özel durumların <xref:System.ServiceModel.CommunicationException>uygun türetilmiş sınıfına normalleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="9c4a9-110">Özel aktarımı bir kanal yığınına ekleyen bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="9c4a9-111">Daha fazla bilgi için bkz. [bağlama öğesi ekleme].</span><span class="sxs-lookup"><span data-stu-id="9c4a9-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="9c4a9-112">IDuplexSessionChannel oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c4a9-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="9c4a9-113">WVA3,0 TCP birlikte çalışabilirlik aktarımını yazmanın ilk adımı, bir <xref:System.Net.Sockets.Socket><xref:System.ServiceModel.Channels.IDuplexSessionChannel> bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="9c4a9-114">`WseTcpDuplexSessionChannel` <xref:System.ServiceModel.Channels.ChannelBase>türetilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="9c4a9-115">İleti gönderme mantığı iki ana parçadan oluşur: (1) iletiyi bayt olarak kodlama ve (2) bu baytları çerçevelendirme ve hatta gönderme.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="9c4a9-116">Ayrıca, Send () çağrılarının IDuplexSessionChannel sıra garantisi koruması ve temel alınan yuvaya yapılan çağrıların doğru şekilde eşitlenmesi için bir kilit alınır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="9c4a9-117">`WseTcpDuplexSessionChannel`, Byte [] öğesine ve <xref:System.ServiceModel.Channels.Message> çevirmek için bir <xref:System.ServiceModel.Channels.MessageEncoder> kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="9c4a9-118">Bir taşıma olduğundan, kanalın yapılandırıldığı uzak adresi uygulamaktan de sorumlu `WseTcpDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="9c4a9-119">`EncodeMessage` bu dönüştürmenin mantığını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="9c4a9-120"><xref:System.ServiceModel.Channels.Message> bayt olarak kodlandıktan sonra, bu, hatta iletime aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="9c4a9-121">Bu, ileti sınırlarını tanımlamak için bir sistem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="9c4a9-122">WVA3,0, çerçeveleme protokolü olarak bir [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="9c4a9-123">`WriteData` Byte [] öğesini bir DıME kayıt kümesine sarmalamak için çerçeveleme mantığını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="9c4a9-124">İleti alma mantığı çok benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="9c4a9-125">Ana karmaşıklık, bir yuva okugusunun istenenden daha az bayt döndürebileceğinden olguyu işliyor.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="9c4a9-126">Bir ileti almak için `WseTcpDuplexSessionChannel` iletileri tel dışı okur, DıME çerçeveleme kodunu çözer ve sonra Byte [] ' ı bir <xref:System.ServiceModel.Channels.Message>açmak için <xref:System.ServiceModel.Channels.MessageEncoder> kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="9c4a9-127">Taban `WseTcpDuplexSessionChannel` bağlı bir yuva aldığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="9c4a9-128">Temel sınıf, yuva kapatılmasını işler.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="9c4a9-129">Yuva kapanışına sahip arabirime üç yer vardır:</span><span class="sxs-lookup"><span data-stu-id="9c4a9-129">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="9c4a9-130">OnAbort--yuvayı düzgün şekilde kapatın (keskin kapatma).</span><span class="sxs-lookup"><span data-stu-id="9c4a9-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="9c4a9-131">[Begin] kapat sayfasında, yuvayı düzgün şekilde kapatın (geçici kapatma).</span><span class="sxs-lookup"><span data-stu-id="9c4a9-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="9c4a9-132">oturumuna. CloseOutputSession--giden veri akışını (yarım kapanış) kapatın.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="9c4a9-133">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="9c4a9-133">Channel Factory</span></span>  
 <span data-ttu-id="9c4a9-134">TCP aktarımını yazarken bir sonraki adım, istemci kanalları için <xref:System.ServiceModel.Channels.IChannelFactory> bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="9c4a9-135">`WseTcpChannelFactory`, <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel > türetilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="9c4a9-136">İstemci kanalları oluşturmak için `OnCreateChannel` geçersiz kılan bir fabrikadır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="9c4a9-137">`ClientWseTcpDuplexSessionChannel`, `channel.Open` zamanda bir TCP sunucusuna bağlanmak için temel `WseTcpDuplexSessionChannel` Logic ekler.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="9c4a9-138">İlk olarak, aşağıdaki kodda gösterildiği gibi, ana bilgisayar adı bir IP adresine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="9c4a9-139">Ardından, ana bilgisayar adı aşağıdaki kodda gösterildiği gibi bir döngüdeki ilk kullanılabilir IP adresine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="9c4a9-140">Kanal sözleşmesinin bir parçası olarak, <xref:System.ServiceModel.CommunicationException>`SocketException` gibi, etki alanına özgü özel durumlar sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="9c4a9-141">Kanal dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="9c4a9-141">Channel Listener</span></span>  
 <span data-ttu-id="9c4a9-142">TCP aktarımını yazarken bir sonraki adım, sunucu kanallarını kabul etmek için <xref:System.ServiceModel.Channels.IChannelListener> bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="9c4a9-143">`WseTcpChannelListener`, dinleme yuvasının ömrünü denetlemek için <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel > ve [Begin] açık ve [BEGIN] Close üzerinde geçersiz kılmalarla türetilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="9c4a9-144">OnOpen 'de IP_ANY dinlemek için bir yuva oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="9c4a9-145">Daha gelişmiş uygulamalar, IPv6 'yı da dinlemek için ikinci bir yuva oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="9c4a9-146">Ayrıca, IP adresinin ana bilgisayar adı 'nda belirtilmesine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="9c4a9-147">Yeni bir yuva kabul edildiğinde, bu yuvada bir sunucu kanalı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="9c4a9-148">Tüm giriş ve çıkış Taban sınıfında zaten uygulanmış olduğundan, bu kanal yuvayı başlatmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="9c4a9-149">Bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="9c4a9-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="9c4a9-150">Fabrikalar ve kanallar oluşturuldığına göre, bir bağlama yoluyla ServiceModel çalışma zamanına gösterilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="9c4a9-151">Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="9c4a9-152">Yığındaki her öğe bir Binding öğesi tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="9c4a9-153">Örnekte, bağlama öğesi, <xref:System.ServiceModel.Channels.TransportBindingElement>türetilen `WseTcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="9c4a9-154"><xref:System.ServiceModel.Channels.IDuplexSessionChannel> destekler ve bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="9c4a9-155">Ayrıca, `BindingElement` klonlamamız ve düzenimizi (WSE. TCP) döndürmek için de üye içerir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="9c4a9-156">Wo TCP test konsolu</span><span class="sxs-lookup"><span data-stu-id="9c4a9-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="9c4a9-157">Bu örnek taşımanın kullanımı için test kodu TestCode.cs içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="9c4a9-158">Aşağıdaki yönergelerde, WVA`TcpSyncStockService` örneğinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="9c4a9-159">Test kodu, kodlama olarak MTOM ve taşıma olarak `WseTcpTransport` bir özel bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="9c4a9-160">Ayrıca, aşağıdaki kodda gösterildiği gibi, AddressingVersion değerini WVA3,0 ile uyumlu olacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="9c4a9-161">İki testten oluşur; bir test, WVA3,0 WSDL 'den oluşturulan kodu kullanarak türü belirtilmiş bir istemciyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="9c4a9-162">İkinci test, doğrudan kanal API 'lerinin üzerine ileti göndererek hem istemci hem de sunucu olarak WCF 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="9c4a9-163">Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="9c4a9-164">İstemci:</span><span class="sxs-lookup"><span data-stu-id="9c4a9-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="9c4a9-165">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="9c4a9-165">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9c4a9-166">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9c4a9-166">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9c4a9-167">Bu örneği çalıştırmak için, wva3,0 ve wva`TcpSyncStockService` örneğinin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="9c4a9-168">[Wo 3,0 ' i MSDN 'den](https://go.microsoft.com/fwlink/?LinkId=95000)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c4a9-169">WVA3,0, Windows Server 2008 ' de desteklenmediğinden, bu işletim sistemine `TcpSyncStockService` örneğini yükleyemez veya çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-169">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="9c4a9-170">`TcpSyncStockService` örneğini yükledikten sonra şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="9c4a9-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="9c4a9-171">Visual Studio 'da `TcpSyncStockService` açın (TcpSyncStockService örneğinin WVA3,0 ile yüklendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="9c4a9-172">Bu örnek kodunun bir parçası değildir).</span><span class="sxs-lookup"><span data-stu-id="9c4a9-172">It is not part of this sample's code).</span></span>  
  
    2. <span data-ttu-id="9c4a9-173">StockService projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-173">Set the StockService project as the start up project.</span></span>  
  
    3. <span data-ttu-id="9c4a9-174">StockService projesinde StockService.cs ' i açın ve `StockService` sınıfında [Policy] özniteliğini not edin.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="9c4a9-175">Bu, örnekten güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-175">This disables security from the sample.</span></span> <span data-ttu-id="9c4a9-176">WCF, WKEN 3,0 güvenli uç noktaları ile birlikte çalışabilirken, bu örneğin özel TCP taşımasına odaklanmasını sağlamak için güvenlik devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="9c4a9-177">`TcpSyncStockService`başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="9c4a9-178">Hizmet yeni bir konsol penceresinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-178">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="9c4a9-179">Bu TCP aktarma örneğini Visual Studio 'da açın.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="9c4a9-180">TestCode.cs içindeki "hostname" değişkenini, `TcpSyncStockService`çalıştıran makine adıyla eşleşecek şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="9c4a9-181">TCP Aktarım örneğini başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="9c4a9-182">TCP Aktarım sınama istemcisi yeni bir konsolda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="9c4a9-183">İstemci, hizmetten stok tekliflerini ister ve sonra sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9c4a9-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
