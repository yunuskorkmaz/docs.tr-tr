---
title: 'Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: fb877e6d55214e9a268a88b33a4613ca8df0eb8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transport-wse-30-tcp-interoperability"></a>Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik
WSE 3.0 TCP birlikte çalışabilirlik taşıma örneği, TCP çift yönlü oturum özel bir Windows Communication Foundation (WCF) taşıma olarak uygulamak gösterilmiştir. Kanal katmanını genişletilebilirlik arabirimine varolan dağıtılan sistemleriyle kablo üzerinden nasıl kullanabileceğinizi gösterir. Aşağıdaki adımlar, bu özel nasıl oluşturulacağını gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] taşıma:  
  
1.  Bir TCP yuvası ile başlayarak, istemci ve sunucu uygulamaları oluşturma <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , DIME çerçeveleme ileti sınırlarını tanımlamak için kullanın.  
  
2.  WSE TCP hizmetine bağlanır ve istemci Çerçeveli iletileri gönderen bir kanal fabrikası oluşturma <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Gelen TCP bağlantılarını kabul etmek ve karşılık gelen kanalları üretmek için bir kanal dinleyicisi oluşturun.  
  
4.  Ağa özgü özel durumlar için uygun olan türetilmiş sınıf normalleştirilmiş emin olun <xref:System.ServiceModel.CommunicationException>.  
  
5.  Bir kanal yığınına özel taşıma ekler bir bağlama öğesi ekleyin. [Bağlama öğesi ekleme] daha fazla bilgi için bkz.  
  
## <a name="creating-iduplexsessionchannel"></a>Da IDuplexSessionChannel öğelerini oluşturma  
 WSE 3.0 TCP birlikte çalışabilirlik aktarım yazma ilk adımı uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IDuplexSessionChannel> üstünde bir <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` türetilen <xref:System.ServiceModel.Channels.ChannelBase>. Bir ileti gönderme mantığı iki ana parçalarını oluşur: (1) bayt sayısı, (2) bu bayt çerçeveleme ve kablo göndererek içine iletinin kodlaması.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ayrıca, bir kilit böylece Send() çağrıları da IDuplexSessionChannel öğelerini sıralı garantisi korumak ve temel yuva çağrıları doğru eşitlenmesi alınır.  
  
 `WseTcpDuplexSessionChannel` kullanan bir <xref:System.ServiceModel.Channels.MessageEncoder> çevirme için bir <xref:System.ServiceModel.Channels.Message> byte [] gelen ve giden. Bir taşıma olduğundan `WseTcpDuplexSessionChannel` ayrıca kanalı ile yapılandırılmış uzak adres uygulamak için sorumludur. `EncodeMessage` Bu dönüştürme için mantığı yalıtır.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Bir kez <xref:System.ServiceModel.Channels.Message> kodlanır baytlara, onu kablo aktarılması gerekir. Bu ileti sınırlarını tanımlamak için bir sistem gerektirir. WSE 3.0 kullanan bir sürümünü [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) çerçeveleme protokol olarak. `WriteData` byte [] DIME kayıt kümesine sarmalamak için çerçeveleme mantığı yalıtır.  
  
 İletileri almak için mantığı çok benzer. Ana karmaşıklık okuma yuva istenenden daha az bayt döndürebilir olgu işliyor. Bir ileti alacak `WseTcpDuplexSessionChannel` kablo kapalı bayt okur, DIME çerçeveleme kodunu çözer ve ardından kullanır <xref:System.ServiceModel.Channels.MessageEncoder> kapatma içine byte [] için bir <xref:System.ServiceModel.Channels.Message>.  
  
 Temel `WseTcpDuplexSessionChannel` bağlı bir yuva aldığını varsayar. Taban sınıfı yuva kapatma işler. Yuva kapatılması ile arabirim üç yerde vardır:  
  
-   OnAbort--yuva ungracefully kapatın (sabit Kapat).  
  
-   [Başlangıç üzerinde] Kapat--yuva düzgün biçimde kapatılamadı (yumuşak Kapat).  
  
-   oturumu. CloseOutputSession--kapatma giden veri akışı (yarım Kapat).  
  
## <a name="channel-factory"></a>Kanal Fabrikası  
 TCP taşıma yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> istemci kanalları.  
  
-   `WseTcpChannelFactory` türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<da IDuplexSessionChannel öğelerini >. Geçersiz kılan bir Fabrika olduğu `OnCreateChannel` istemci kanallar oluşturmak için.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` temel mantığı ekler `WseTcpDuplexSessionChannel` bir TCP sunucusuna bağlanmak için `channel.Open` zaman. İlk ana bilgisayar adı aşağıdaki kodda gösterildiği gibi bir IP adresine çözümlenir.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Ardından ana bilgisayar adı bir döngü ilk kullanılabilir IP adresi aşağıdaki kodda gösterildiği gibi bağlı.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Kanal sözleşmesinin bir parçası, etki alanına özgü özel durumlar, gibi sarılır `SocketException` içinde <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Kanal dinleyicisi  
 TCP taşıma yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelListener> sunucuya kanalların kabul etmek için.  
  
