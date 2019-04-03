---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 342c9c39eaa755363615dd83933cf00480e01c91
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842362"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik
WSE 3.0 TCP birlikte çalışabilirlik aktarım örnek bir TCP çift yönlü oturumu özel bir Windows Communication Foundation (WCF) aktarım olarak uygulamak nasıl gösterir. Kanal katmanını genişletilmesinde arabirimine dağıtılan var olan sistemlerle kablo üzerinden nasıl kullanabileceğinizi gösterir. Aşağıdaki adımlar bu özel WCF taşıma yapı işlemini gösterir:  
  
1.  Bir TCP yuva ile başlayarak, istemci ve sunucu uygulamaları oluşturma <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ayıklanmış çerçeveleme DIME iletisi sınırları ayırmak için.  
  
2.  WSE TCP hizmetine bağlanır ve istemci üzerinde Çerçeveli iletileri gönderen bir kanal fabrikası oluşturma <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Gelen TCP bağlantılarını kabul etmek ve karşılık gelen bir kanal oluşturmak için bir kanal dinleyicisi oluşturun.  
  
4.  Ağ özgü özel durumların uygun türetilmiş sınıfa normalleştirilir olun <xref:System.ServiceModel.CommunicationException>.  
  
5.  Bir kanal yığınına özel taşıma ekleyen bir bağlama öğesi ekleyin. [Bir bağlama öğesi ekleme] daha fazla bilgi için bkz.  
  
## <a name="creating-iduplexsessionchannel"></a>Da IDuplexSessionChannel öğelerini oluşturma  
 WSE 3.0 TCP birlikte çalışabilirlik aktarım yazma ilk adımı uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IDuplexSessionChannel> üst kısmındaki bir <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` öğesinden türetilen <xref:System.ServiceModel.Channels.ChannelBase>. Bir ileti gönderme mantığı iki ana parçalarını oluşur: (1) bayt ve (2) bu baytlardan çerçeveleme ve kablo göndererek, ileti kodlama.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ayrıca, bir kilit, böylece da IDuplexSessionChannel öğelerini sırayla garanti Send() çağrıları korumak ve temel alınan yuva çağrıları doğru eşitlenebilmesi amacıyla alınır.  
  
 `WseTcpDuplexSessionChannel` kullanan bir <xref:System.ServiceModel.Channels.MessageEncoder> çevirme için bir <xref:System.ServiceModel.Channels.Message> byte [] gelen ve giden. Bir taşıma olduğundan `WseTcpDuplexSessionChannel` ayrıca kanalı ile yapılandırılmış uzak adres uygulamak için sorumludur. `EncodeMessage` Bu dönüştürme mantığını kapsüller.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Bir kez <xref:System.ServiceModel.Channels.Message> kodlanmış baytlara, onu kablo iletilmesi gerekir. Bu ileti sınırlarını tanımlamak için bir sistem gerektirir. WSE 3.0 kullanan bir sürümünü [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) çerçeveleme protokol olarak. `WriteData` bayt [] DIME kayıt kümesini sarmalamak için çerçeveleme mantığı kapsüller.  
  
 İleti almak için mantığı çok benzer. Ana karmaşıklığı okuma yuva istenenden daha az bayt döndürebilir olgu işleyen. Bir ileti almak için `WseTcpDuplexSessionChannel` kablo kapalı baytlarını okuyan DIME çerçeveleme kodunu çözer ve ardından <xref:System.ServiceModel.Channels.MessageEncoder> byte [] oturum açmak için bir <xref:System.ServiceModel.Channels.Message>.  
  
 Temel `WseTcpDuplexSessionChannel` bağlanmış bir yuva aldığını varsayar. Temel sınıf yuva kapatma işler. Yuva kapatma ile arabirim üç yer vardır:  
  
-   OnAbort--yuva ungracefully kapatın (sabit kapanış).  
  
-   [Begin üzerinde] yakın--yuva düzgün biçimde kapatılamadı (yazılım Kapat).  
  
-   oturumu. CloseOutputSession--kapatma giden veri akışı (yarı Kapat).  
  
## <a name="channel-factory"></a>Kanal Fabrikası  
 TCP aktarımı yazma sonraki adımı uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> istemci kanallar için.  
  
-   `WseTcpChannelFactory` öğesinden türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<da IDuplexSessionChannel öğelerini >. Geçersiz kılan bir factory, `OnCreateChannel` istemci kanalları oluşturmak için.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` mantıksal tabanda ekler `WseTcpDuplexSessionChannel` bir TCP sunucusuna bağlanmak için `channel.Open` zaman. Önce aşağıdaki kodda gösterildiği gibi bir IP adresine çözümlenen adıdır.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Ardından ana bilgisayar adı, döngü içinde ilk kullanılabilir IP adresi aşağıdaki kodda gösterildiği gibi bağlıdır.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Kanal sözleşmesinin bir parçası, etki alanına özgü özel durumların, gibi sarmalanır `SocketException` içinde <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Kanal dinleyicisi  
 TCP aktarımı yazma sonraki adımı uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelListener> sunucuya kanalların kabul etmek için.  
  
