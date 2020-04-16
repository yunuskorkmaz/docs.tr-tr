---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7b436e2ce708a122a7eae3b07ad01515fb2dce96
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463972"
---
# <a name="chunking-channel"></a>Öbekleme Kanalı

Windows Communication Foundation (WCF) kullanarak büyük iletiler gönderirken, genellikle bu iletileri arabelleğe almak için kullanılan bellek miktarını sınırlamak istenir. Olası bir çözüm ileti gövdesini akış (verilerin büyük bir kısmının gövdede olduğunu varsayarak). Ancak bazı protokoller tüm iletinin arabelleğe alınmasını gerektirir. Güvenilir mesajlaşma ve güvenlik bu iki örnektir. Başka bir olası çözüm, büyük iletiyi parçalar olarak adlandırılan daha küçük iletilere bölmek, bu parçaları her seferinde bir yığın göndermek ve büyük iletiyi alıcı tarafta yeniden oluşturmaktır. Uygulamanın kendisi bu yığın ve de-chunking yapabilir veya bunu yapmak için özel bir kanal kullanabilirsiniz. Chunking kanal örneği, özel bir protokolün veya katmanlı kanalın rasgele büyük iletilerin öğrlemeyi ve parçalarını ayrıştma yapmak için nasıl kullanılabileceğini gösterir.

Chunking her zaman yalnızca gönderilecek tüm ileti oluşturulduktan sonra kullanılmalıdır. Bir yığın kanalı her zaman bir güvenlik kanalı nın ve güvenilir bir oturum kanalının altına katmanlanmalıdır.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Kanal Varsayımlarını ve Sınırlamalarını Parçalama

### <a name="message-structure"></a>İleti Yapısı

Yığın kanalı, iletilerin parçalanması için aşağıdaki ileti yapısını varsayar:

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

ServiceModel'i kullanırken, 1 giriş parametresi olan sözleşme işlemleri, giriş iletisi için bu ileti şekline uygundur. Benzer şekilde, 1 çıktı parametresi veya iade değeri olan sözleşme işlemleri, çıktı iletisi için bu ileti şekline uygundur. Bu tür işlemlere örnekler aşağıda verilmiştir:

```csharp
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

Yığın kanalı, iletilerin (öbek) sırayla teslim edilmesinde iletilerin tam olarak bir kez teslim edilmesini gerektirir. Bu, temel kanal yığınının oturum dolusu olması gerektiği anlamına gelir. Oturumlar aktarım (örneğin, TCP aktarım) veya oturum lu bir protokol kanalı (örneğin, ReliableSession kanalı) tarafından sağlanabilir.

### <a name="asynchronous-send-and-receive"></a>Asynchronous Gönder ve Al

Asynchronous gönderme ve alma yöntemleri, yığın kanalı örneğinin bu sürümünde uygulanmaz.

## <a name="chunking-protocol"></a>Parçalama Protokolü

Yığın kanalı, bir dizi parçanın başlangıç ve sonunu ve her bir parçanın sıra numarasını gösteren bir protokol tanımlar. Aşağıdaki üç örnek ileti, her birinin temel yönlerini açıklayan açıklamalarla başlangıç, öbek ve bitiş iletilerini gösterir.

### <a name="start-message"></a>İletiyi Başlat

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

### <a name="chunk-message"></a>Öbek İletisi

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

### <a name="end-message"></a>İletiyi Sonla

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

## <a name="chunking-channel-architecture"></a>Chunking Kanal Mimarisi

Chunking kanalı, `IDuplexSessionChannel` yüksek düzeyde, tipik kanal mimarisini izleyen bir kanaldır. Bir ve `ChunkingBindingElement` bir `ChunkingChannelFactory` inşa edebilirsiniz bir `ChunkingChannelListener`. `ChunkingChannel` İstendiğinde `ChunkingChannelFactory` örnekler oluşturur. Yeni `ChunkingChannelListener` bir iç `ChunkingChannel` kanal kabul edildiğinde örnekler oluşturur. İletilerin `ChunkingChannel` gönderilmesi nden ve alınmasından kendisi sorumludur.

Bir sonraki düzeyde `ChunkingChannel` aşağı, parçalama protokolü uygulamak için çeşitli bileşenlere dayanır. Gönder tarafında, kanal gerçek ötme yapan bir özel <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` kullanır. `ChunkingWriter`parçaları göndermek için doğrudan iç kanalı kullanır. Bir özel `XmlDictionaryWriter` kullanarak bize orijinal iletinin büyük gövdesi yazılı olarak parçalar göndermek için izin verir. Bu, özgün iletinin tamamını arabelleğe almadığımız anlamına gelir.

![Yığın lama kanalını gösteren diyagram mimari gönder.](./media/chunking-channel/chunking-channel-send.gif)

