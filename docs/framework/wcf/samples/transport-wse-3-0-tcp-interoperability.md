---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 510d523cea78aa16a16adc8572c839e95059c068
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="8ff0a-102">Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="8ff0a-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="8ff0a-103">WSE 3.0 TCP birlikte çalışabilirlik aktarım örnek TCP çift yönlü oturum özel olarak uygulamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] taşıma.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="8ff0a-104">Kanal katmanını genişletilebilirlik arabirimine varolan dağıtılan sistemleriyle kablo üzerinden nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="8ff0a-105">Aşağıdaki adımlar, bu özel nasıl oluşturulacağını gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] taşıma:</span><span class="sxs-lookup"><span data-stu-id="8ff0a-105">The following steps show how to build this custom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport:</span></span>  
  
1.  <span data-ttu-id="8ff0a-106">Bir TCP yuvası ile başlayarak, istemci ve sunucu uygulamaları oluşturma <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , DIME çerçeveleme ileti sınırlarını tanımlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="8ff0a-107">WSE TCP hizmetine bağlanır ve istemci Çerçeveli iletileri gönderen bir kanal fabrikası oluşturma <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="8ff0a-108">Gelen TCP bağlantılarını kabul etmek ve karşılık gelen kanalları üretmek için bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="8ff0a-109">Ağa özgü özel durumlar için uygun olan türetilmiş sınıf normalleştirilmiş emin olun <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="8ff0a-110">Bir kanal yığınına özel taşıma ekler bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="8ff0a-111">[Bağlama öğesi ekleme] daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="8ff0a-112">Da IDuplexSessionChannel öğelerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ff0a-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="8ff0a-113">WSE 3.0 TCP birlikte çalışabilirlik aktarım yazma ilk adımı uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IDuplexSessionChannel> üstünde bir <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="8ff0a-114">`WseTcpDuplexSessionChannel` türetilen <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="8ff0a-115">Bir ileti gönderme mantığı iki ana parçalarını oluşur: (1) bayt sayısı, (2) bu bayt çerçeveleme ve kablo göndererek içine iletinin kodlaması.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="8ff0a-116">Ayrıca, bir kilit böylece Send() çağrıları da IDuplexSessionChannel öğelerini sıralı garantisi korumak ve temel yuva çağrıları doğru eşitlenmesi alınır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="8ff0a-117">`WseTcpDuplexSessionChannel` kullanan bir <xref:System.ServiceModel.Channels.MessageEncoder> çevirme için bir <xref:System.ServiceModel.Channels.Message> byte [] gelen ve giden.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="8ff0a-118">Bir taşıma olduğundan `WseTcpDuplexSessionChannel` ayrıca kanalı ile yapılandırılmış uzak adres uygulamak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="8ff0a-119">`EncodeMessage` Bu dönüştürme için mantığı yalıtır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="8ff0a-120">Bir kez <xref:System.ServiceModel.Channels.Message> kodlanır baytlara, onu kablo aktarılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="8ff0a-121">Bu ileti sınırlarını tanımlamak için bir sistem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="8ff0a-122">WSE 3.0 kullanan bir sürümünü [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) çerçeveleme protokol olarak.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-122">WSE 3.0 uses a version of [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="8ff0a-123">`WriteData` byte [] DIME kayıt kümesine sarmalamak için çerçeveleme mantığı yalıtır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="8ff0a-124">İletileri almak için mantığı çok benzer.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="8ff0a-125">Ana karmaşıklık okuma yuva istenenden daha az bayt döndürebilir olgu işliyor.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="8ff0a-126">Bir ileti alacak `WseTcpDuplexSessionChannel` kablo kapalı bayt okur, DIME çerçeveleme kodunu çözer ve ardından kullanır <xref:System.ServiceModel.Channels.MessageEncoder> kapatma içine byte [] için bir <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="8ff0a-127">Temel `WseTcpDuplexSessionChannel` bağlı bir yuva aldığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="8ff0a-128">Taban sınıfı yuva kapatma işler.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="8ff0a-129">Yuva kapatılması ile arabirim üç yerde vardır:</span><span class="sxs-lookup"><span data-stu-id="8ff0a-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="8ff0a-130">OnAbort--yuva ungracefully kapatın (sabit Kapat).</span><span class="sxs-lookup"><span data-stu-id="8ff0a-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="8ff0a-131">[Başlangıç üzerinde] Kapat--yuva düzgün biçimde kapatılamadı (yumuşak Kapat).</span><span class="sxs-lookup"><span data-stu-id="8ff0a-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="8ff0a-132">oturumu. CloseOutputSession--kapatma giden veri akışı (yarım Kapat).</span><span class="sxs-lookup"><span data-stu-id="8ff0a-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="8ff0a-133">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="8ff0a-133">Channel Factory</span></span>  
 <span data-ttu-id="8ff0a-134">TCP taşıma yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> istemci kanalları.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="8ff0a-135">`WseTcpChannelFactory` türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<da IDuplexSessionChannel öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="8ff0a-136">Geçersiz kılan bir Fabrika olduğu `OnCreateChannel` istemci kanallar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="8ff0a-137">`ClientWseTcpDuplexSessionChannel` temel mantığı ekler `WseTcpDuplexSessionChannel` bir TCP sunucusuna bağlanmak için `channel.Open` zaman.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="8ff0a-138">İlk ana bilgisayar adı aşağıdaki kodda gösterildiği gibi bir IP adresine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="8ff0a-139">Ardından ana bilgisayar adı bir döngü ilk kullanılabilir IP adresi aşağıdaki kodda gösterildiği gibi bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="8ff0a-140">Kanal sözleşmesinin bir parçası, etki alanına özgü özel durumlar, gibi sarılır `SocketException` içinde <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="8ff0a-141">Kanal dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="8ff0a-141">Channel Listener</span></span>  
 <span data-ttu-id="8ff0a-142">TCP taşıma yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelListener> sunucuya kanalların kabul etmek için.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="8ff0a-143">`WseTcpChannelListener` türetilen <xref:System.ServiceModel.Channels.ChannelListenerBase> \<da IDuplexSessionChannel öğelerini > ve geçersiz kılma [Başlangıç] ve [Başlangıç] açık üzerinde Dinleme yuvası ömrü kapatmak için denetim.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="8ff0a-144">Açıldığında, yuva IP_ANY üzerinde dinlenecek oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="8ff0a-145">Daha gelişmiş uygulamaları IPv6 için de dinlemek için ikinci bir yuva oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="8ff0a-146">Ayrıca ana bilgisayar adı belirtilmesi için IP adresi izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="8ff0a-147">Yeni bir yuva kabul edildiğinde, bir sunucu kanal bu yuvası ile başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="8ff0a-148">Tüm giriş ve çıkış zaten uygulanır taban sınıf içinde bu kanal yuva başlatmak için sorumlu olduğu şekilde.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="8ff0a-149">Bir bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="8ff0a-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="8ff0a-150">Fabrikaları ve kanallar oluşturulmuştur, bunlar bir bağlama aracılığıyla ServiceModel çalışma zamanına sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="8ff0a-151">Bir bağlama hizmeti adresi ile ilişkili iletişim yığını temsil eden bağlama öğelerinin bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="8ff0a-152">Yığındaki her öğe bir bağlama öğesi temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="8ff0a-153">Örnekte, bağlama öğedir `WseTcpTransportBindingElement`, den türetilen <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="8ff0a-154">Destekliyorsa <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ve bizim bağlama ile ilişkili oluşturucuları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="8ff0a-155">Kopyalama için de üyeleri içeren `BindingElement` ve bizim düzenini (wse.tcp) döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="8ff0a-156">WSE TCP sınama Konsolu</span><span class="sxs-lookup"><span data-stu-id="8ff0a-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="8ff0a-157">Bu örnek aktarım kullanmak için test kodu TestCode.cs içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="8ff0a-158">Aşağıdaki yönergeler WSE ayarlama Göster `TcpSyncStockService` örnek.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="8ff0a-159">MTOM kodlama olarak kullanan özel bağlama test kodunu oluşturur ve `WseTcpTransport` taşıma olarak.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="8ff0a-160">Ayrıca AddressingVersion değerini WSE 3.0 ile uyumlu olması için aşağıdaki kodda gösterildiği gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="8ff0a-161">İki sınamaları oluşur: WSE 3.0 WSDL oluşturulan kod kullanarak bir türü belirlenmiş istemci ayarlayan bir sınama.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="8ff0a-162">İkinci test kullanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem istemci hem de sunucunun kanal API'lerini doğrudan üstünde iletiler göndererek olarak.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-162">The second test uses [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="8ff0a-163">Örnek çalıştırırken aşağıdaki çıkış beklenir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="8ff0a-164">İstemci:</span><span class="sxs-lookup"><span data-stu-id="8ff0a-164">Client:</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff0a-165">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="8ff0a-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ff0a-166">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="8ff0a-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8ff0a-167">Bu örneği çalıştırmak için WSE 3.0 ve WSE sahip `TcpSyncStockService` yüklü örnek.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="8ff0a-168">İndirebilirsiniz [WSE 3.0 MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="8ff0a-168">You can download [WSE 3.0 from MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ff0a-169">WSE 3.0 üzerinde desteklenmediğinden [!INCLUDE[lserver](../../../../includes/lserver-md.md)], yükleme veya çalıştıramazsınız `TcpSyncStockService` bu işletim sisteminde örnek.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="8ff0a-170">Yüklemeden sonra `TcpSyncStockService` örnek, aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="8ff0a-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="8ff0a-171">Açık `TcpSyncStockService` Visual Studio (Not TcpSyncStockService örnek WSE 3.0 ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="8ff0a-172">Bu örnek 's kod parçası değil).</span><span class="sxs-lookup"><span data-stu-id="8ff0a-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="8ff0a-173">StockService projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="8ff0a-174">StockService.cs StockService proje ve yorum out [ilke] özniteliğini açmak `StockService` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="8ff0a-175">Bu güvenlik örnekten devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-175">This disables security from the sample.</span></span> <span data-ttu-id="8ff0a-176">Sırada [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 güvenli uç noktaları çalışabilirler, güvenlik üzerinde özel TCP taşıma odaklanmış Bu örnek tutmak için devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-176">While [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="8ff0a-177">Başlatmak için F5 tuşuna basın `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="8ff0a-178">Yeni bir konsol penceresi hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="8ff0a-179">Bu TCP taşıma örnek Visual Studio'da açın.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="8ff0a-180">Makine adı çalışan eşleşecek şekilde TestCode.cs "ana bilgisayar adı" değişkeninde güncelleştirme `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="8ff0a-181">TCP taşıma örneği başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="8ff0a-182">TCP taşıma test istemcisi yeni bir konsol içinde başlatır.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="8ff0a-183">İstemci Hizmeti'nden borsa bilgileri ister ve sonra sonuçları, konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff0a-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ff0a-184">See Also</span></span>
