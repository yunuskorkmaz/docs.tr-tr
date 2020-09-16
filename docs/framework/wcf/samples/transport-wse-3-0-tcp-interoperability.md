---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: f61d5037af0be6579d5110152ca070bec586fe87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558972"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik
WVA3,0 TCP birlikte çalışabilirlik aktarım örneği, bir TCP çift yönlü oturumunun özel Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir. Ayrıca, mevcut dağıtılan sistemlerle kablo üzerinde arabirim sağlamak için kanal katmanının genişletilebilirliğini nasıl kullanabileceğinizi gösterir. Aşağıdaki adımlarda, bu özel WCF taşımanın nasıl oluşturulacağı gösterilmektedir:  
  
1. Bir TCP yuvasından başlayarak, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ileti sınırlarını belirtmek IÇIN DIME Çerçeveleme kullanan istemci ve sunucu uygulamaları oluşturun.  
  
2. WSE TCP hizmetine bağlanan ve istemci s üzerinden çerçeveli iletiler gönderen bir kanal fabrikası oluşturun <xref:System.ServiceModel.Channels.IDuplexSessionChannel> .  
  
3. Gelen TCP bağlantılarını kabul etmek ve karşılık gelen kanalları oluşturmak için bir kanal dinleyicisi oluşturun.  
  
4. Ağa özgü özel durumların, uygun türetilmiş sınıfına normalleştirildiğinden emin olun <xref:System.ServiceModel.CommunicationException> .  
  
5. Özel aktarımı bir kanal yığınına ekleyen bir bağlama öğesi ekleyin. Daha fazla bilgi için bkz. [bağlama öğesi ekleme].  
  
## <a name="creating-iduplexsessionchannel"></a>IDuplexSessionChannel oluşturma  
 WVA3,0 TCP birlikte çalışabilirlik aktarımını yazmanın ilk adımı <xref:System.ServiceModel.Channels.IDuplexSessionChannel> bir üzerinde uygulamasının bir uygulamasını oluşturmaktır <xref:System.Net.Sockets.Socket> . `WseTcpDuplexSessionChannel` türetiliyor <xref:System.ServiceModel.Channels.ChannelBase> . İleti gönderme mantığı iki ana parçadan oluşur: (1) iletiyi bayt olarak kodlama ve (2) bu baytları çerçevelendirme ve hatta gönderme.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ayrıca, Send () çağrılarının IDuplexSessionChannel sıra garantisi koruması ve temel alınan yuvaya yapılan çağrıların doğru şekilde eşitlenmesi için bir kilit alınır.  
  
 `WseTcpDuplexSessionChannel`<xref:System.ServiceModel.Channels.MessageEncoder> <xref:System.ServiceModel.Channels.Message> , Byte [] öğesine ve öğesinden çevirmek için bir kullanır. Bir taşıma işlemi olduğundan, `WseTcpDuplexSessionChannel` kanalın yapılandırıldığı uzak adresi uygulamaktan de sorumludur. `EncodeMessage` Bu dönüştürme için mantığı kapsüller.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Bayt olarak <xref:System.ServiceModel.Channels.Message> kodlandıktan sonra, bu, hatta iletime aktarılmalıdır. Bu, ileti sınırlarını tanımlamak için bir sistem gerektirir. WVA3,0, çerçeveleme protokolü olarak bir [DIME](/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) sürümü kullanır. `WriteData` bir Byte [] öğesini DıME kayıt kümesine kaydırmak için çerçeveleme mantığını kapsüller.  
  
 İleti alma mantığı benzerdir. Ana karmaşıklık, bir yuva okugusunun istenenden daha az bayt döndürebileceğinden olguyu işliyor. Bir ileti almak için, `WseTcpDuplexSessionChannel` baytları tel dışı okur, DIME çerçeveleme kodunu çözer ve ardından ' <xref:System.ServiceModel.Channels.MessageEncoder> a Byte [] öğesini ' a açmak için kullanır <xref:System.ServiceModel.Channels.Message> .  
  
 Taban, `WseTcpDuplexSessionChannel` bağlı bir yuva aldığını varsayar. Temel sınıf, yuva kapatılmasını işler. Yuva kapanışına sahip arabirime üç yer vardır:  
  
- OnAbort--yuvayı düzgün şekilde kapatın (keskin kapatma).  
  
- [Begin] kapat sayfasında, yuvayı düzgün şekilde kapatın (geçici kapatma).  
  
- oturumuna. CloseOutputSession--giden veri akışını (yarım kapanış) kapatın.  
  
## <a name="channel-factory"></a>Kanal Fabrikası  
 TCP aktarımını yazarken bir sonraki adım, <xref:System.ServiceModel.Channels.IChannelFactory> İstemci kanalları için bir uygulama oluşturmaktır.  
  