Alma tarafında, `ChunkingChannel` iletileri iç kanaldan çeker ve gelen <xref:System.Xml.XmlDictionaryReader> parçalardan gelen orijinal iletiyi yeniden oluşturan `ChunkingReader`özel bir özele teslim eder. `ChunkingChannel`bu `ChunkingReader` özel bir `Message` uygulama `ChunkingMessage` denir sarar ve yukarıdaki katmana bu iletiyi döndürür. Bu kombinasyon `ChunkingReader` `ChunkingMessage` ve bize tüm orijinal ileti gövdesi arabelleğe almak zorunda yerine yukarıdaki katman tarafından okunuyor gibi orijinal ileti gövdesi de-chunk sağlar. `ChunkingReader`en fazla yapılandırılmış arabellekli parça sayısına kadar gelen parçaları arabelleğe aldığı bir kuyruğa sahiptir. Bu maksimum sınıra ulaşıldığında, okuyucu iletilerin yukarıdaki katman tarafından (diğer bir şekilde orijinal ileti gövdesinden okunarak) veya maksimum alma zaman aşımına ulaşılAna kadar sıradan boşaltılmasını bekler.

![Yığın kanalını gösteren diyagram mimari alır.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Chunking Programlama Modeli

Hizmet geliştiriciler, sözleşme içindeki işlemlere öznitelik uygulayarak `ChunkingBehavior` hangi iletilerin ödeneceğini belirtebilir. Öznitelik, geliştiricinin `AppliesTo` öbeklemenin giriş iletisi, çıktı iletisi veya her ikisi için de geçerli olup olmadığını belirtmesine olanak tanıyan bir özelliği ortaya çıkarır. Aşağıdaki örnek, öznitelik `ChunkingBehavior` kullanımını gösterir:

```csharp
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

Bu programlama modelinden, `ChunkingBindingElement` ödenecek iletileri tanımlayan bir eylem UUI listesi derler. Giden her iletinin eylemi, iletinin parçalanmış mı yoksa doğrudan gönderilmesi mi gerektiğini belirlemek için bu listeyle karşılaştırılır.

## <a name="implementing-the-send-operation"></a>Gönderme İşleminin Uygulanması

Yüksek düzeyde, Gönderen işlemi önce giden iletinin parçalanıp tıkanması gerekmediğini denetler ve değilse, iletiyi doğrudan iç kanalı kullanarak gönderir.

İletinin parçalanmış olması gerekiyorsa, Gönder `ChunkingWriter` yeni `WriteBodyContents` bir oluşturma ve bu `ChunkingWriter`iletiyi geçen giden iletiyi çağırır. Daha `ChunkingWriter` sonra ileti ödenebilir (başlangıç öbek iletisine özgün ileti üstbilgilerinin kopyalanması dahil) yapar ve iç kanalı kullanarak öbek gönderir.

Kayda değer birkaç ayrıntı:

- Açıldığından `CommunicationState` `ThrowIfDisposedOrNotOpened` emin olmak için ilk aramaları gönderin.

- Gönderme, her oturum için aynı anda yalnızca bir ileti gönderilebilmek için eşitlenir. Bir yığın `ManualResetEvent` `sendingDone` ileti gönderilirken sıfırlanan bir ad vardır. Son öbek iletisi gönderildikten sonra, bu olay ayarlanır. Gönder yöntemi, giden iletiyi göndermeye çalışır önce bu olayın ayarını bekler.

- Gönderirken `CommunicationObject.ThisLock` eşitlenmiş durum değişikliklerini önlemek için kilitleri gönder. Durumlar <xref:System.ServiceModel.Channels.CommunicationObject> ve durum makinesi <xref:System.ServiceModel.Channels.CommunicationObject> hakkında daha fazla bilgi için belgelere bakın.

- Gönder'e geçirilen zaman aşımı, tüm parçaları göndermeyi içeren tüm gönderme işlemi için zaman aşımı olarak kullanılır.

- Özel <xref:System.Xml.XmlDictionaryWriter> tasarım, tüm orijinal ileti gövdesinin arabelleğe alınışını önlemek için seçildi. Eğer tüm vücudu <xref:System.Xml.XmlDictionaryReader> kullanarak `message.GetReaderAtBodyContents` bir ceset alırsanız tamponlanmış oluruz. Bunun yerine, biz <xref:System.Xml.XmlDictionaryWriter> geçirilen bir `message.WriteBodyContents`özel var. İleti yazarüzerinde WriteBase64 çağırır gibi, yazar mesajları içine yığınlar kadar paketleri ve iç kanalı kullanarak gönderir. Yığın gönderilene kadar Base64 bloklarını yazın.

## <a name="implementing-the-receive-operation"></a>Alma İşleminin Uygulanması

Yüksek düzeyde, Alma işlemi ilk olarak gelen iletinin `null` olmadığını ve eyleminin `ChunkingAction`. Her iki ölçüte de uymuyorsa, ileti Receive'tan değiştirilmeden döndürülür. Aksi takdirde, Receive `ChunkingReader` yeni ve `ChunkingMessage` yeni bir sarılmış `GetNewChunkingMessage`(arayarak) oluşturur. Bu yeni `ChunkingMessage`döndürmeden önce , Receive yürütmek `ReceiveChunkLoop`için `innerChannel.Receive` bir threadpool iş parçacığı kullanır `ChunkingReader` , bir döngü içinde çağırır ve son yığın iletisi alınana veya alma zaman acısı isabet kadar parçaları kapalı eller.

Kayda değer birkaç ayrıntı:

- Gönder gibi, Açıldığından `ThrowIfDisposedOrNotOepned` `CommunicationState` emin olmak için ilk çağrıları alın.

- Alma, oturumdan aynı anda yalnızca bir ileti alınabilmesi için eşitlenir. Bu özellikle önemlidir, çünkü bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm iletilerin bir son öbek iletisi alınana kadar bu yeni yığın dizisi içinde parçalar olması beklenir. İletiye ait tüm parçalar şu anda parçalanan ileti ye gelene kadar iç kanaldan ileti çekemez. Bunu gerçekleştirmek için, `ManualResetEvent` Receive, son öbek iletisi alındığı zaman ayarlanan ve yeni bir başlangıç öycesi iletisi aldığında sıfırlanan bir adlandırılmış `currentMessageCompleted`kullanır.

- Gönder'in aksine, Receive alırken eşitlenmiş durum geçişlerini engellemez. Örneğin, teslim alırken Kapat çağrılabilir ve özgün iletinin bekleyen alabilmesi tamamlanana veya belirtilen zaman sonu değerine ulaşılAna kadar bekleyebilir.

- Receive için geçirilen zaman aşımı, tüm parçaları almayı içeren tüm alma işlemi için zaman aşımı olarak kullanılır.

- İletiyi tüketen katman ileti gövdesini gelen öbek iletilerinin hızından daha düşük bir `ChunkingReader` oranda tüketiyorsa, gelen öbek, gelen öbek'leri ' tarafından `ChunkingBindingElement.MaxBufferedChunks`belirtilen sınıra kadar arabellek Bu sınıra ulaşıldıktan sonra, arabelleğe alınan bir yığın tüketilene veya alma zaman aşıntısına ulaşılına kadar alt katmandan başka parça çekilmez.

## <a name="communicationobject-overrides"></a>İletişimNesne Geçersiz Kılma

### <a name="onopen"></a>Açık Açık

`OnOpen`iç `innerChannel.Open` kanalı açmak için çağırır.

### <a name="onclose"></a>Onclose

`OnClose`durdurmak `stopReceive` için `true` bekleyen `ReceiveChunkLoop` sinyal için ilk ayarlar. Daha sonra durur `receiveStopped` <xref:System.Threading.ManualResetEvent>ayarlanır `ReceiveChunkLoop` , bekler. Belirtilen `ReceiveChunkLoop` zaman anına kadar `OnClose` `innerChannel.Close` durakları varsayarsak, kalan zaman amıyla çağırır.

### <a name="onabort"></a>Onabort

`OnAbort`iç `innerChannel.Abort` kanalı iptal etmek için çağırır. Bekleyen `ReceiveChunkLoop` bir arama varsa, bekleyen `innerChannel.Receive` aramadan bir özel durum alır.

### <a name="onfaulted"></a>Hatalı

Kanal `ChunkingChannel` arızalandığında özel davranış gerektirmez, bu `OnFaulted` nedenle geçersiz kılınmaz.

## <a name="implementing-channel-factory"></a>Kanal Fabrikası'nın Uygulanması

İç `ChunkingChannelFactory` kanal fabrikasına `ChunkingDuplexSessionChannel` devlet geçişlerinin örneklerini oluşturmaktan ve basamaklamadurumundan sorumludur.

`OnCreateChannel`bir `IDuplexSessionChannel` iç kanal oluşturmak için iç kanal fabrikasını kullanır. Daha sonra, bu `ChunkingDuplexSessionChannel` iç kanalda, ötülecek ileti eylemlerinin listesi ve aldıktan sonra arabelleğe alınacak en fazla parça sayısı yla birlikte yeni bir geçiş oluşturur. Parçalanacak ileti eylemlerinin listesi ve arabellek için kullanılacak en fazla parça `ChunkingChannelFactory` sayısı, oluşturucusunda geçirilen iki parametredir. Bu `ChunkingBindingElement` değerlerin nereden geldiğini açıklayan bölüm.

, `OnOpen` `OnClose` `OnAbort` ve onların eşzamanlı eşdeğerleri iç kanal fabrikasında karşılık gelen durum geçiş yöntemi ni çağırır.

## <a name="implementing-channel-listener"></a>Kanal Dinleyicisi Uygulama

Bir `ChunkingChannelListener` iç kanal dinleyici etrafında bir sarmalayıcı. Ana işlevi, bu iç kanal dinleyiciiçin delege çağrıları `ChunkingDuplexSessionChannels` yanı sıra, iç kanal dinleyici kabul kanalları etrafında yeni sarmak için. Bu yapılır `OnAcceptChannel` ve `OnEndAcceptChannel`. Yeni oluşturulan `ChunkingDuplexSessionChannel` daha önce açıklanan diğer parametrelerile birlikte iç kanal geçirilir.

## <a name="implementing-binding-element-and-binding"></a>Bağlama Öğesi nin Uygulanması ve Bağlama

`ChunkingBindingElement`oluşturmaktan sorumludur `ChunkingChannelFactory` ve `ChunkingChannelListener`. T `ChunkingBindingElement`> ve `CanBuildChannelFactory` \< `CanBuildChannelListener` \<T>'daki T'nin türde `IDuplexSessionChannel` olup olmadığını (öbeklenme kanalı tarafından desteklenen tek kanal) ve bağlamadaki diğer bağlama öğelerinin bu kanal türünü desteklediğini denetler.

`BuildChannelFactory`\<T> önce istenen kanal türünün oluşturulabileceğini denetler ve ardından parçalanacak ileti eylemlerinin listesini alır. Daha fazla bilgi için aşağıdaki bölüme bakın. Daha sonra yeni `ChunkingChannelFactory` bir geçiş o iç kanal `context.BuildInnerChannelFactory<IDuplexSessionChannel>`fabrika (döndürülen), ileti eylemleri listesi ve arabellek için parçaların maksimum sayısı oluşturur. En fazla parça `MaxBufferedChunks` `ChunkingBindingElement`sayısı, 'nin maruz kalan özelliğinden gelir.

`BuildChannelListener<T>`oluşturmak `ChunkingChannelListener` ve iç kanal dinleyici geçmek için benzer bir uygulama vardır.

Bu örnekte .. `TcpChunkingBinding` Bu bağlama iki bağlayıcı `TcpTransportBindingElement` öğeden oluşur: ve `ChunkingBindingElement`. Özelliği açığa çıkarmanın `MaxBufferedChunks` yanı sıra, bağlama gibi `TcpTransportBindingElement` bazı `MaxReceivedMessageSize` özellikleri de `ChunkingUtils.ChunkSize` ayarlar (üstbilgi için + 100KB bayt ayarlar).

`TcpChunkingBinding`ayrıca yalnızca `IBindingRuntimePreferences` senkron Receive `ReceiveSynchronously` çağrılarının uygulandığını belirten yöntemden doğru olarak uygular ve döndürür.

### <a name="determining-which-messages-to-chunk"></a>Hangi İletilerin Öbek Olarak Belirlene

Yığın kanalı yalnızca öznitelik üzerinden `ChunkingBehavior` tanımlanan iletileri parçalar. Sınıf `ChunkingBehavior` uygular `IOperationBehavior` ve `AddBindingParameter` yöntemi çağırarak uygulanır. Bu yöntemde, `ChunkingBehavior` hangi iletilerin `AppliesTo` parçalanılması gerektiğini belirlemek için özelliğinin`InMessage` `OutMessage` (veya her ikisinin) değerini inceler. Daha sonra bu iletilerin her birinin eylemini alır `OperationDescription`(Üzerindeki İletiler koleksiyonundan) ve bir `ChunkingBindingParameter`örnek içinde bulunan bir dize koleksiyonuna ekler. Daha sonra `ChunkingBindingParameter` sağlanan `BindingParameterCollection`bu ekler.

Bu `BindingParameterCollection` bağlama öğesi `BindingContext` kanal fabrikası veya kanal dinleyici oluşturur zaman bağlama her bağlayıcı öğe içinde geçirilir. 'uygulama `ChunkingBindingElement` `BuildChannelFactory<T>` ve `BuildChannelListener<T>` `ChunkingBindingParameter` `BindingContext’`s `BindingParameterCollection`bu çekin . İçinde `ChunkingBindingParameter` yer alan eylemlerin toplanması daha `ChunkingChannelFactory` sonra `ChunkingChannelListener`ya da , sırayla geçer `ChunkingDuplexSessionChannel`.

## <a name="running-the-sample"></a>Örneği Çalıştırma

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

3. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.

5. Önce Service.exe'yi çalıştırın, sonra Client.exe'yi çalıştırın ve çıktı için her iki konsol penceresini de izleyin.

Örneği çalıştırırken, aşağıdaki çıktı bekleniyor.

İstemci:

```console
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

```console
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