-   `WseTcpChannelListener` öğesinden türetilen <xref:System.ServiceModel.Channels.ChannelListenerBase> \<da IDuplexSessionChannel öğelerini > ve [Begin] ve [Begin] açık geçersiz kılmalar kapatmak için Dinleme yuvası ömrünü denetleyin. Açıldığında, yuva IP_ANY üzerinde dinleyecek şekilde oluşturulur. IPv6 için de dinlemek için ikinci bir yuva daha gelişmiş uygulamalar oluşturabilirsiniz. Ayrıca ana bilgisayar adı belirtilmesi için IP adresine izin verebilirsiniz.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Yeni bir yuva kabul edildiğinde, bir sunucu kanalı bu yuvası ile başlatılır. Tüm giriş ve çıkış zaten uygulanır ve taban sınıfta bu kanal yuva başlatmak için sorumlu olacak şekilde.  
  
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleniyor  
 Fabrikaları ve kanallar oluşturulur, bunlar bir bağlama aracılığıyla ServiceModel çalışma zamanına sunulmalıdır. Bir bağlama temsil eden bir hizmet adresle ilişkilendirilen iletişim yığını bağlama öğelerinin bir koleksiyondur. Yığındaki her öğe bir bağlama öğesi tarafından temsil edilir.  
  
 Bu örnekte bağlama öğedir `WseTcpTransportBindingElement`, öğesinden türetildiğini <xref:System.ServiceModel.Channels.TransportBindingElement>. Destekliyorsa <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ve bizim bağlamayla ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Kopyalama için de üyeleri içeren `BindingElement` ve bizim (wse.tcp) şeması döndürüyor.  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP Test Konsolu  
 Bu örnek aktarım kullanmak için test kodu TestCode.cs içinde kullanılabilir. Aşağıdaki yönergeler WSE nasıl belirleyeceğinizi `TcpSyncStockService` örnek.  
  
 MTOM kodlama olarak kullanan özel bir bağlama test kodu oluşturur ve `WseTcpTransport` aktarım olarak. Ayrıca AddressingVersion değerini ' WSE 3.0 ile uyumlu olması için aşağıdaki kodda gösterildiği gibi ayarlar.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 İki testleri oluşur: WSE 3.0 WSDL'den oluşturulan kodu kullanarak türü belirtilmiş bir istemci bir test ayarlar. İkinci test API'ler kanal üzerine doğrudan iletiler göndererek hem istemci hem de sunucu olarak WCF kullanır.  
  
 Örnek çalıştırırken aşağıdaki çıktı beklenir.  
  
 İstemci:  
  
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
  
 Sunucu:  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Bu örneği çalıştırmak için WSE 3.0 ve WSE sahip `TcpSyncStockService` yüklü örnek. İndirebileceğiniz [WSE 3.0 MSDN'den](https://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  WSE 3.0 üzerinde desteklenmediğinden [!INCLUDE[lserver](../../../../includes/lserver-md.md)], yükleme veya çalıştıramazsınız `TcpSyncStockService` bu işletim sisteminde örnek.  
  
1.  Yüklemeden sonra `TcpSyncStockService` örnek, aşağıdakileri yapın:  
  
    1.  Açık `TcpSyncStockService` Visual Studio'daki (TcpSyncStockService örnek ile WSE 3.0 yüklü olduğunu unutmayın. Bu örnek'ın kod parçası değildir).  
  
    2.  StockService projeyi başlangıç projesi olarak ayarlayın.  
  
    3.  StockService.cs StockService projesi ve [ilke] özniteliği yorum açmak `StockService` sınıfı. Bu örnekteki güvenlik devre dışı bırakır. WCF WSE 3.0 güvenli uç noktaları ile çalışabilirler, ancak güvenlik özel TCP taşımasında odaklanmış Bu örneği tutmak için devre dışı bırakıldı.  
  
    4.  Başlatmak için F5 tuşuna basın `TcpSyncStockService`. Hizmetini yeni bir konsol penceresi başlatır.  
  
    5.  Bu TCP taşıma örneği Visual Studio'da açın.  
  
    6.  Makine adı çalışan eşleştirilecek TestCode.cs "ana bilgisayar adı" değişkeninde güncelleştirme `TcpSyncStockService`.  
  
    7.  TCP aktarımı örneği başlatmak için F5 tuşuna basın.  
  
    8.  TCP aktarımı test istemcisinin yeni bir konsolda başlatır. İstemci, hisse senedi fiyatlarını hizmetten ister ve ardından sonuçları, konsol penceresinde görüntüler.  
  
