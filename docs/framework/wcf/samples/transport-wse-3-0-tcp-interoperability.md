---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 6541ddf322a2084601daf2f1271ac5c888073f8f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423868"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik
WVA3,0 TCP birlikte çalışabilirlik aktarım örneği, bir TCP çift yönlü oturumunun özel Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir. Ayrıca, mevcut dağıtılan sistemlerle kablo üzerinde arabirim sağlamak için kanal katmanının genişletilebilirliğini nasıl kullanabileceğinizi gösterir. Aşağıdaki adımlarda, bu özel WCF taşımanın nasıl oluşturulacağı gösterilmektedir:  
  
1. Bir TCP yuvasından başlayarak, ileti sınırlarını belirtmek için DıME Çerçeveleme kullanan <xref:System.ServiceModel.Channels.IDuplexSessionChannel> istemci ve sunucu uygulamaları oluşturun.  
  
2. WSE TCP hizmetine bağlanan ve istemci <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s üzerinden çerçeveli iletiler gönderen bir kanal fabrikası oluşturun.  
  
3. Gelen TCP bağlantılarını kabul etmek ve karşılık gelen kanalları oluşturmak için bir kanal dinleyicisi oluşturun.  
  
4. Ağa özgü tüm özel durumların <xref:System.ServiceModel.CommunicationException>uygun türetilmiş sınıfına normalleştirildiğinden emin olun.  
  
5. Özel aktarımı bir kanal yığınına ekleyen bir bağlama öğesi ekleyin. Daha fazla bilgi için bkz. [bağlama öğesi ekleme].  
  
## <a name="creating-iduplexsessionchannel"></a>IDuplexSessionChannel oluşturma  
 WVA3,0 TCP birlikte çalışabilirlik aktarımını yazmanın ilk adımı, bir <xref:System.Net.Sockets.Socket><xref:System.ServiceModel.Channels.IDuplexSessionChannel> bir uygulama oluşturmaktır. `WseTcpDuplexSessionChannel` <xref:System.ServiceModel.Channels.ChannelBase>türetilir. İleti gönderme mantığı iki ana parçadan oluşur: (1) iletiyi bayt olarak kodlama ve (2) bu baytları çerçevelendirme ve hatta gönderme.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ayrıca, Send () çağrılarının IDuplexSessionChannel sıra garantisi koruması ve temel alınan yuvaya yapılan çağrıların doğru şekilde eşitlenmesi için bir kilit alınır.  
  
 `WseTcpDuplexSessionChannel`, Byte [] öğesine ve <xref:System.ServiceModel.Channels.Message> çevirmek için bir <xref:System.ServiceModel.Channels.MessageEncoder> kullanır. Bir taşıma olduğundan, kanalın yapılandırıldığı uzak adresi uygulamaktan de sorumlu `WseTcpDuplexSessionChannel`. `EncodeMessage` bu dönüştürmenin mantığını kapsüller.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message> bayt olarak kodlandıktan sonra, bu, hatta iletime aktarılmalıdır. Bu, ileti sınırlarını tanımlamak için bir sistem gerektirir. WVA3,0, çerçeveleme protokolü olarak bir [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) sürümü kullanır. `WriteData` Byte [] öğesini bir DıME kayıt kümesine sarmalamak için çerçeveleme mantığını kapsüller.  
  
 İleti alma mantığı çok benzerdir. Ana karmaşıklık, bir yuva okugusunun istenenden daha az bayt döndürebileceğinden olguyu işliyor. Bir ileti almak için `WseTcpDuplexSessionChannel` iletileri tel dışı okur, DıME çerçeveleme kodunu çözer ve sonra Byte [] ' ı bir <xref:System.ServiceModel.Channels.Message>açmak için <xref:System.ServiceModel.Channels.MessageEncoder> kullanır.  
  
 Taban `WseTcpDuplexSessionChannel` bağlı bir yuva aldığını varsayar. Temel sınıf, yuva kapatılmasını işler. Yuva kapanışına sahip arabirime üç yer vardır:  
  
- OnAbort--yuvayı düzgün şekilde kapatın (keskin kapatma).  
  
- [Begin] kapat sayfasında, yuvayı düzgün şekilde kapatın (geçici kapatma).  
  
- oturumuna. CloseOutputSession--giden veri akışını (yarım kapanış) kapatın.  
  
## <a name="channel-factory"></a>Kanal Fabrikası  
 TCP aktarımını yazarken bir sonraki adım, istemci kanalları için <xref:System.ServiceModel.Channels.IChannelFactory> bir uygulama oluşturmaktır.  
  