- `WseTcpChannelFactory`türetiliyor <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel> . İstemci kanalları oluşturmak için geçersiz kılan bir fabrikadır `OnCreateChannel` .  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel``WseTcpDuplexSessionChannel`BIR TCP sunucusuna zamanında bağlanmak için temel mantığı ekler `channel.Open` . İlk olarak, aşağıdaki kodda gösterildiği gibi, ana bilgisayar adı bir IP adresine çözümlenir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Ardından, ana bilgisayar adı aşağıdaki kodda gösterildiği gibi bir döngüdeki ilk kullanılabilir IP adresine bağlanır.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- Kanal sözleşmesinin bir parçası olarak, içindeki gibi tüm etki alanına özgü özel durumlar sarmalanır `SocketException` <xref:System.ServiceModel.CommunicationException> .  
  
## <a name="channel-listener"></a>Kanal dinleyicisi  
 TCP aktarımını yazarken bir sonraki adım, <xref:System.ServiceModel.Channels.IChannelListener> sunucu kanallarını kabul etmek için bir uygulama oluşturmaktır.  
  
- `WseTcpChannelListener`<xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> dinleme yuvasının ömrünü denetlemek Için [BEGIN] Open ve [BEGIN] Close üzerinde bulunan ve geçersiz kılmalar. OnOpen 'de IP_ANY dinlemek için bir yuva oluşturulur. Daha gelişmiş uygulamalar, IPv6 'yı da dinlemek için ikinci bir yuva oluşturabilir. Ayrıca, IP adresinin ana bilgisayar adı 'nda belirtilmesine izin verebilir.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Yeni bir yuva kabul edildiğinde, bu yuvada bir sunucu kanalı başlatılır. Tüm giriş ve çıkış Taban sınıfında zaten uygulanmış olduğundan, bu kanal yuvayı başlatmaktan sorumludur.  
  
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  
 Fabrikalar ve kanallar oluşturuldığına göre, bir bağlama yoluyla ServiceModel çalışma zamanına gösterilmeleri gerekir. Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur. Yığındaki her öğe bir Binding öğesi tarafından temsil edilir.  
  
 Örnekte, bağlama öğesi `WseTcpTransportBindingElement` öğesinden türetilir <xref:System.ServiceModel.Channels.TransportBindingElement> . <xref:System.ServiceModel.Channels.IDuplexSessionChannel>Bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri destekler ve geçersiz kılar.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ayrıca, `BindingElement` klonımızın (WSE. TCP) kopyalanması ve döndürülmesi için de üye içerir.  
  
## <a name="the-wse-tcp-test-console"></a>Wo TCP test konsolu  
 Bu örnek taşımanın kullanımı için test kodu TestCode.cs içinde bulunabilir. Aşağıdaki yönergelerde Wo örneğinin nasıl ayarlanacağı gösterilmektedir `TcpSyncStockService` .  
  
 Test kodu, kodlama olarak ve taşıma olarak MTOM 'yi kullanan özel bir bağlama oluşturur `WseTcpTransport` . Ayrıca, aşağıdaki kodda gösterildiği gibi, AddressingVersion değerini WVA3,0 ile uyumlu olacak şekilde ayarlar.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 İki testten oluşur; bir test, WVA3,0 WSDL 'den oluşturulan kodu kullanarak türü belirtilmiş bir istemciyi ayarlar. İkinci test, doğrudan kanal API 'lerinin üzerine ileti göndererek hem istemci hem de sunucu olarak WCF 'yi kullanır.  
  
 Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.  
  
 İstemci:  
  
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
  
 Sunucu:  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma  
  
1. Bu örneği çalıştırmak için, [Microsoft .net Için Web Hizmetleri geliştirmeleri (WVAS) 3,0](https://www.microsoft.com/download/details.aspx?id=14089) ve wvas `TcpSyncStockService` örneği yüklü olmalıdır.
  
> [!NOTE]
> WVA3,0, Windows Server 2008 ' de desteklenmediğinden, `TcpSyncStockService` örneği bu işletim sistemine yükleyemez veya çalıştıramazsınız.  
  
1. Örneği yükledikten sonra şunları `TcpSyncStockService` yapın:  
  
    1. `TcpSyncStockService`Visual Studio 'da açın. (TcpSyncStockService örneği WVA3,0 ile yüklenir. Bu örnek kodunun bir parçası değildir.)  
  
    2. StockService projesini başlangıç projesi olarak ayarlayın.  
  
    3. StockService projesinde StockService.cs ' i açın ve sınıfındaki [Policy] özniteliğini not edin `StockService` . Bu, örnekten güvenliği devre dışı bırakır. WCF, WKEN 3,0 güvenli uç noktaları ile birlikte çalışabilirken, bu örneğin özel TCP taşımasına odaklanmasını sağlamak için güvenlik devre dışı bırakılır.  
  
    4. Başlatmak için F5 tuşuna basın `TcpSyncStockService` . Hizmet yeni bir konsol penceresinde başlatılır.  
  
    5. Bu TCP aktarma örneğini Visual Studio 'da açın.  
  
    6. TestCode.cs içindeki "hostname" değişkenini çalıştıran makine adıyla eşleşecek şekilde güncelleştirin `TcpSyncStockService` .  
  
    7. TCP Aktarım örneğini başlatmak için F5 tuşuna basın.  
  
    8. TCP Aktarım sınama istemcisi yeni bir konsolda başlatılır. İstemci, hizmetten stok tekliflerini ister ve sonra sonuçları konsol penceresinde görüntüler.
