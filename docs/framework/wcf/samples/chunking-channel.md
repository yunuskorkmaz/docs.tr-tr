---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: b59f5c42f5a0f81f666bc5d22924f14c678a60e1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045708"
---
# <a name="chunking-channel"></a>Öbekleme Kanalı

Windows Communication Foundation (WCF) kullanarak büyük iletiler gönderirken, bu iletileri arabelleğe almak için kullanılan bellek miktarının sınırlanmasından genellikle tercih edilir. Olası bir çözüm, ileti gövdesinin akışını (verilerin toplu olarak gövdesinde olduğu varsayıldığında) sağlar. Ancak bazı protokollerin iletinin tamamının arabelleğe alınması gerekir. Güvenilir Mesajlaşma ve güvenlik iki tür örnektir. Diğer bir olası çözüm de büyük iletiyi öbek adı verilen küçük iletilere bölmek, bu öbekleri tek seferde bir öbek göndermek ve alma tarafında büyük iletiyi edilmeyen. Uygulamanın kendisi bu parçalama ve parçalama işlemlerini yapmak için özel bir kanal kullanabilir. Öbek oluşturma kanalı örneği, özel bir protokol veya katmanlı kanalın, rastgele büyük iletileri parçalama ve parçalama için nasıl kullanılabileceğini gösterir.

Parçalama her zaman yalnızca gönderilecek iletinin tamamı oluşturulduktan sonra kullanılmalıdır. Bir parçalama kanalının her zaman bir güvenlik kanalının ve güvenilir bir oturum kanalının altında katmanlanmış olması gerekir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Kanal varsayımları ve sınırlamaları parçalama

### <a name="message-structure"></a>İleti yapısı

Öbek oluşturma kanalı, iletilerin öbeklenmesini sağlamak için aşağıdaki ileti yapısını varsayar:

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

ServiceModel kullanılırken, 1 girdi parametresine sahip sözleşme işlemleri giriş iletileri için bu ileti şekliyle uyumlu olmalıdır. Benzer şekilde, 1 çıkış parametresi veya dönüş değeri olan sözleşme işlemleri, çıkış iletileri için bu ileti şekliyle uyumlu değildir. Bu tür işlemlere örnekler aşağıda verilmiştir:

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

Öbek oluşturma kanalı, iletilerin sıralı iletiler (öbekler) tesliminde tam olarak bir kez teslim edilmesini gerektirir. Bu, temeldeki kanal yığınının oturumsuz olması gerektiği anlamına gelir. Oturumlar, taşıma (örneğin, TCP aktarımı) veya bir oturum Protokolü kanalı (örneğin, Reliableoturum kanalı) tarafından sağlanırlar.

### <a name="asynchronous-send-and-receive"></a>Zaman uyumsuz gönderme ve alma

Zaman uyumsuz gönderme ve alma yöntemleri, parçalama kanalı örneğinin bu sürümünde uygulanmaz.

## <a name="chunking-protocol"></a>Kümeleme Protokolü

Öbek oluşturma kanalı, bir dizi öbekin başlangıcını ve sonunu ve her öbekin sıra numarasını belirten bir protokol tanımlar. Aşağıdaki üç örnek ileti, her birinin ana yönlerini tanımlayan yorumlarla başlangıç, öbek ve son iletileri gösterir.

### <a name="start-message"></a>Iletiyi Başlat

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

### <a name="chunk-message"></a>Öbek Iletisi

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

### <a name="end-message"></a>Bitiş Iletisi

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

## <a name="chunking-channel-architecture"></a>Parçalama kanalı mimarisi

Öbek oluşturma kanalı, yüksek düzeyde `IDuplexSessionChannel` olan ve tipik kanal mimarisini izleyen bir düzeydir. `ChunkingChannelFactory` Ve`ChunkingChannelListener`biroluşturabilir. `ChunkingBindingElement` , `ChunkingChannelFactory` İstendiğinde`ChunkingChannel` örnek oluşturur. , `ChunkingChannelListener` Yeni bir iç `ChunkingChannel` kanal kabul edildiğinde örnekleri oluşturur. `ChunkingChannel` Kendi kendine ileti göndermekten ve onlardan sorumlu olur.

