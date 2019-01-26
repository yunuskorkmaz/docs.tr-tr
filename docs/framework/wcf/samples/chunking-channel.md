---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: db14ceb956202bee06ff5e6b37b21fb837c6f1d9
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066421"
---
# <a name="chunking-channel"></a>Öbekleme Kanalı
Windows Communication Foundation (WCF) kullanarak büyük iletileri gönderirken, genellikle bu iletileri arabelleğe almak için kullanılan bellek miktarını sınırlamak için tercih edilir. Olası bir çözüm (toplu veri gövdesinde olduğunu varsayarak) ileti akışı sağlamaktır. Ancak bazı protokoller, iletinin tamamı arabelleğe alma gerektirir. Güvenilir Mesajlaşma ve güvenlik gibi iki örnek verilebilir. Başka bir olası öbekleri adlı küçük iletilere büyük ileti ayırmak, söz konusu öbekleri bir öbek teker teker gönderilir ve alıcı tarafında büyük ileti yeniden oluşturmak için bir çözümdür. Uygulama bu parçalama yapabilirsiniz ve serbest Öbekleme veya özel bir kanalda yapmak için kullanabilirsiniz. Kümeleme kanal örnek nasıl bir özel protokolü veya katmanlı kanal Öbekleme ve büyük iletilerin XML'deki Öbekleme yapmak için kullanılabileceğini gösterir.  
  
 Gönderilecek iletinin tamamı bir yalnızca oluşturulan sonra Öbekleme her zaman işe. Kümeleme kanal her zaman bir güvenlik kanalı ve bir güvenilir oturum kanalı altında katmanlı.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Kümeleme kanal varsayımlar ve sınırlamalar  
  
### <a name="message-structure"></a>İleti yapısı  
 Kümeleme kanalın iletilerin öbekli aşağıdaki ileti yapısını varsayılır:  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 ServiceModel kullanırken, 1 giriş parametresi kendi giriş iletisi iletisinin bu şekli ile uyumlu olan işlemler sözleşme. Benzer şekilde, bu şekilde, çıktı iletisi iletisinin 1 çıkış parametresi veya dönüş değeri sözleşme işlemleri uyumlu. Bu tür işlemlerine örnekler şunlardır:  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a>Oturumlar  
 Kümeleme kanal iletileri (parçalar) iletilerin sıralı teslim, kesinlikle bir kerelik teslim edilmesini gerektirir. Bu, arka plandaki kanal yığın kapatamaması olması gerektiği anlamına gelir. Oturumlarının kapatamaması Protokolü kanal (örneğin, ReliableSession kanal) veya aktarım (örneğin, TCP taşıma) tarafından sağlanabilir.  
  
### <a name="asynchronous-send-and-receive"></a>Zaman uyumsuz gönderme ve alma  
 Zaman uyumsuz yöntemler gönderip kümeleme kanal örnek bu sürümünde uygulanmadı.  
  
## <a name="chunking-protocol"></a>Kümeleme Protokolü  
 Kümeleme kanal başlangıç ve yanı sıra her bir öbeği sıra numarası öbekleri bir dizi sonuna belirten bir protokol tanımlar. Aşağıdaki üç örnek iletileri başlangıcı, her önemli noktaları açıklayan bir yorum ile öbek ve son iletileri gösterir.  
  
