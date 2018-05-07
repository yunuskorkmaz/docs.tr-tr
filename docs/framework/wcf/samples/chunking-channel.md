---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 1acb635be23b9a838abee714156d818abee6bcd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="chunking-channel"></a>Öbekleme Kanalı
Windows Communication Foundation (WCF) kullanarak büyük ileti gönderirken, genellikle bu iletileri arabelleğe almak için kullanılan bellek miktarını sınırlamak için önerilir. Olası bir çözüm (toplu veri gövdesinde olduğunu varsayarak) ileti gövdesi akış olmaktır. Ancak bazı protokolleri tüm ileti arabelleğe almayı gerektirir. Güvenilir Mesajlaşma ve güvenlik gibi iki örnek verilmiştir. Başka bir olası öbekleri adı verilen daha küçük iletilerine büyük ileti bölmek, aynı anda bu öbekleri bir öbek göndermek ve büyük iletiyi alan tarafta yeniden oluşturma için çözümüdür. Uygulama bu Öbekleme yapabilirsiniz ve XML'deki Öbekleme veya özel bir kanalda yapmak için kullanabilirsiniz. Kümeleme kanal örnek nasıl özel protokol veya katmanlı kanal Öbekleme ve büyük iletilerin XML'deki Öbekleme yapmak için kullanılabileceğini gösterir.  
  
 Gönderilecek iletinin tamamını bir yalnızca oluşturulan sonra Öbekleme her zaman işe. Kümeleme kanal her zaman bir güvenlik kanalı ve bir güvenilir oturum kanalı altında katmanlı.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Kümeleme kanal varsayımlar ve sınırlamalar  
  
### <a name="message-structure"></a>İleti yapısı  
 Kümeleme kanal iletileri öbekli için aşağıdaki iletiyi yapısı varsayılır:  
  
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
  
 ServiceModel kullanırken, kendi giriş ileti için ileti Bu şeklin uyması 1 giriş parametresi olan işlemler sözleşme. Benzer şekilde, kendi çıktı iletisi için iletisinin bu Şekil 1 çıktı parametresi veya dönüş değeri sözleşme işlemleri uyumlu. Bu tür işlemler örnekleri verilmiştir:  
  
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
 Kümeleme kanal iletileri (öbek) sıralı teslimini tam olarak bir kez teslim edilecek iletileri gerektirir. Bu, temel alınan kanal yığını süre sonuyla olması gerektiği anlamına gelir. Oturumları süre sonuyla Protokolü kanalı (örneğin, ReliableSession kanal) veya aktarım (örneğin, aktarım TCP) tarafından sağlanabilir.  
  
### <a name="asynchronous-send-and-receive"></a>Zaman uyumsuz gönderme ve alma  
 Zaman uyumsuz yöntemleri gönderip kümeleme kanal örnek bu sürümünde uygulanmadı.  
  
## <a name="chunking-protocol"></a>Kümeleme Protokolü  
 Kümeleme kanal başlangıç ve bitişini öbek ve aynı zamanda her bir öbeğin sıra numarasını belirten bir iletişim kuralı tanımlar. Aşağıdaki üç örnek iletileri başlangıç, her anahtar yönlerini açıklamak yorumlarla öbek ve bitiş iletileri gösterir.  
  