Bir sonraki düzeyde, `ChunkingChannel` öbek protokolünü uygulamak için çeşitli bileşenlere bağımlıdır. Gönderme tarafında kanal, gerçek parçalama yapan bir özel <xref:System.Xml.XmlDictionaryWriter> çağırılır. `ChunkingWriter` `ChunkingWriter`öbekleri göndermek için doğrudan iç kanalı kullanır. Özel `XmlDictionaryWriter` kullanmak, özgün iletinin büyük gövdesi yazıldığı için öbekleri göndermemizi sağlar. Bu, tüm özgün iletiyi arabelleğe sunduğumuz anlamına gelir.

![Parçalama kanalı gönderme mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-send.gif)

Alma tarafında, `ChunkingChannel` iç kanaldan iletiler çeker ve bunları gelen öbeklerden özgün iletiyi reconstitutes bir özel <xref:System.Xml.XmlDictionaryReader> çağrıldı `ChunkingReader`. `ChunkingChannel`Bunu `ChunkingReader` `Message` adlı özel`ChunkingMessage` bir uygulamada sarmalanmış ve bu iletiyi yukarıdaki katmana döndürüyor. Bu `ChunkingReader` ve`ChunkingMessage` birleşimi, özgün ileti gövdesinin tüm özgün ileti gövdesini arabelleğe almak yerine yukarıdaki katman tarafından okunmakta olduğundan, özgün ileti gövdesini serbest bırakmamızı sağlar. `ChunkingReader`, gelen öbekleri en fazla yapılandırılabilir sayıda arabelleğe alınmış parçalara kadar arabelleğe aldığı bir kuyruğa sahiptir. Bu en fazla sınıra ulaşıldığında, okuyucu yukarıdaki katmanda bulunan (yani yalnızca özgün ileti gövdesinden okunarak) veya en fazla alma zaman aşımına ulaşılana kadar iletilerin kuyruktan dönmesini bekler.