-   `WseTcpChannelListener` türetilen <xref:System.ServiceModel.Channels.ChannelListenerBase> \<da IDuplexSessionChannel öğelerini > ve geçersiz kılma [Başlangıç] ve [Başlangıç] açık üzerinde Dinleme yuvası ömrü kapatmak için denetim. Açıldığında, yuva IP_ANY üzerinde dinlenecek oluşturulur. Daha gelişmiş uygulamaları IPv6 için de dinlemek için ikinci bir yuva oluşturabilirsiniz. Ayrıca ana bilgisayar adı belirtilmesi için IP adresi izin verebilirsiniz.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Yeni bir yuva kabul edildiğinde, bir sunucu kanal bu yuvası ile başlatıldı. Tüm giriş ve çıkış zaten uygulanır taban sınıf içinde bu kanal yuva başlatmak için sorumlu olduğu şekilde.  
  
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleme  
 Fabrikaları ve kanallar oluşturulmuştur, bunlar bir bağlama aracılığıyla ServiceModel çalışma zamanına sunulmalıdır. Bir bağlama hizmeti adresi ile ilişkili iletişim yığını temsil eden bağlama öğelerinin bir koleksiyondur. Yığındaki her öğe bir bağlama öğesi temsil edilir.  
  
 Örnekte, bağlama öğedir `WseTcpTransportBindingElement`, den türetilen <xref:System.ServiceModel.Channels.TransportBindingElement>. Destekliyorsa <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ve bizim bağlama ile ilişkili oluşturucuları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Kopyalama için de üyeleri içeren `BindingElement` ve bizim düzenini (wse.tcp) döndürüyor.  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP sınama Konsolu  
 Bu örnek aktarım kullanmak için test kodu TestCode.cs içinde kullanılabilir. Aşağıdaki yönergeler WSE ayarlama Göster `TcpSyncStockService` örnek.  
  
 MTOM kodlama olarak kullanan özel bağlama test kodunu oluşturur ve `WseTcpTransport` taşıma olarak. Ayrıca AddressingVersion değerini WSE 3.0 ile uyumlu olması için aşağıdaki kodda gösterildiği gibi ayarlar.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 İki sınamaları oluşur: WSE 3.0 WSDL oluşturulan kod kullanarak bir türü belirlenmiş istemci ayarlayan bir sınama. İkinci test kullanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hem istemci hem de sunucunun kanal API'lerini doğrudan üstünde iletiler göndererek olarak.  
  
 Örnek çalıştırırken aşağıdaki çıkış beklenir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Bu örneği çalıştırmak için WSE 3.0 ve WSE sahip `TcpSyncStockService` yüklü örnek. İndirebilirsiniz [WSE 3.0 MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  WSE 3.0 üzerinde desteklenmediğinden [!INCLUDE[lserver](../../../../includes/lserver-md.md)], yükleme veya çalıştıramazsınız `TcpSyncStockService` bu işletim sisteminde örnek.  
  
1.  Yüklemeden sonra `TcpSyncStockService` örnek, aşağıdakileri yapın:  
  
    1.  Açık `TcpSyncStockService` Visual Studio (Not TcpSyncStockService örnek WSE 3.0 ile yüklenir. Bu örnek 's kod parçası değil).  
  
    2.  StockService projesini başlangıç projesi olarak ayarlayın.  
  
    3.  StockService.cs StockService proje ve yorum out [ilke] özniteliğini açmak `StockService` sınıfı. Bu güvenlik örnekten devre dışı bırakır. Sırada [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSE 3.0 güvenli uç noktaları çalışabilirler, güvenlik üzerinde özel TCP taşıma odaklanmış Bu örnek tutmak için devre dışıdır.  
  
    4.  Başlatmak için F5 tuşuna basın `TcpSyncStockService`. Yeni bir konsol penceresi hizmetini başlatır.  
  
    5.  Bu TCP taşıma örnek Visual Studio'da açın.  
  
    6.  Makine adı çalışan eşleşecek şekilde TestCode.cs "ana bilgisayar adı" değişkeninde güncelleştirme `TcpSyncStockService`.  
  
    7.  TCP taşıma örneği başlatmak için F5 tuşuna basın.  
  
    8.  TCP taşıma test istemcisi yeni bir konsol içinde başlatır. İstemci Hizmeti'nden borsa bilgileri ister ve sonra sonuçları, konsol penceresinde görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.