### <a name="start-message"></a>Başlatma iletisi  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
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
 Kümeleme kanal bir `IDuplexSessionChannel` , yüksek düzeyde, normal kanal mimarisi izler. Var olan bir `ChunkingBindingElement` , oluşturabilir bir `ChunkingChannelFactory` ve `ChunkingChannelListener`. `ChunkingChannelFactory` Örneklerini oluşturur `ChunkingChannel` zaman onu istendi. `ChunkingChannelListener` Örneklerini oluşturur `ChunkingChannel` zaman yeni bir iç kanal tarafından kabul edilir. `ChunkingChannel` Kendisi ileti gönderme ve alma için sorumlu değildir.  
  
 Aşağı, İleri düzeyde `ChunkingChannel` kümeleme Protokolü uygulamak için birkaç bileşenlerini kullanır. Özel bir kanal gönderme tarafında kullandığı `XmlDictionaryWriter` adlı `ChunkingWriter` gerçek Öbekleme gerçekleştirir. `ChunkingWriter` İç kanal öbekleri doğrudan göndermek için kullanır. Özel bir kullanarak `XmlDictionaryWriter` büyük özgün ileti gövdesini yazıldığı şekilde öbekleri göndermemizi sağlar. Bu, biz tüm özgün ileti arabellek değil anlamına gelir.  
  
 ![Öbekleme kanalı](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 Alma tarafında `ChunkingChannel` iç kanaldan iletiler çeker ve özel olarak aktarır `XmlDictionaryReader` adlı `ChunkingReader`, gelen öbek özgün iletiden reconstitutes. `ChunkingChannel` Bu sarmalar `ChunkingReader` özel bir `Message` adlı uygulama `ChunkingMessage` ve bu ileti yukarıdaki katmanı döndürür. Bu bileşimi `ChunkingReader` ve `ChunkingMessage` tüm özgün ileti gövdesini arabelleğe zorunda kalmak yerine katmanın üzerinde tarafından okunduğu olarak özgün ileti gövdesi XML'deki öbek olanak tanır. `ChunkingReader` bir sıranın nerede arabelleğe alınan öbekleri maksimum yapılandırılabilir sayıya kadar gelen Öbek arabelleği vardır. Bu sınırına ulaşıldığında, okuyucu iletileri sıradan yukarıdaki katmanı tarafından boşaltmış bekler (diğer bir deyişle, yalnızca özgün ileti gövdesinden okuyarak) veya maksimum alacak kadar zaman aşımı ulaştı.  
  
 ![Öbekleme kanalı](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Programlama modeli Öbekleme  
 Hizmet geliştiricileri, hangi iletilerin uygulayarak öbekli üzeresiniz belirtebilirsiniz `ChunkingBehavior` sözleşme işlemlerini özniteliği. Öznitelik kullanıma sunan bir `AppliesTo` Öbekleme giriş iletisi, çıktı iletisi veya her ikisi de geçerli olup olmadığını belirlemek Geliştirici imkan tanıyan özellik. Aşağıdaki örnek kullanımını gösterir `ChunkingBehavior` özniteliği:  
  
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
  
 Bu programlama modelden `ChunkingBindingElement` eylem öbekli iletileri tanımlamak URI'ler listesini derler. Eylem giden her iletinin ileti öbekli doğrudan gönderilen olmadığını belirlemek için bu listeyi karşı karşılaştırılır.  
  
## <a name="implementing-the-send-operation"></a>Gönderme işlemi uygulama  
 Yüksek düzeyde, gönderme işlemi ilk giden ileti öbekli gerekir değilse, iç kanal kullanarak doğrudan ileti gönderir olup olmadığını denetler ve.  
  
 İleti öbekli, gönderme yeni bir oluşturur `ChunkingWriter` ve çağrıları `WriteBodyContents` giden ileti üzerinde bu geçirme `ChunkingWriter`. `ChunkingWriter` (Özgün ileti üstbilgilerini başlangıç öbek iletiye kopyalama dahil) ileti Öbekleme yapar ve iç kanalı kullanılarak öbekleri gönderir.  
  
 Eşitlenmeyeceği birkaç ayrıntıları:  
  
-   İlk çağrıları Gönder `ThrowIfDisposedOrNotOpened` emin olmak için `CommunicationState` açılır.  
  
-   Her oturum için bir defada yalnızca bir iletinin gönderilmesi için gönderme eşitlenir. Var olan bir `ManualResetEvent` adlı `sendingDone` öbekli bir ileti gönderildiğinde sıfırlanır. Son öbek ileti gönderildikten sonra bu olay ayarlanır. Send yöntemi giden ileti göndermeye çalışmadan önce ayarlamak bu olay için bekler.  
  
-   Kilitleri Gönder `CommunicationObject.ThisLock` önlemek için eşitleme durumu değişiklikleri gönderilirken. Bkz: <xref:System.ServiceModel.Channels.CommunicationObject> hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.CommunicationObject> durumları ve Durum makinesi.  
  
-   Gönderme geçirilen zaman aşımı tüm öbek gönderme içeren tüm gönderme işlemi için zaman aşımı olarak kullanılır.  
  
-   Özel `XmlDictionaryWriter` tasarım tüm özgün ileti gövdesini arabelleğe almayı önlemek için seçildi. Alınacak olsaydı bir `XmlDictionaryReader` gövde kullanma `message.GetReaderAtBodyContents` tüm gövdesinin arabelleğe. Bunun yerine, özel bir sahibiz `XmlDictionaryWriter` için geçirilen `message.WriteBodyContents`. İletiyi olarak iç kanal yazıcıda yazan WriteBase64 iletileri parçalara paketleri ve bunları gönderir çağrılarını kullanarak. Öbek gönderilene kadar WriteBase64 engeller.  
  
## <a name="implementing-the-receive-operation"></a>Uygulama alma işlemi  
 Yüksek bir düzeyde alma işlemi önce gelen ileti olmadığını denetler `null` ve kendi eylem olan `ChunkingAction`. Her iki ölçütleri karşılamıyorsa, ileti alma değişmeden döndürülür. Aksi takdirde alma yeni bir oluşturur `ChunkingReader` ve yeni bir `ChunkingMessage` etrafında kaydırılan (çağırarak `GetNewChunkingMessage`). Bu yeni dönmeden önce `ChunkingMessage`, alma yürütmek için bir iş parçacığı havuzu iş parçacığı kullanan `ReceiveChunkLoop`, çağıran `innerChannel.Receive` bir döngü ve öbekleri için ellerini `ChunkingReader` son öbek ileti alındığında veya alma işlemi zaman aşımı isabet kadar.  
  
 Eşitlenmeyeceği birkaç ayrıntıları:  
  
-   Gönderme gibi ilk çağrıları alma `ThrowIfDisposedOrNotOepned` emin olmak için `CommunicationState` açılır.  
  
-   Alma oturumundan bir seferde yalnızca tek bir iletiyi alınabilmesi için de eşitlenir. Başlangıç öbek iletisi alındığında, tüm sonraki alınan iletileri son öbek iletisine alınana kadar bu yeni öbek sırası içinde öbekleri olması beklenen olmadığından bu seçenek özellikle önemlidir. Alma şu anda XML'deki öbekli ileti ait öbeklerin tümü alınana kadar iç kanaldan iletiler çekme olamaz. Bunu gerçekleştirmek için kullandığı alma bir `ManualResetEvent` adlı `currentMessageCompleted`, son öbek ileti aldı ve yeni bir başlangıç öbek iletisi alındığında sıfırlama ayarlayın.  
  
-   Gönder, alma alma sırasında eşitlenmiş durumu geçişleri engellemez. Örneğin, Kapat alma ve bekler sırasında özgün iletinin bekleyen alma tamamlandı veya belirtilen zaman aşımı değerine ulaşılana kadar çağrılabilir.  
  
-   Tüm için zaman aşımı alma gibi tüm öbek almayı içeren işlemi Al geçirilen zaman aşımı kullanılır.  
  
-   İleti tüketir katman gelen öbek iletileri hızından daha düşük bir hızda ileti gövdesi kullanıp kullanmadığına `ChunkingReader` tarafından belirtilen sınıra kadar bu gelen Öbek arabelleği `ChunkingBindingElement.MaxBufferedChunks`. Bu sınıra ulaşıldığında, öbeği arabelleğe alınan bir öbek tüketilen ya da alma zaman aşımı ulaşılana kadar düşük katmandan alınır.  
  
## <a name="communicationobject-overrides"></a>CommunicationObject geçersiz kılmaları  
  
### <a name="onopen"></a>Açıldığında  
 `OnOpen` çağrıları `innerChannel.Open` iç kanalı açmak için.  
  
### <a name="onclose"></a>OnClose  
 `OnClose` İlk Ayarlar `stopReceive` için `true` göstermek için bekleyen `ReceiveChunkLoop` durdurmak için. Ardından için bekler `receiveStopped``ManualResetEvent`, ayarlanmış ne zaman `ReceiveChunkLoop` durdurur. Varsayılarak `ReceiveChunkLoop` durdurur belirtilen süre içinde `OnClose` çağrıları `innerChannel.Close` kalan zaman aşımı ile.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` çağrıları `innerChannel.Abort` iç kanal durdurulacak. Varsa bir bekleyen `ReceiveChunkLoop` özel durumu alır bekleyen `innerChannel.Receive` çağırın.  
  
### <a name="onfaulted"></a>OnFaulted  
 `ChunkingChannel` Kanal olduğunda özel davranış hatalı bunu gerektirmez `OnFaulted` değil geçersiz kılınır.  
  
## <a name="implementing-channel-factory"></a>Kanal fabrikası uygulama  
 `ChunkingChannelFactory` Örneğini oluşturmaktan sorumlu `ChunkingDuplexSessionChannel` ve iç kanal fabrikası için basamaklı durumu geçişleri için.  
  
 `OnCreateChannel` İç kanal fabrikası oluşturmak için kullandığı bir `IDuplexSessionChannel` iç kanal. Ardından yeni bir oluşturur `ChunkingDuplexSessionChannel` öbekli için ileti eylemleri ve öbekleri alma arabellek sayısı listesi yanı sıra iç bu kanal geçirme. Öbekli için ileti eylemleri ve öbekleri arabellek sayısı listesi verilmiştir geçirilen iki parametre `ChunkingChannelFactory` kendi oluşturucusuna. Bölüm `ChunkingBindingElement` bu değerleri alınacağı yeri açıklar.  
  
 `OnOpen`, `OnClose`, `OnAbort` Ve zaman uyumsuz eşdeğerlerine iç kanal fabrikası karşılık gelen durum geçiş yöntemini çağırın.  
  
## <a name="implementing-channel-listener"></a>Kanal dinleyicisi uygulama  
 `ChunkingChannelListener` Olan bir iç kanal dinleyicisi çevresinde bir sarmalayıcı. Yeni kaydırmak için o iç kanal dinleyicisi temsilci çağrılarını yanı sıra ana işlevi olan `ChunkingDuplexSessionChannels` iç kanal dinleyicisi kabul kanalları geçici. Bu yapılır `OnAcceptChannel` ve `OnEndAcceptChannel`. Yeni oluşturulan `ChunkingDuplexSessionChannel` iç kanal daha önce açıklanan diğer parametreleri birlikte geçirilir.  
  
## <a name="implementing-binding-element-and-binding"></a>Uygulama bağlama öğesi ve bağlama  
 `ChunkingBindingElement` oluşturmaktan sorumlu `ChunkingChannelFactory` ve `ChunkingChannelListener`. `ChunkingBindingElement` Denetler olup olmadığını T `CanBuildChannelFactory` \<T > ve `CanBuildChannelListener` \<T > türünde `IDuplexSessionChannel` (yalnızca kanalı kümeleme kanalı tarafından desteklenen) ve bağlamayı diğer bağlama öğeleri bu destek Kanal türü.  
  
 `BuildChannelFactory`\<T > ilk denetler istenen kanal türü oluşturulabilir ve öbekli için ileti eylemlerin bir listesini alır. Daha fazla bilgi için aşağıdaki bölümüne bakın. Ardından yeni bir oluşturur `ChunkingChannelFactory` iç kanal fabrikası geçirme (döndürülen gibi `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), ileti Eylemler ve öbekleri arabellek sayısı listesi. Öbek sayısı olarak adlandırılan bir özellikten gelen `MaxBufferedChunks` tarafından sunulan `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>` oluşturma için benzer bir uygulamaya sahip `ChunkingChannelListener` ve iç kanal dinleyicisi geçirme.  
  
 Adlı bu örnek dahil bir örnek bağlama yok `TcpChunkingBinding`. Bu bağlamanın iki bağlama öğelerden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement`. Gösterme yanı sıra `MaxBufferedChunks` özelliği, bağlama ayrıca ayarlar bazı `TcpTransportBindingElement` gibi özellikler `MaxReceivedMessageSize` (ayarlar `ChunkingUtils.ChunkSize` + üstbilgileri için 100 KB bayt).  
  
 `TcpChunkingBinding` Ayrıca uygulayan `IBindingRuntimePreferences` gelen true değerini döndürür `ReceiveSynchronously` yalnızca zaman uyumlu alma çağrıları uyguladığını gösteren yöntemi.  
  
### <a name="determining-which-messages-to-chunk"></a>Hangi öbeğe iletileri belirleme  
 Kümeleme kanal üzerinden tanımlanan iletileri chunks `ChunkingBehavior` özniteliği. `ChunkingBehavior` Uygulayan sınıf `IOperationBehavior` ve çağırarak uygulanmıştır `AddBindingParameter` yöntemi. Bu yöntemde, `ChunkingBehavior` değerini inceler, `AppliesTo` özelliği (`InMessage`, `OutMessage` veya her ikisini de) hangi iletilerin öbekli belirlemek için. Ardından her bu iletiler bir eylemi alır (üzerinde iletileri koleksiyonundan `OperationDescription`) ve örneği içinde yer alan bir dize koleksiyonuna ekler `ChunkingBindingParameter`. Bunu daha sonra bu ekler `ChunkingBindingParameter` için sağlanan `BindingParameterCollection`.  
  
 Bu `BindingParameterCollection` içinde geçirilen `BindingContext` her bağlama öğesine bu bağlama öğesi kanal fabrikası veya kanal dinleyicisi oluşturduğunda bağlama. `ChunkingBindingElement`'S uyarlamasını `BuildChannelFactory<T>` ve `BuildChannelListener<T>` bu çekme `ChunkingBindingParameter` dışı `BindingContext’`s `BindingParameterCollection`. İçinde bulunan Eylemler koleksiyonunu `ChunkingBindingParameter` sonra geçirilen `ChunkingChannelFactory` veya `ChunkingChannelListener`, hangi sırayla geçirir kendisine `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Service.exe önce çalıştırın, ardından Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleyin.  
  
 Örnek çalıştırırken aşağıdaki çıkış beklenir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.
