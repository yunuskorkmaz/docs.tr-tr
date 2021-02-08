---
description: 'Daha fazla bilgi edinin: taşıma: WVA3,0 TCP birlikte çalışabilirliği'
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 2e0a5927b8f16116dc07910970268ff6ec35f396
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798244"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="53a00-103">Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="53a00-103">Transport: WSE 3.0 TCP Interoperability</span></span>

<span data-ttu-id="53a00-104">WVA3,0 TCP birlikte çalışabilirlik aktarım örneği, bir TCP çift yönlü oturumunun özel Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="53a00-104">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="53a00-105">Ayrıca, mevcut dağıtılan sistemlerle kablo üzerinde arabirim sağlamak için kanal katmanının genişletilebilirliğini nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="53a00-105">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="53a00-106">Aşağıdaki adımlarda, bu özel WCF taşımanın nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="53a00-106">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="53a00-107">Bir TCP yuvasından başlayarak, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ileti sınırlarını belirtmek IÇIN DIME Çerçeveleme kullanan istemci ve sunucu uygulamaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="53a00-107">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="53a00-108">WSE TCP hizmetine bağlanan ve istemci s üzerinden çerçeveli iletiler gönderen bir kanal fabrikası oluşturun <xref:System.ServiceModel.Channels.IDuplexSessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="53a00-108">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="53a00-109">Gelen TCP bağlantılarını kabul etmek ve karşılık gelen kanalları oluşturmak için bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="53a00-109">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="53a00-110">Ağa özgü özel durumların, uygun türetilmiş sınıfına normalleştirildiğinden emin olun <xref:System.ServiceModel.CommunicationException> .</span><span class="sxs-lookup"><span data-stu-id="53a00-110">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="53a00-111">Özel aktarımı bir kanal yığınına ekleyen bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53a00-111">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="53a00-112">Daha fazla bilgi için bkz. [bağlama öğesi ekleme].</span><span class="sxs-lookup"><span data-stu-id="53a00-112">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="53a00-113">IDuplexSessionChannel oluşturma</span><span class="sxs-lookup"><span data-stu-id="53a00-113">Creating IDuplexSessionChannel</span></span>  

 <span data-ttu-id="53a00-114">WVA3,0 TCP birlikte çalışabilirlik aktarımını yazmanın ilk adımı <xref:System.ServiceModel.Channels.IDuplexSessionChannel> bir üzerinde uygulamasının bir uygulamasını oluşturmaktır <xref:System.Net.Sockets.Socket> .</span><span class="sxs-lookup"><span data-stu-id="53a00-114">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="53a00-115">`WseTcpDuplexSessionChannel` türetiliyor <xref:System.ServiceModel.Channels.ChannelBase> .</span><span class="sxs-lookup"><span data-stu-id="53a00-115">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="53a00-116">İleti gönderme mantığı iki ana parçadan oluşur: (1) iletiyi bayt olarak kodlama ve (2) bu baytları çerçevelendirme ve hatta gönderme.</span><span class="sxs-lookup"><span data-stu-id="53a00-116">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="53a00-117">Ayrıca, Send () çağrılarının IDuplexSessionChannel sıra garantisi koruması ve temel alınan yuvaya yapılan çağrıların doğru şekilde eşitlenmesi için bir kilit alınır.</span><span class="sxs-lookup"><span data-stu-id="53a00-117">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="53a00-118">`WseTcpDuplexSessionChannel`<xref:System.ServiceModel.Channels.MessageEncoder> <xref:System.ServiceModel.Channels.Message> , Byte [] öğesine ve öğesinden çevirmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="53a00-118">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="53a00-119">Bir taşıma işlemi olduğundan, `WseTcpDuplexSessionChannel` kanalın yapılandırıldığı uzak adresi uygulamaktan de sorumludur.</span><span class="sxs-lookup"><span data-stu-id="53a00-119">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="53a00-120">`EncodeMessage` Bu dönüştürme için mantığı kapsüller.</span><span class="sxs-lookup"><span data-stu-id="53a00-120">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="53a00-121">Bayt olarak <xref:System.ServiceModel.Channels.Message> kodlandıktan sonra, bu, hatta iletime aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53a00-121">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="53a00-122">Bu, ileti sınırlarını tanımlamak için bir sistem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="53a00-122">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="53a00-123">WVA3,0, çerçeveleme protokolü olarak bir [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="53a00-123">WSE 3.0 uses a version of [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) as its framing protocol.</span></span> <span data-ttu-id="53a00-124">`WriteData` bir Byte [] öğesini DıME kayıt kümesine kaydırmak için çerçeveleme mantığını kapsüller.</span><span class="sxs-lookup"><span data-stu-id="53a00-124">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="53a00-125">İleti alma mantığı benzerdir.</span><span class="sxs-lookup"><span data-stu-id="53a00-125">The logic for receiving messages is similar.</span></span> <span data-ttu-id="53a00-126">Ana karmaşıklık, bir yuva okugusunun istenenden daha az bayt döndürebileceğinden olguyu işliyor.</span><span class="sxs-lookup"><span data-stu-id="53a00-126">The main complexity is handling the fact that a socket read can return fewer bytes than were requested.</span></span> <span data-ttu-id="53a00-127">Bir ileti almak için, `WseTcpDuplexSessionChannel` baytları tel dışı okur, DIME çerçeveleme kodunu çözer ve ardından ' <xref:System.ServiceModel.Channels.MessageEncoder> a Byte [] öğesini ' a açmak için kullanır <xref:System.ServiceModel.Channels.Message> .</span><span class="sxs-lookup"><span data-stu-id="53a00-127">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="53a00-128">Taban, `WseTcpDuplexSessionChannel` bağlı bir yuva aldığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="53a00-128">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="53a00-129">Temel sınıf, yuva kapatılmasını işler.</span><span class="sxs-lookup"><span data-stu-id="53a00-129">The base class handles socket shutdown.</span></span> <span data-ttu-id="53a00-130">Yuva kapanışına sahip arabirime üç yer vardır:</span><span class="sxs-lookup"><span data-stu-id="53a00-130">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="53a00-131">OnAbort--yuvayı düzgün şekilde kapatın (keskin kapatma).</span><span class="sxs-lookup"><span data-stu-id="53a00-131">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="53a00-132">[Begin] kapat sayfasında, yuvayı düzgün şekilde kapatın (geçici kapatma).</span><span class="sxs-lookup"><span data-stu-id="53a00-132">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="53a00-133">oturumuna. CloseOutputSession--giden veri akışını (yarım kapanış) kapatın.</span><span class="sxs-lookup"><span data-stu-id="53a00-133">session.CloseOutputSession -- shut down the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="53a00-134">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="53a00-134">Channel Factory</span></span>  

 <span data-ttu-id="53a00-135">TCP aktarımını yazarken bir sonraki adım, <xref:System.ServiceModel.Channels.IChannelFactory> İstemci kanalları için bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="53a00-135">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="53a00-136">`WseTcpChannelFactory`türetiliyor <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel> .</span><span class="sxs-lookup"><span data-stu-id="53a00-136">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="53a00-137">İstemci kanalları oluşturmak için geçersiz kılan bir fabrikadır `OnCreateChannel` .</span><span class="sxs-lookup"><span data-stu-id="53a00-137">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="53a00-138">`ClientWseTcpDuplexSessionChannel``WseTcpDuplexSessionChannel`BIR TCP sunucusuna zamanında bağlanmak için temel mantığı ekler `channel.Open` .</span><span class="sxs-lookup"><span data-stu-id="53a00-138">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="53a00-139">İlk olarak, aşağıdaki kodda gösterildiği gibi, ana bilgisayar adı bir IP adresine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="53a00-139">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="53a00-140">Ardından, ana bilgisayar adı aşağıdaki kodda gösterildiği gibi bir döngüdeki ilk kullanılabilir IP adresine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="53a00-140">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="53a00-141">Kanal sözleşmesinin bir parçası olarak, içindeki gibi tüm etki alanına özgü özel durumlar sarmalanır `SocketException` <xref:System.ServiceModel.CommunicationException> .</span><span class="sxs-lookup"><span data-stu-id="53a00-141">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="53a00-142">Kanal dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="53a00-142">Channel Listener</span></span>  

 <span data-ttu-id="53a00-143">TCP aktarımını yazarken bir sonraki adım, <xref:System.ServiceModel.Channels.IChannelListener> sunucu kanallarını kabul etmek için bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="53a00-143">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="53a00-144">`WseTcpChannelListener`<xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> dinleme yuvasının ömrünü denetlemek Için [BEGIN] Open ve [BEGIN] Close üzerinde bulunan ve geçersiz kılmalar.</span><span class="sxs-lookup"><span data-stu-id="53a00-144">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="53a00-145">OnOpen 'de IP_ANY dinlemek için bir yuva oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53a00-145">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="53a00-146">Daha gelişmiş uygulamalar, IPv6 'yı da dinlemek için ikinci bir yuva oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="53a00-146">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="53a00-147">Ayrıca, IP adresinin ana bilgisayar adı 'nda belirtilmesine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="53a00-147">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="53a00-148">Yeni bir yuva kabul edildiğinde, bu yuvada bir sunucu kanalı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="53a00-148">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="53a00-149">Tüm giriş ve çıkış Taban sınıfında zaten uygulanmış olduğundan, bu kanal yuvayı başlatmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="53a00-149">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="53a00-150">Bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="53a00-150">Adding a Binding Element</span></span>  

 <span data-ttu-id="53a00-151">Fabrikalar ve kanallar oluşturuldığına göre, bir bağlama yoluyla ServiceModel çalışma zamanına gösterilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="53a00-151">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="53a00-152">Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="53a00-152">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="53a00-153">Yığındaki her öğe bir Binding öğesi tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="53a00-153">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="53a00-154">Örnekte, bağlama öğesi `WseTcpTransportBindingElement` öğesinden türetilir <xref:System.ServiceModel.Channels.TransportBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="53a00-154">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="53a00-155"><xref:System.ServiceModel.Channels.IDuplexSessionChannel>Bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri destekler ve geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="53a00-155">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="53a00-156">Ayrıca, `BindingElement` klonımızın (WSE. TCP) kopyalanması ve döndürülmesi için de üye içerir.</span><span class="sxs-lookup"><span data-stu-id="53a00-156">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="53a00-157">Wo TCP test konsolu</span><span class="sxs-lookup"><span data-stu-id="53a00-157">The WSE TCP Test Console</span></span>  

 <span data-ttu-id="53a00-158">Bu örnek taşımanın kullanımı için test kodu TestCode.cs içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="53a00-158">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="53a00-159">Aşağıdaki yönergelerde Wo örneğinin nasıl ayarlanacağı gösterilmektedir `TcpSyncStockService` .</span><span class="sxs-lookup"><span data-stu-id="53a00-159">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="53a00-160">Test kodu, kodlama olarak ve taşıma olarak MTOM 'yi kullanan özel bir bağlama oluşturur `WseTcpTransport` .</span><span class="sxs-lookup"><span data-stu-id="53a00-160">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="53a00-161">Ayrıca, aşağıdaki kodda gösterildiği gibi, AddressingVersion değerini WVA3,0 ile uyumlu olacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="53a00-161">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="53a00-162">İki testten oluşur; bir test, WVA3,0 WSDL 'den oluşturulan kodu kullanarak türü belirtilmiş bir istemciyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="53a00-162">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="53a00-163">İkinci test, doğrudan kanal API 'lerinin üzerine ileti göndererek hem istemci hem de sunucu olarak WCF 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="53a00-163">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="53a00-164">Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="53a00-164">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="53a00-165">İstemci:</span><span class="sxs-lookup"><span data-stu-id="53a00-165">Client:</span></span>  
  
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
  
 <span data-ttu-id="53a00-166">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="53a00-166">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="53a00-167">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53a00-167">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="53a00-168">Bu örneği çalıştırmak için, [Microsoft .net Için Web Hizmetleri geliştirmeleri (WVAS) 3,0](https://www.microsoft.com/download/details.aspx?id=14089) ve wvas `TcpSyncStockService` örneği yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53a00-168">To run this sample, you must have [Web Services Enhancements (WSE) 3.0 for Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) and the WSE `TcpSyncStockService` sample installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="53a00-169">WVA3,0, Windows Server 2008 ' de desteklenmediğinden, `TcpSyncStockService` örneği bu işletim sistemine yükleyemez veya çalıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="53a00-169">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="53a00-170">Örneği yükledikten sonra şunları `TcpSyncStockService` yapın:</span><span class="sxs-lookup"><span data-stu-id="53a00-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="53a00-171">`TcpSyncStockService`Visual Studio 'da açın.</span><span class="sxs-lookup"><span data-stu-id="53a00-171">Open the `TcpSyncStockService` in Visual Studio.</span></span> <span data-ttu-id="53a00-172">(TcpSyncStockService örneği WVA3,0 ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="53a00-172">(The TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="53a00-173">Bu örnek kodunun bir parçası değildir.)</span><span class="sxs-lookup"><span data-stu-id="53a00-173">It is not part of this sample's code.)</span></span>  
  
    2. <span data-ttu-id="53a00-174">StockService projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="53a00-174">Set the StockService project as the start-up project.</span></span>  
  
    3. <span data-ttu-id="53a00-175">StockService projesinde StockService.cs ' i açın ve sınıfındaki [Policy] özniteliğini not edin `StockService` .</span><span class="sxs-lookup"><span data-stu-id="53a00-175">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="53a00-176">Bu, örnekten güvenliği devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="53a00-176">This disables security from the sample.</span></span> <span data-ttu-id="53a00-177">WCF, WKEN 3,0 güvenli uç noktaları ile birlikte çalışabilirken, bu örneğin özel TCP taşımasına odaklanmasını sağlamak için güvenlik devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="53a00-177">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="53a00-178">Başlatmak için F5 tuşuna basın `TcpSyncStockService` .</span><span class="sxs-lookup"><span data-stu-id="53a00-178">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="53a00-179">Hizmet yeni bir konsol penceresinde başlatılır.</span><span class="sxs-lookup"><span data-stu-id="53a00-179">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="53a00-180">Bu TCP aktarma örneğini Visual Studio 'da açın.</span><span class="sxs-lookup"><span data-stu-id="53a00-180">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="53a00-181">TestCode.cs içindeki "hostname" değişkenini çalıştıran makine adıyla eşleşecek şekilde güncelleştirin `TcpSyncStockService` .</span><span class="sxs-lookup"><span data-stu-id="53a00-181">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="53a00-182">TCP Aktarım örneğini başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="53a00-182">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="53a00-183">TCP Aktarım sınama istemcisi yeni bir konsolda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="53a00-183">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="53a00-184">İstemci, hizmetten stok tekliflerini ister ve sonra sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="53a00-184">The client requests stock quotes from the service and then displays the results in its console window.</span></span>