![Parçalama kanalı alma mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Öbek programlama modeli

Hizmet geliştiricileri, sözleşme içindeki işlemlere `ChunkingBehavior` özniteliği uygulayarak hangi iletilerin öbeklere göre olduğunu belirtebilir. Özniteliği, geliştiricinin giriş `AppliesTo` mesajı, çıkış iletisi veya her ikisi için de parçalama uygulanıp uygulanmadığını belirtmesini sağlayan bir özellik sunar. Aşağıdaki örnek `ChunkingBehavior` özniteliğin kullanımını gösterir:

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

Bu programlama modelinde, `ChunkingBindingElement` iletileri öbekli olacak şekilde tanımlayan eylem URI 'lerinin bir listesini derler. Her giden ileti eylemi, iletinin öbekli olarak mı yoksa doğrudan mi gönderileceğini öğrenmek için bu listeyle karşılaştırılır.

## <a name="implementing-the-send-operation"></a>Gönderme Işlemini uygulama

Yüksek düzeyde, Gönder işlemi önce giden iletinin öbekli olup olmadığını denetler ve yoksa iletiyi doğrudan iç kanalı kullanarak gönderir.

İleti öbekli olması gerekiyorsa, Send bunu geçirerek `ChunkingWriter` `ChunkingWriter`giden iletide yeni bir `WriteBodyContents` ve çağrılar oluşturur. `ChunkingWriter` Ardından ileti öbek (özgün ileti üstbilgilerini başlangıç öbeğiyle kopyalama dahil) ve iç kanalı kullanarak öbekleri gönderir.

Dikkat edilecek bazı ayrıntılar:

- `ThrowIfDisposedOrNotOpened` Açık`CommunicationState` olduğundan emin olmak için ilk çağrıları gönderin.

- Gönderme, her oturum için tek seferde yalnızca bir ileti gönderilebilmesi için eşitlenir. Bir öbekli `ManualResetEvent` ileti `sendingDone` gönderilirken sıfırlanan bir adlandırılmış adı vardır. Öbek iletisi gönderildikten sonra bu olay ayarlanır. Send yöntemi, giden iletiyi göndermeyi denemeden önce bu olayın ayarlanmış olmasını bekler.

- Gönderme, `CommunicationObject.ThisLock` gönderme sırasında eşitlenen durum değişikliklerini engellemek için ' a kilitler. Durumlar ve durum makinesi hakkında <xref:System.ServiceModel.Channels.CommunicationObject> daha fazla bilgi için belgelerebakın.<xref:System.ServiceModel.Channels.CommunicationObject>

- Gönderme için geçirilen zaman aşımı, tüm öbeklerin gönderilmesini içeren gönderme işleminin tamamına yönelik zaman aşımı olarak kullanılır.

- Özel <xref:System.Xml.XmlDictionaryWriter> tasarım, özgün ileti gövdesinin tamamını arabelleğe almayı önlemek için seçildi. Gövdeyi kullanarak `message.GetReaderAtBodyContents` gövdenin tamamını kullanırsanız, tüm gövdenin ara belleğe alınacaksa. <xref:System.Xml.XmlDictionaryReader> Bunun yerine, öğesine <xref:System.Xml.XmlDictionaryWriter> `message.WriteBodyContents`geçirilen özel bir sunuyoruz. İleti, yazıcı üzerinde WriteBase64 çağırdığında, yazıcı paketleri ileti halinde parçalara ayırır ve bunları iç kanalı kullanarak gönderir. WriteBase64 blokları öbek gönderilene kadar engeller.

## <a name="implementing-the-receive-operation"></a>Alma Işlemi uygulama

Yüksek düzeyde, alma işlemi önce gelen iletinin olmadığını `null` ve eyleminin `ChunkingAction`olduğunu denetler. Her iki ölçütü de karşılamıyorsa ileti alma işleminden değişmeden döndürülür. Aksi takdirde, alma yeni `ChunkingReader` bir ve etrafında yeni `ChunkingMessage` bir sarmalanmış oluşturur (çağırarak `GetNewChunkingMessage`). Bu yeni `ChunkingMessage`döndürmeden önce, alma işlemi yürütmek `ReceiveChunkLoop`için bir ThreadPool iş parçacığı kullanır, `innerChannel.Receive` bu, döngü içinde çağrı yapan ve son öbek `ChunkingReader` iletisi alınana veya alma zaman aşımı alınana kadar öbeklerin parçalara geçmesini sağlar.

Dikkat edilecek bazı ayrıntılar:

- Send gibi, açık `ThrowIfDisposedOrNotOepned` `CommunicationState` olduğundan emin olmak için ilk çağrıları alın.

- Alma işlemi, oturumdan bir seferde yalnızca bir ileti alınabilmesi için de eşitlenir. Bu durum, bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm alınan iletilerin, son öbek iletisi alınana kadar bu yeni öbek sırası içinde öbeklerinin olması beklendiğinden özellikle önemlidir. Alma, şu anda öbekli olmayan bir iletiye ait olan tüm parçalar alındığından iç kanaldan ileti çekmez. Bunu gerçekleştirmek için al, yeni bir `ManualResetEvent` öbek `currentMessageCompleted`iletisi alındığında son öbek iletisi alındığında ve sıfırlandığında ayarlanan adlandırılmış bir kullanır.

- Gönderme, alma işleminden farklı olarak alma sırasında eşitlenmiş durum geçişlerini engellemez. Örneğin, alma sırasında çağrılabilir ve özgün iletinin bekleyen alımı tamamlanana veya belirtilen zaman aşımı değerine ulaşılana kadar beklenebilir.

- Alma işlemi sırasında geçen zaman aşımı, tüm öbeklerin alınması dahil olmak üzere tüm alma işlemleri için zaman aşımı olarak kullanılır.

- İletiyi tüketen katman, gelen öbek iletilerinin hızından daha düşük bir hızda ileti gövdesini kullanıyorsa, `ChunkingReader` gelen öbeklerin tarafından `ChunkingBindingElement.MaxBufferedChunks`belirtilen sınıra kadar olan arabelleklerini arabelleğe alır. Bu sınıra ulaşıldığında, arabelleğe alınmış bir öbek tüketilene veya alma zaman aşımına ulaşılana kadar alt katmandan daha fazla öbek çekilmeyen bir değer yoktur.

## <a name="communicationobject-overrides"></a>CommunicationObject geçersiz kılmaları

### <a name="onopen"></a>OnOpen

`OnOpen`iç `innerChannel.Open` kanalı açmak için çağırır.

### <a name="onclose"></a>OnClose

`OnClose`İlk olarak `stopReceive` `true` , durdurmak için bekleyen `ReceiveChunkLoop` ' i işaret etmek üzere ayarlar. Ardından, `receiveStopped` durdurulduğunda`ReceiveChunkLoop` ayarlanan için <xref:System.Threading.ManualResetEvent>bekler. Belirtilen zaman aşımı süresi içinde `OnClose` `innerChannel.Close` durduğu varsayılarak, kalan zaman aşımı ile çağrılar yapılır. `ReceiveChunkLoop`

### <a name="onabort"></a>OnAbort

`OnAbort`iç `innerChannel.Abort` kanalı durdurmak için çağırır. Bekleyen `ReceiveChunkLoop` bir sorun varsa, bekleyen `innerChannel.Receive` çağrıdan bir özel durum alır.

### <a name="onfaulted"></a>Onhatalı

Kanal `ChunkingChannel` hata verdi durumunda özel bir davranış gerektirmez, bu nedenle `OnFaulted` geçersiz kılınmaz.

## <a name="implementing-channel-factory"></a>Kanal fabrikası uygulama

, `ChunkingChannelFactory` İç kanal fabrikasına basamaklı durum `ChunkingDuplexSessionChannel` geçişleri için ve örneklerinin oluşturulmasından sorumludur.

`OnCreateChannel`iç kanal fabrikası oluşturmak `IDuplexSessionChannel` için iç kanal fabrikasını kullanır. Daha sonra bu iç kanalı `ChunkingDuplexSessionChannel` , yığın olarak kullanılacak ileti eylemlerinin listesi ve alma sırasında arabelleğe eklenecek en fazla parça sayısı ile birlikte geçen yeni bir oluşturur. Yığın olarak kullanılacak ileti eylemlerinin listesi ve arabellekteki öbeklerin en fazla sayısı, oluşturucusunda iki parametre olarak geçirilir `ChunkingChannelFactory` . Üzerindeki `ChunkingBindingElement` bölümü, bu değerlerin nereden geldiği açıklanmaktadır.

`OnOpen` ,`OnClose`Ve zamanuyumsuzeşdeğerleri,içkanalfabrikasındakarşılıkgelendurumgeçişyönteminiçağırır.`OnAbort`

## <a name="implementing-channel-listener"></a>Kanal dinleyicisi uygulama

, `ChunkingChannelListener` Bir iç kanal dinleyicisi etrafında bir sarmalayıcıdır. Ana işlevinin, bu iç kanal dinleyicisine yönelik temsilci çağrılarının yanı sıra, iç kanal dinleyicisinden kabul edilen yeni `ChunkingDuplexSessionChannels` kanallar etrafında sarmalaması de vardır. Bu, ve `OnEndAcceptChannel`' `OnAcceptChannel` de yapılır. Yeni oluşturulan `ChunkingDuplexSessionChannel` , daha önce açıklanan diğer parametrelerle birlikte iç kanalı geçti.

## <a name="implementing-binding-element-and-binding"></a>Bağlama öğesi ve bağlamayı uygulama

`ChunkingBindingElement`, `ChunkingChannelFactory` ve`ChunkingChannelListener`oluşturmaktan sorumludur. \< `CanBuildChannelFactory` T>`CanBuildChannelListener`ve `ChunkingBindingElement` t>`IDuplexSessionChannel` 'in türde olup olmadığını denetler (parçalama kanalının desteklediği tek kanal) ve bağlamadaki diğer bağlama öğeleri bunu desteklemelidir \< Kanal türü.

`BuildChannelFactory`\<T > önce istenen kanal türünün oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır. Daha fazla bilgi için aşağıdaki bölüme bakın. Daha sonra, iç kanal `ChunkingChannelFactory` Fabrikası (öğesinden döndürülen), ileti eylemlerinin listesi ve `context.BuildInnerChannelFactory<IDuplexSessionChannel>`arabelleğe alınan en fazla parça sayısı gibi yeni bir geçirme oluşturur. En fazla parça sayısı, `MaxBufferedChunks` `ChunkingBindingElement`tarafından açığa çıkarılan adlı bir özellikten gelir.

`BuildChannelListener<T>`, iç kanal dinleyicisi oluşturma `ChunkingChannelListener` ve geçirme için benzer bir uygulamaya sahiptir.

Bu örneğe `TcpChunkingBinding`eklenen örnek bir bağlama vardır. Bu bağlama iki bağlama öğesinden oluşur: `TcpTransportBindingElement` ve. `ChunkingBindingElement` `MaxBufferedChunks` Özelliği ayarlamanın yanı sıra, bağlama gibi bazı `TcpTransportBindingElement` Özellikler `MaxReceivedMessageSize` de ayarlanır (üst bilgiler için + 100 KB bayt olarak `ChunkingUtils.ChunkSize` ayarlanır).

`TcpChunkingBinding`Ayrıca, `IBindingRuntimePreferences` yalnızca zaman uyumlu alma çağrılarının `ReceiveSynchronously` uygulandığını belirten yönteminden true değerini uygular.

### <a name="determining-which-messages-to-chunk"></a>Hangi Iletileri öbekte belirleme

Öbek oluşturma kanalı yalnızca `ChunkingBehavior` özniteliği aracılığıyla tanımlanan iletileri parçalara parçalar. Sınıfı, yöntemini`AddBindingParameter` çağırarak uygular `IOperationBehavior` ve uygulanır. `ChunkingBehavior` Bu yöntemde, hangi iletilerin `ChunkingBehavior` öbekli olması gerektiğini belirleyen `AppliesTo` , özelliğin`InMessage`değerini `OutMessage` (veya her ikisi) inceler. Daha sonra bu iletilerin her birinin eylemini alır (üzerindeki `OperationDescription`iletiler koleksiyonundan) ve `ChunkingBindingParameter`örneği içinde yer alan bir dize koleksiyonuna ekler. Daha sonra bunu `ChunkingBindingParameter` , belirtilen `BindingParameterCollection`öğesine ekler.

Bu `BindingParameterCollection` , bağlama öğesi kanal `BindingContext` fabrikası veya kanal dinleyicisi oluşturduğunda bağlamadaki her bağlama öğesinin içine geçirilir. `ChunkingBindingElement`' Nin `BuildChannelFactory<T>` uygulanması ve `BuildChannelListener<T>` bu uygulamadan`ChunkingBindingParameter` çekmesi .`BindingContext’` `BindingParameterCollection` İçinde `ChunkingBindingParameter` yer alan eylemlerin koleksiyonu daha sonra `ChunkingChannelFactory` veya `ChunkingChannelListener` `ChunkingDuplexSessionChannel`' a geçirilir ve bu da ' a geçirilir.

## <a name="running-the-sample"></a>Örnek çalıştırma

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

5. Önce Service. exe ' yi çalıştırın, sonra Client. exe ' yi çalıştırın ve çıktı için hem konsol pencerelerini izleyin.

Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.

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

Server

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