### <a name="start-message"></a>Başlangıç iletisi  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!--Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a>Öbek iletisi  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a>Son ileti  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a>Öbekleme kanalı mimarisi  
 Kümeleme kanal bir `IDuplexSessionChannel` tipik kanal mimari, yüksek bir düzeyde izler. Var olan bir `ChunkingBindingElement` , yapılandırılabilir bir `ChunkingChannelFactory` ve `ChunkingChannelListener`. `ChunkingChannelFactory` Örneklerini oluşturur `ChunkingChannel` zaman bunu istenir. `ChunkingChannelListener` Örneklerini oluşturur `ChunkingChannel` ne zaman yeni bir iç kanal kabul edilir. `ChunkingChannel` Kendisi ileti gönderme ve alma için sorumlu değildir.  
  
 Aşağı, sonraki düzeyde `ChunkingChannel` kümeleme Protokolü uygulamak için çeşitli bileşenleri kullanır. Gönderme tarafında, özel bir kanal kullanan `XmlDictionaryWriter` adlı `ChunkingWriter` gerçek Öbekleme yapar. `ChunkingWriter` İç kanal öbekleri doğrudan göndermek için kullanır. Özel bir kullanarak `XmlDictionaryWriter` büyük iletisinin gövdesi, özgün yazıldığı gibi öbekleri göndermemizi sağlar. Bu, biz özgün iletinin tamamı arabellek yok anlamına gelir.  
  
 ![Öbekleme kanalı](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 Alma tarafında `ChunkingChannel` iç kanal gelen iletileri alır ve bunları özel bir uygulamalı `XmlDictionaryReader` adlı `ChunkingReader`, gelen öbek özgün iletiden reconstitutes. `ChunkingChannel` Bu sarmalar `ChunkingReader` özel `Message` adlı uygulama `ChunkingMessage` ve bu iletiyi yukarıdaki katmana döndürür. Bu birleşimi `ChunkingReader` ve `ChunkingMessage` tüm özgün ileti gövdesini arabelleğe alıp zorunda kalmak yerine katmanın üzerinde okunduğu şekilde özgün ileti gövdesi serbest öbek olanak sağlıyor. `ChunkingReader` bir kuyruk, burada arabelleğe alınan öbekleri yapılandırılabilir en fazla sayıya kadar gelen öbekleri arabelleğe alır sahiptir. Bu maksimum sınıra ulaşıldığında, okuyucu iletilerin kuyruktan yukarıdaki katmanı tarafından boşaltılır bekler (diğer bir deyişle, yalnızca özgün iletinin gövdesinden okuyarak) veya en fazla alana kadar zaman aşımına ulaşıldığı.  
  
 ![Öbekleme kanalı](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Programlama modeli Öbekleme  
 Hizmet geliştiricileri, iletileri uygulayarak öbekli üzeresiniz belirtebilirsiniz `ChunkingBehavior` sözleşme işlemlerini özniteliği. Öznitelik sunan bir `AppliesTo` Öbekleme giriş iletisi, çıktı iletisi veya her ikisi de uygulanıp uygulanmayacağını belirtmek Geliştirici izin veren özellik. Aşağıdaki örnek, kullanımını gösterir. `ChunkingBehavior` özniteliği:  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 Bu programlama modelinden `ChunkingBindingElement` eylem öbekli için iletileri tanımlayan bir URI'leri listesini derler. Eylemin her Giden iletinin ileti öbekli veya doğrudan gönderilen belirlemek için bu listeyi karşı karşılaştırılır.  
  
## <a name="implementing-the-send-operation"></a>Gönderme işlemi uygulama  
 Yüksek düzeyde, gönderme işlemi ilk giden ileti öbekli gerekir aksi takdirde, iç kanal kullanarak doğrudan ileti gönderir olup olmadığını ve denetler.  
  
 İleti öbekli, gönderme yeni bir oluşturur `ChunkingWriter` ve çağrıları `WriteBodyContents` giden iletide bu iletmeden `ChunkingWriter`. `ChunkingWriter` (Başlangıç öbek iletiyi özgün ileti üstbilgileri kopyalama dahil) ileti Öbekleme yapar ve iç kanal kullanarak öbekleri gönderir.  
  
 Önemli birkaç ayrıntıları:  
  
-   İlk çağrı gönderme `ThrowIfDisposedOrNotOpened` emin olmak için `CommunicationState` açılır.  
  
-   Her oturum için bir kerede yalnızca bir ileti gönderilmesi için gönderme eşitlenir. Var olan bir `ManualResetEvent` adlı `sendingDone` öbekli bir ileti gönderildiğinde sıfırlanır. Son öbek ileti gönderildikten sonra bu olay ayarlanır. Send yöntemi giden ileti göndermeye çalışmadan önce ayarlamak bu olay için bekler.  
  
-   Kilitleri Gönder `CommunicationObject.ThisLock` önlemek için eşitleme durumu değişiklikleri gönderilirken. Bkz: <xref:System.ServiceModel.Channels.CommunicationObject> hakkında daha fazla bilgi için belgelere <xref:System.ServiceModel.Channels.CommunicationObject> durumları ve Durum makinesi.  
  
-   Gönderme geçirilen zaman aşımı, tüm öbekleri gönderme içeren tüm gönderme işlemi için zaman aşımı olarak kullanılır.  
  
-   Özel `XmlDictionaryWriter` tasarım, tüm özgün ileti gövdesini arabelleğe almayı önlemek için seçildi. Alınacak olsaydık bir `XmlDictionaryReader` gövdesi kullanma `message.GetReaderAtBodyContents` tüm gövdesinin arabelleğe. Bunun yerine, özel bir sahibiz `XmlDictionaryWriter` yapan `message.WriteBodyContents`. İletiyi WriteBase64 yazıcısı, yazıcı iletileri parçalara'kurmak paketleri ve bunları gönderir çağrıları iç kanal kullanma. Öbek gönderilene kadar WriteBase64 engeller.  
  
## <a name="implementing-the-receive-operation"></a>Uygulama alma işlemi  
 Yüksek bir düzeyde alma işlemi önce gelen ileti olmadığını denetler `null` ve sahip olduğu eylem ise `ChunkingAction`. Her iki ölçütleri karşılamıyorsa ileti alma değiştirilmeden döndürülür. Aksi takdirde, Al yeni bir oluşturur `ChunkingReader` ve yeni bir `ChunkingMessage` etrafında sarmalanmış (çağırarak `GetNewChunkingMessage`). Bu yeni döndürmeden önce `ChunkingMessage`, alma kullanan bir iş parçacığı havuzu iş parçacığını yürütmek için `ReceiveChunkLoop`, çağıran `innerChannel.Receive` döngü ve öbekleri için ellerini `ChunkingReader` son öbek ileti alındığında veya alma işlemi zamanı aşımını isabet kadar.  
  
 Önemli birkaç ayrıntıları:  
  
-   İlk çağrı gönderme gibi alan `ThrowIfDisposedOrNotOepned` emin olmak için `CommunicationState` açılır.  
  
-   Alma oturum aynı anda yalnızca bir ileti alınabilmesi için de eşitlenir. Bu, başlangıç öbek iletisi alındıktan sonra sonraki alınan iletilerin tümünü bir son öbeği iletisi alınana kadar bu yeni öbek dizisi içindeki öbekleri olmaları beklenir çünkü özellikle önemlidir. Alma şu anda devre dışı bırakmak öbekli iletinin ait öbeklerin tümü alınana kadar iç kanal iletilerden çekme gerçekleştirilemiyor. Bunu gerçekleştirmek için kullandığı almak bir `ManualResetEvent` adlı `currentMessageCompleted`, son öbek ileti alındı ve yeni bir başlangıç öbek ileti alındığında sıfırlama sırasında ayarlanır.  
  
-   Gönderme, alma alma sırasında eşitlenmiş durumu geçişleri engellemez. Örneğin, yakın alma ve bekler sırasında özgün iletinin bekleyen alma tamamlandı veya belirtilen zaman aşımı değeri ulaşılana kadar çağrılabilir.  
  
-   Alınacak geçirilen zaman aşımı tamamı için zaman aşımını alma gibi tüm parçalar içeren işlemi kullanılır.  
  
-   İleti gövdesi gelen öbek iletileri hızdan daha düşük bir hızda iletiyi tüketir katmanı kullanıp kullanmadığına `ChunkingReader` tarafından belirtilen sınıra kadar gelen söz konusu öbekleri arabelleği `ChunkingBindingElement.MaxBufferedChunks`. Bu sınıra ulaşıldığında, öbeği arabelleğe alınan bir Öbek ile kullanılan ya da alma zaman aşımı ulaşılana kadar daha düşük bir katmandan diğerine alınır.  
  
## <a name="communicationobject-overrides"></a>CommunicationObject geçersiz kılmaları  
  
### <a name="onopen"></a>Açıldığında  
 `OnOpen` çağrıları `innerChannel.Open` iç kanal açın.  
  
### <a name="onclose"></a>OnClose  
 `OnClose` öncelikle ayarlar `stopReceive` için `true` göstermek için bekleyen `ReceiveChunkLoop` durdurmak için. Ardından bekler `receiveStopped` <xref:System.Threading.ManualResetEvent>, ne zaman ayarlanır `ReceiveChunkLoop` durdurur. Varsayılarak `ReceiveChunkLoop` durdurur belirtilen süre içinde `OnClose` çağrıları `innerChannel.Close` kalan zaman aşımı ile.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` çağrıları `innerChannel.Abort` iç kanal iptal etmek için. Varsa bir bekleyen `ReceiveChunkLoop` adresinden bir özel durum alır bekleyen `innerChannel.Receive` çağırın.  
  
### <a name="onfaulted"></a>OnFaulted  
 `ChunkingChannel` Kanal olduğunda özel davranış hatalı bunu gerektirmez `OnFaulted` değil geçersiz kılınır.  
  
## <a name="implementing-channel-factory"></a>Kanal fabrikası uygulama  
 `ChunkingChannelFactory` Örneklerini oluşturmaktan sorumlu `ChunkingDuplexSessionChannel` ve iç kanal fabrikası basamaklı durumuna geçişler.  
  
 `OnCreateChannel` İç kanal fabrikası oluşturmak için kullandığı bir `IDuplexSessionChannel` iç kanal. Ardından yeni bir oluşturur `ChunkingDuplexSessionChannel` öbekli için ileti Eylemler ve öbekleri alma sırasında arabelleğe alınacak en fazla sayısını listesi ile birlikte bu iç kanal geçirme. Öbekli için ileti Eylemler ve öbekleri arabelleğe alınacak en fazla sayısını listesi olan iki parametre geçirilen `ChunkingChannelFactory` kendi oluşturucusuna. Bölüm `ChunkingBindingElement` bu değerlerin nereden geldiğini açıklar.  
  
 `OnOpen`, `OnClose`, `OnAbort` Ve zaman uyumsuz eşdeğerlerine üzerinde iç kanal fabrikası karşılık gelen durum geçiş yöntemini çağırın.  
  
## <a name="implementing-channel-listener"></a>Kanal dinleyicisi uygulama  
 `ChunkingChannelListener` Bir iç kanal dinleyicisi çevresinde bir sarmalayıcı olan. Ana işlevi, bu iç kanal dinleyicisi temsilci çağrılarını yanı sıra yeni sarmaktır `ChunkingDuplexSessionChannels` iç kanal dinleyicisinden kabul kanalları geçici bir çözüm. Bu yapılır `OnAcceptChannel` ve `OnEndAcceptChannel`. Yeni oluşturulan `ChunkingDuplexSessionChannel` iç kanal daha önce açıklanan diğer parametreler birlikte geçirilir.  
  
## <a name="implementing-binding-element-and-binding"></a>Uygulama bağlama öğesi ve bağlama  
 `ChunkingBindingElement` oluşturmaktan sorumlu `ChunkingChannelFactory` ve `ChunkingChannelListener`. `ChunkingBindingElement` Denetler olup olmadığını T `CanBuildChannelFactory` \<T > ve `CanBuildChannelListener` \<T > türü `IDuplexSessionChannel` (yalnızca kanalı kümeleme kanalı tarafından desteklenen) ve bağlamayı diğer bağlama öğeleri bu destek Kanal türü.  
  
 `BuildChannelFactory`\<T > ilk denetler istenen kanal türü oluşturulabilir ve ardından öbekli için ileti eylemlerin bir listesini alır. Daha fazla bilgi için aşağıdaki bölüme bakın. Ardından yeni bir oluşturur `ChunkingChannelFactory` iç kanal fabrikası geçirme (döndürülen `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), ileti Eylemler ve öbekleri arabelleğe alınacak en fazla sayısını listesi. Adlı bir özellikten öbekleri sayısı gelir `MaxBufferedChunks` tarafından kullanıma sunulan `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>` oluşturmak için benzer bir uygulamaya sahip `ChunkingChannelListener` ve iç kanal dinleyicisi geçirme.  
  
 Bu örnekte adlı bulunan bir örnek bağlaması var. `TcpChunkingBinding`. Bu bağlamanın iki bağlama öğelerden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement`. Gösterme yanı sıra `MaxBufferedChunks` özelliği, bağlama de ayarlar bazı `TcpTransportBindingElement` gibi özellikler `MaxReceivedMessageSize` (ayarlar `ChunkingUtils.ChunkSize` + 100 KB bayt üst bilgileri için).  
  
 `TcpChunkingBinding` Ayrıca uygulayan `IBindingRuntimePreferences` ve öğesinden true değerini döndürür `ReceiveSynchronously` yalnızca zaman uyumlu alma çağrıları uyguladığını gösteren yöntemi.  
  
### <a name="determining-which-messages-to-chunk"></a>Hangi öbek için iletileri belirleme  
 Kümeleme kanal aracılığıyla tanıtılan iletileri chunks `ChunkingBehavior` özniteliği. `ChunkingBehavior` Sınıfının Implements `IOperationBehavior` ve çağırarak uygulanan `AddBindingParameter` yöntemi. Bu yöntemde, `ChunkingBehavior` değerini inceler, `AppliesTo` özelliği (`InMessage`, `OutMessage` veya her ikisi) hangi iletileri öbekli belirlemek için. Ardından eylem her birinin bu iletileri alır (üzerinde iletileri koleksiyondan `OperationDescription`) ve örneği içinde yer alan bir dize koleksiyonu ekler `ChunkingBindingParameter`. Ardından bu ekler `ChunkingBindingParameter` için sağlanan `BindingParameterCollection`.  
  
 Bu `BindingParameterCollection` içine geçirilen `BindingContext` bağlamasında, bağlama öğesi kanal fabrikası ya da kanal dinleyicisi oluşturduğunda her bağlama öğesi için. `ChunkingBindingElement`'S uygulaması `BuildChannelFactory<T>` ve `BuildChannelListener<T>` bu çekme `ChunkingBindingParameter` tanesi `BindingContext’`s `BindingParameterCollection`. Koleksiyonu içinde bulunan Eylemler `ChunkingBindingParameter` geçirilerek `ChunkingChannelFactory` veya `ChunkingChannelListener`, sırayla Geçiren kendisine `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Service.exe ilk çalıştırma, Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleyin.  
  
 Örnek çalıştırırken aşağıdaki çıktı beklenir.  
  
 İstemci:  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 Sunucu:  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