- `WseTcpChannelFactory`, <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel > türetilir. İstemci kanalları oluşturmak için `OnCreateChannel` geçersiz kılan bir fabrikadır.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`, `channel.Open` zamanda bir TCP sunucusuna bağlanmak için temel `WseTcpDuplexSessionChannel` Logic ekler. İlk olarak, aşağıdaki kodda gösterildiği gibi, ana bilgisayar adı bir IP adresine çözümlenir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Ardından, ana bilgisayar adı aşağıdaki kodda gösterildiği gibi bir döngüdeki ilk kullanılabilir IP adresine bağlanır.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- Kanal sözleşmesinin bir parçası olarak, <xref:System.ServiceModel.CommunicationException>`SocketException` gibi, etki alanına özgü özel durumlar sarmalanır.  
  
## <a name="channel-listener"></a>Kanal dinleyicisi  
 TCP aktarımını yazarken bir sonraki adım, sunucu kanallarını kabul etmek için <xref:System.ServiceModel.Channels.IChannelListener> bir uygulama oluşturmaktır.  
  
- `WseTcpChannelListener`, dinleme yuvasının ömrünü denetlemek için <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel > ve [Begin] açık ve [BEGIN] Close üzerinde geçersiz kılmalarla türetilir. OnOpen 'de, IP_ANY üzerinde dinlemek için bir yuva oluşturulur. Daha gelişmiş uygulamalar, IPv6 'yı da dinlemek için ikinci bir yuva oluşturabilir. Ayrıca, IP adresinin ana bilgisayar adı 'nda belirtilmesine izin verebilir.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Yeni bir yuva kabul edildiğinde, bu yuvada bir sunucu kanalı başlatılır. Tüm giriş ve çıkış Taban sınıfında zaten uygulanmış olduğundan, bu kanal yuvayı başlatmaktan sorumludur.  
  
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  
 Fabrikalar ve kanallar oluşturuldığına göre, bir bağlama yoluyla ServiceModel çalışma zamanına gösterilmeleri gerekir. Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur. Yığındaki her öğe bir Binding öğesi tarafından temsil edilir.  
  
 Örnekte, bağlama öğesi, <xref:System.ServiceModel.Channels.TransportBindingElement>türetilen `WseTcpTransportBindingElement`. <xref:System.ServiceModel.Channels.IDuplexSessionChannel> destekler ve bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ayrıca, `BindingElement` klonlamamız ve düzenimizi (WSE. TCP) döndürmek için de üye içerir.  
  
## <a name="the-wse-tcp-test-console"></a>Wo TCP test konsolu  
 Bu örnek taşımanın kullanımı için test kodu TestCode.cs içinde bulunabilir. Aşağıdaki yönergelerde, WVA`TcpSyncStockService` örneğinin nasıl ayarlanacağı gösterilmektedir.  
  
 Test kodu, kodlama olarak MTOM ve taşıma olarak `WseTcpTransport` bir özel bağlama oluşturur. Ayrıca, aşağıdaki kodda gösterildiği gibi, AddressingVersion değerini WVA3,0 ile uyumlu olacak şekilde ayarlar.  
  
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
  
 Server  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Bu örneği çalıştırmak için, wva3,0 ve wva`TcpSyncStockService` örneğinin yüklü olması gerekir. [Wo 3,0 ' i MSDN 'den](https://go.microsoft.com/fwlink/?LinkId=95000)indirebilirsiniz.  
  
> [!NOTE]
> WVA3,0 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]desteklenmediğinden, bu işletim sistemine `TcpSyncStockService` örneğini yükleyemez veya çalıştıramazsınız.  
  
1. `TcpSyncStockService` örneğini yükledikten sonra şunları yapın:  
  
    1. Visual Studio 'da `TcpSyncStockService` açın (TcpSyncStockService örneğinin WVA3,0 ile yüklendiğini unutmayın. Bu örnek kodunun bir parçası değildir).  
  
    2. StockService projesini başlangıç projesi olarak ayarlayın.  
  
    3. StockService projesinde StockService.cs ' i açın ve `StockService` sınıfında [Policy] özniteliğini not edin. Bu, örnekten güvenliği devre dışı bırakır. WCF, WKEN 3,0 güvenli uç noktaları ile birlikte çalışabilirken, bu örneğin özel TCP taşımasına odaklanmasını sağlamak için güvenlik devre dışı bırakılır.  
  
    4. `TcpSyncStockService`başlatmak için F5 tuşuna basın. Hizmet yeni bir konsol penceresinde başlatılır.  
  
    5. Bu TCP aktarma örneğini Visual Studio 'da açın.  
  
    6. TestCode.cs içindeki "hostname" değişkenini, `TcpSyncStockService`çalıştıran makine adıyla eşleşecek şekilde güncelleştirin.  
  
    7. TCP Aktarım örneğini başlatmak için F5 tuşuna basın.  
  
    8. TCP Aktarım sınama istemcisi yeni bir konsolda başlatılır. İstemci, hizmetten stok tekliflerini ister ve sonra sonuçları konsol penceresinde görüntüler.  
