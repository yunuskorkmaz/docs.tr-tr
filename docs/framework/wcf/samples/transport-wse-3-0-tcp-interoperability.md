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
# <a name="transport-wse-30-tcp-interoperability"></a>Taşıma: WSE 3.0 TCP Birlikte Çalışabilirlik
WSE 3.0 TCP Birlikte Çalışabilirlik Taşıma örneği, özel bir Windows Communication Foundation (WCF) aktarımı olarak Bir TCP çift yönlü oturumun nasıl uygulanacağını gösterir. Ayrıca, kanal katmanının genişletilebilirliğini, varolan konuşlanmış sistemlerle kablo üzerinde arabirim yapmak için nasıl kullanabileceğinizi de gösterir. Aşağıdaki adımlar, bu özel WCF aktarımını nasıl oluşturabildiğini gösterir:  
  
1. Bir TCP soketiyle başlayarak, ileti <xref:System.ServiceModel.Channels.IDuplexSessionChannel> sınırlarını nida lamak için DIME Çerçeveleme'yi kullanan istemci ve sunucu uygulamalarını oluşturun.  
  
2. WSE TCP hizmetine bağlanan ve istemcinin <xref:System.ServiceModel.Channels.IDuplexSessionChannel>üzerinden çerçeveli iletiler gönderen bir kanal fabrikası oluşturun.  
  
3. Gelen TCP bağlantılarını kabul etmek ve ilgili kanalları üretmek için bir kanal dinleyicisi oluşturun.  
  
4. Ağa özgü özel özel durumların uygun türemiş sınıfa normalleştirildiğinden emin <xref:System.ServiceModel.CommunicationException>olun.  
  
5. Kanal yığınına özel aktarım ekleyen bağlayıcı bir öğe ekleyin. Daha fazla bilgi için bkz: [Bağlama Öğesi Ekleme].  
  
## <a name="creating-iduplexsessionchannel"></a>IDuplexSessionChannel oluşturma  
 WSE 3.0 TCP Birlikte Çalışabilirlik Taşımacılığı'nı <xref:System.ServiceModel.Channels.IDuplexSessionChannel> yazmanın ilk adımı, <xref:System.Net.Sockets.Socket>bir . `WseTcpDuplexSessionChannel`<xref:System.ServiceModel.Channels.ChannelBase>türetilmiştir. İleti gönderme mantığı iki ana parçadan oluşur: (1) İletiyi baytlara kodlamak ve (2) bu baytları çerçeveleme ve tel üzerinde gönderme.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Buna ek olarak, Send() çağrılarının IDuplexSessionChannel sıralı garantisini koruması ve böylece alttaki sokete yapılan çağrıların doğru şekilde eşitlemesi için bir kilit alınır.  
  
 `WseTcpDuplexSessionChannel`a <xref:System.ServiceModel.Channels.Message> <xref:System.ServiceModel.Channels.MessageEncoder> ve byte çevirmek için kullanır[]. Bu bir aktarım `WseTcpDuplexSessionChannel` olduğundan, kanalın birlikte yapılandırıldığı uzak adresi de uygulamaktan sorumludur. `EncodeMessage`bu dönüştürme nin mantığını kapsüller.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <xref:System.ServiceModel.Channels.Message> Baytlar halinde kodlandıktan sonra, tel üzerinde iletilmelidir. Bu, ileti sınırlarını tanımlamak için bir sistem gerektirir. WSE 3.0 çerçeveleme protokolü olarak [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) bir sürümünü kullanır. `WriteData`bir bayt[] dime kayıtları kümesine sarmak için çerçeveleme mantığını kapsüller.  
  
 İleti alma mantığı benzer. Ana karmaşıklık, bir soket okumasının istenenden daha az bayt döndürebildiği gerçeğini işlemektir. İleti almak için, `WseTcpDuplexSessionChannel` kablodan baytokur, DIME çerçevesini çözer ve <xref:System.ServiceModel.Channels.MessageEncoder> bayt[] bir <xref:System.ServiceModel.Channels.Message>.  
  
 Taban, `WseTcpDuplexSessionChannel` bağlı bir soket aldığını varsayar. Taban sınıf soket kapatma yı işler. Soket kapatma ile arayüz oluşturan üç yer vardır:  
  
- OnAbort -- soketi nezaketsiz kapatın (sert yakın).  
  
- [Begin]Close -soketi incelikle kapatın (yumuşak yakın).  
  
- Oturum. CloseOutputSession -- giden veri akışını kapatın (yarı yakın).  
  
## <a name="channel-factory"></a>Kanal Fabrikası  
 TCP aktarımını yazarken bir sonraki adım, istemci kanalları için <xref:System.ServiceModel.Channels.IChannelFactory> bir uygulama oluşturmaktır.  
  
- `WseTcpChannelFactory`IDuplexSessionChannel> türetilmiştir. <xref:System.ServiceModel.Channels.ChannelFactoryBase> \< İstemci kanalları üretmek `OnCreateChannel` için geçersiz kılan bir fabrikadır.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`zamanda bir TCP sunucusuna bağlanmak için tabanına `WseTcpDuplexSessionChannel` mantık ekler. `channel.Open` Önce ana bilgisayar adı, aşağıdaki kodda gösterildiği gibi bir IP adresine çözülür.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Ardından, ana bilgisayar adı, aşağıdaki kodda gösterildiği gibi, bir döngüdeki ilk kullanılabilir IP adresine bağlanır.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- Kanal sözleşmesinin bir parçası olarak, etki alanına özgü özel `SocketException` <xref:System.ServiceModel.CommunicationException>özel durumlar , 'deki gibi.  
  
## <a name="channel-listener"></a>Kanal Dinleyicisi  
 TCP aktarımını yazarken bir sonraki adım, sunucu kanallarını <xref:System.ServiceModel.Channels.IChannelListener> kabul etmek için bir uygulama oluşturmaktır.  
  
- `WseTcpChannelListener`iDuplexSessionChannel>'den <xref:System.ServiceModel.Channels.ChannelListenerBase> \<türetilmiştir ve dinleme soketinin ömrünü kontrol etmek için On[Begin]Open ve On[Begin]Close'u geçersiz kılar. OnOpen'de, IP_ANY dinlemek için bir soket oluşturulur. Daha gelişmiş uygulamalar da IPv6 dinlemek için ikinci bir soket oluşturabilirsiniz. Ayrıca IP adresinin ana bilgisayar adında belirtilmesine de izin verebilirler.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Yeni bir soket kabul edildiğinde, bu soketle bir sunucu kanalı açılır. Tüm giriş ve çıktı zaten taban sınıfta uygulanmıştır, bu nedenle bu kanal soketin başlatılmasından sorumludur.  
  
## <a name="adding-a-binding-element"></a>Bağlama Öğesi Ekleme  
 Artık fabrikalar ve kanallar inşa edildiklerine göre, bir bağlama yoluyla ServiceModel çalışma süresine maruz kalmalıdırlar. Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğeleri topluluğudur. Yığındaki her öğe bağlayıcı bir öğe yle temsil edilir.  
  
 Örnekte, bağlama öğesi `WseTcpTransportBindingElement`, hangi türetilmiştir <xref:System.ServiceModel.Channels.TransportBindingElement>. Bizim <xref:System.ServiceModel.Channels.IDuplexSessionChannel> bağlama ile ilişkili fabrikalar oluşturmak için aşağıdaki yöntemleri destekler ve geçersiz kılar.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Ayrıca klonlama `BindingElement` ve düzeni (wse.tcp) iade üyeleri içerir.  
  
## <a name="the-wse-tcp-test-console"></a>WSE TCP Test Konsolu  
 Bu örnek aktarım ı kullanmak için test kodu TestCode.cs'da mevcuttur. Aşağıdaki yönergeler WSE `TcpSyncStockService` örneğinin nasıl ayarlanacağını gösterir.  
  
 Test kodu, kodlama ve `WseTcpTransport` aktarım olarak MTOM kullanan özel bir bağlama oluşturur. Ayrıca, aşağıdaki kodda gösterildiği gibi Adresleme Sürümü'nü WSE 3.0 ile uyumlu olacak şekilde ayarlar.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 İki testten oluşur- bir test WSE 3.0 WSDL oluşturulan kodu kullanarak bir yazılı istemci ayarlar. İkinci test, doğrudan kanal API'lerinin üstüne ileti göndererek WCF'yi hem istemci hem de sunucu olarak kullanır.  
  
 Örneği çalıştırırken, aşağıdaki çıktı bekleniyor.  
  
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
  
## <a name="set-up-build-and-run-the-sample"></a>Örneği ayarlama, oluşturma ve çalıştırma  
  
1. Bu örneği çalıştırmak için [Microsoft .NET için Web Hizmetleri Geliştirmeleri (WSE) 3.0](https://www.microsoft.com/download/details.aspx?id=14089) ve WSE `TcpSyncStockService` örneğinin yüklü olması gerekir.
  
> [!NOTE]
> WSE 3.0 Windows Server 2008'de desteklenmediği `TcpSyncStockService` için, örneği bu işletim sistemine yükleyemezsiniz veya çalıştıramazsınız.  
  
1. Örneği yükledikten `TcpSyncStockService` sonra aşağıdakileri yapın:  
  
    1. Visual `TcpSyncStockService` Studio'da açın. (TcpSyncStockService örneği WSE 3.0 ile yüklenir. Bu, bu örneğin kodunun bir parçası değildir.)  
  
    2. StockService projesini başlangıç projesi olarak ayarlayın.  
  
    3. StockService projesinde StockService.cs açın ve sınıfla ilgili [İlke] özniteliğini `StockService` yorumla. Bu, örnekteki güvenliği devre dışı kılabilir. WCF WSE 3.0 güvenli uç noktaları ile birlikte çalışabilirken, bu örneği özel TCP taşımasına odaklamak için güvenlik devre dışı bırakılır.  
  
    4. Başlatmak için F5 `TcpSyncStockService`tuşuna basın. Hizmet yeni bir konsol penceresinde başlar.  
  
    5. Bu TCP taşıma örneğini Visual Studio'da açın.  
  
    6. "Hostname" değişkenini TestCode.cs'da çalıştıran `TcpSyncStockService`makine adıyla eşleştirmek için güncelleştirin.  
  
    7. TCP taşıma örneğini başlatmak için F5 tuşuna basın.  
  
    8. TCP aktarım testi istemcisi yeni bir konsolda başlar. İstemci hizmetten stok teklifleri ister ve sonuçları konsol penceresinde görüntüler.  
