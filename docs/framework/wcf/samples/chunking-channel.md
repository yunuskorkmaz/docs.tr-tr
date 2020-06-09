---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7a5e5292bcb37e83de21458716e34887a0557d91
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585551"
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Kanal varsayımları ve sınırlamaları parçalama

### <a name="message-structure"></a>İleti yapısı

Öbek oluşturma kanalı, iletilerin öbeklenmesini sağlamak için aşağıdaki ileti yapısını varsayar:

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

Öbek oluşturma kanalı, `IDuplexSessionChannel` yüksek düzeyde olan ve tipik kanal mimarisini izleyen bir düzeydir. `ChunkingBindingElement`Ve bir oluşturabilir `ChunkingChannelFactory` `ChunkingChannelListener` . , İstendiğinde `ChunkingChannelFactory` örnek oluşturur `ChunkingChannel` . , `ChunkingChannelListener` `ChunkingChannel` Yeni bir iç kanal kabul edildiğinde örnekleri oluşturur. `ChunkingChannel`Kendi kendine ileti göndermekten ve onlardan sorumlu olur.

Bir sonraki düzeyde, `ChunkingChannel` öbek protokolünü uygulamak için çeşitli bileşenlere bağımlıdır. Gönderme tarafında kanal, <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` gerçek parçalama yapan bir özel çağırılır. `ChunkingWriter`öbekleri göndermek için doğrudan iç kanalı kullanır. Özel kullanmak, `XmlDictionaryWriter` özgün iletinin büyük gövdesi yazıldığı için öbekleri göndermemizi sağlar. Bu, tüm özgün iletiyi arabelleğe sunduğumuz anlamına gelir.

![Parçalama kanalı gönderme mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-send.gif)

Alma tarafında, `ChunkingChannel` iç kanaldan iletiler çeker ve bunları <xref:System.Xml.XmlDictionaryReader> `ChunkingReader` gelen öbeklerden özgün iletiyi reconstitutes bir özel çağrıldı. `ChunkingChannel`Bunu `ChunkingReader` adlı özel bir `Message` uygulamada sarmalanmış `ChunkingMessage` ve bu iletiyi yukarıdaki katmana döndürüyor. Bu ve birleşimi, özgün ileti gövdesinin `ChunkingReader` `ChunkingMessage` tüm özgün ileti gövdesini arabelleğe almak yerine yukarıdaki katman tarafından okunmakta olduğundan, özgün ileti gövdesini serbest bırakmamızı sağlar. `ChunkingReader`, gelen öbekleri en fazla yapılandırılabilir sayıda arabelleğe alınmış parçalara kadar arabelleğe aldığı bir kuyruğa sahiptir. Bu en fazla sınıra ulaşıldığında, okuyucu yukarıdaki katmanda bulunan (yani yalnızca özgün ileti gövdesinden okunarak) veya en fazla alma zaman aşımına ulaşılana kadar iletilerin kuyruktan dönmesini bekler.

![Parçalama kanalı alma mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Öbek programlama modeli

Hizmet geliştiricileri, `ChunkingBehavior` sözleşme içindeki işlemlere özniteliği uygulayarak hangi iletilerin öbeklere göre olduğunu belirtebilir. Özniteliği, `AppliesTo` geliştiricinin giriş mesajı, çıkış iletisi veya her ikisi için de parçalama uygulanıp uygulanmadığını belirtmesini sağlayan bir özellik sunar. Aşağıdaki örnek özniteliğin kullanımını gösterir `ChunkingBehavior` :

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

İleti öbekli olması gerekiyorsa, Send `ChunkingWriter` `WriteBodyContents` bunu geçirerek giden iletide yeni bir ve çağrılar oluşturur `ChunkingWriter` . `ChunkingWriter`Ardından ileti öbek (özgün ileti üstbilgilerini başlangıç öbeğiyle kopyalama dahil) ve iç kanalı kullanarak öbekleri gönderir.

Dikkat edilecek bazı ayrıntılar:

- `ThrowIfDisposedOrNotOpened`Açık olduğundan emin olmak için ilk çağrıları gönderin `CommunicationState` .

- Gönderme, her oturum için tek seferde yalnızca bir ileti gönderilebilmesi için eşitlenir. `ManualResetEvent` `sendingDone` Bir öbekli ileti gönderilirken sıfırlanan bir adlandırılmış adı vardır. Öbek iletisi gönderildikten sonra bu olay ayarlanır. Send yöntemi, giden iletiyi göndermeyi denemeden önce bu olayın ayarlanmış olmasını bekler.

- Gönderme, `CommunicationObject.ThisLock` gönderme sırasında eşitlenen durum değişikliklerini engellemek için ' a kilitler. <xref:System.ServiceModel.Channels.CommunicationObject>Durumlar ve durum makinesi hakkında daha fazla bilgi için belgelere bakın <xref:System.ServiceModel.Channels.CommunicationObject> .

- Gönderme için geçirilen zaman aşımı, tüm öbeklerin gönderilmesini içeren gönderme işleminin tamamına yönelik zaman aşımı olarak kullanılır.

- Özel <xref:System.Xml.XmlDictionaryWriter> Tasarım, özgün ileti gövdesinin tamamını arabelleğe almayı önlemek için seçildi. Gövdeyi <xref:System.Xml.XmlDictionaryReader> kullanarak gövdenin `message.GetReaderAtBodyContents` tamamını kullanırsanız, tüm gövdenin ara belleğe alınacaksa. Bunun yerine, öğesine geçirilen özel bir sunuyoruz <xref:System.Xml.XmlDictionaryWriter> `message.WriteBodyContents` . İleti, yazıcı üzerinde WriteBase64 çağırdığında, yazıcı paketleri ileti halinde parçalara ayırır ve bunları iç kanalı kullanarak gönderir. WriteBase64 blokları öbek gönderilene kadar engeller.

## <a name="implementing-the-receive-operation"></a>Alma Işlemi uygulama

Yüksek düzeyde, alma işlemi önce gelen iletinin olmadığını `null` ve eyleminin olduğunu denetler `ChunkingAction` . Her iki ölçütü de karşılamıyorsa ileti alma işleminden değişmeden döndürülür. Aksi takdirde, alma yeni bir `ChunkingReader` ve etrafında yeni bir `ChunkingMessage` sarmalanmış oluşturur (çağırarak `GetNewChunkingMessage` ). Bu yeni döndürmeden önce `ChunkingMessage` , alma işlemi yürütmek için bir ThreadPool iş parçacığı kullanır, bu, `ReceiveChunkLoop` `innerChannel.Receive` döngü içinde çağrı yapan ve `ChunkingReader` son öbek iletisi alınana veya alma zaman aşımı alınana kadar öbeklerin parçalara geçmesini sağlar.

Dikkat edilecek bazı ayrıntılar:

- Send gibi, `ThrowIfDisposedOrNotOepned` açık olduğundan emin olmak için ilk çağrıları alın `CommunicationState` .

- Alma işlemi, oturumdan bir seferde yalnızca bir ileti alınabilmesi için de eşitlenir. Bu durum, bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm alınan iletilerin, son öbek iletisi alınana kadar bu yeni öbek sırası içinde öbeklerinin olması beklendiğinden özellikle önemlidir. Alma, şu anda öbekli olmayan bir iletiye ait olan tüm parçalar alındığından iç kanaldan ileti çekmez. Bunu gerçekleştirmek için al, yeni bir `ManualResetEvent` `currentMessageCompleted` öbek iletisi alındığında son öbek iletisi alındığında ve sıfırlandığında ayarlanan adlandırılmış bir kullanır.

- Gönderme, alma işleminden farklı olarak alma sırasında eşitlenmiş durum geçişlerini engellemez. Örneğin, alma sırasında çağrılabilir ve özgün iletinin bekleyen alımı tamamlanana veya belirtilen zaman aşımı değerine ulaşılana kadar beklenebilir.

- Alma işlemi sırasında geçen zaman aşımı, tüm öbeklerin alınması dahil olmak üzere tüm alma işlemleri için zaman aşımı olarak kullanılır.

- İletiyi tüketen katman, gelen öbek iletilerinin hızından daha düşük bir hızda ileti gövdesini kullanıyorsa, `ChunkingReader` gelen öbeklerin tarafından belirtilen sınıra kadar olan arabelleklerini arabelleğe alır `ChunkingBindingElement.MaxBufferedChunks` . Bu sınıra ulaşıldığında, arabelleğe alınmış bir öbek tüketilene veya alma zaman aşımına ulaşılana kadar alt katmandan daha fazla öbek çekilmeyen bir değer yoktur.

## <a name="communicationobject-overrides"></a>CommunicationObject geçersiz kılmaları

### <a name="onopen"></a>OnOpen

`OnOpen``innerChannel.Open`iç kanalı açmak için çağırır.

### <a name="onclose"></a>OnClose

`OnClose`ilk `stopReceive` olarak `true` , durdurmak için bekleyen ' i işaret etmek üzere ayarlar `ReceiveChunkLoop` . Ardından, `receiveStopped` <xref:System.Threading.ManualResetEvent> durdurulduğunda ayarlanan için bekler `ReceiveChunkLoop` . `ReceiveChunkLoop`Belirtilen zaman aşımı süresi içinde durduğu varsayılarak, `OnClose` `innerChannel.Close` kalan zaman aşımı ile çağrılar yapılır.

### <a name="onabort"></a>OnAbort

`OnAbort``innerChannel.Abort`iç kanalı durdurmak için çağırır. Bekleyen bir sorun varsa, `ReceiveChunkLoop` bekleyen çağrıdan bir özel durum alır `innerChannel.Receive` .

### <a name="onfaulted"></a>Onhatalı

`ChunkingChannel`Kanal hata verdi durumunda özel bir davranış gerektirmez, bu nedenle `OnFaulted` geçersiz kılınmaz.

## <a name="implementing-channel-factory"></a>Kanal fabrikası uygulama

, `ChunkingChannelFactory` `ChunkingDuplexSessionChannel` İç kanal fabrikasına basamaklı durum geçişleri için ve örneklerinin oluşturulmasından sorumludur.

`OnCreateChannel`iç kanal fabrikası oluşturmak için iç kanal fabrikasını kullanır `IDuplexSessionChannel` . Daha sonra `ChunkingDuplexSessionChannel` Bu iç kanalı, yığın olarak kullanılacak ileti eylemlerinin listesi ve alma sırasında arabelleğe eklenecek en fazla parça sayısı ile birlikte geçen yeni bir oluşturur. Yığın olarak kullanılacak ileti eylemlerinin listesi ve arabellekteki öbeklerin en fazla sayısı, oluşturucusunda iki parametre olarak geçirilir `ChunkingChannelFactory` . Üzerindeki bölümü, `ChunkingBindingElement` Bu değerlerin nereden geldiği açıklanmaktadır.

`OnOpen`, `OnClose` `OnAbort` Ve zaman uyumsuz eşdeğerleri, iç kanal fabrikasında karşılık gelen durum geçiş yöntemini çağırır.

## <a name="implementing-channel-listener"></a>Kanal dinleyicisi uygulama

, Bir `ChunkingChannelListener` iç kanal dinleyicisi etrafında bir sarmalayıcıdır. Ana işlevinin, bu iç kanal dinleyicisine yönelik temsilci çağrılarının yanı sıra, `ChunkingDuplexSessionChannels` iç kanal dinleyicisinden kabul edilen yeni kanallar etrafında sarmalaması de vardır. Bu, ve ' de yapılır `OnAcceptChannel` `OnEndAcceptChannel` . Yeni oluşturulan, `ChunkingDuplexSessionChannel` daha önce açıklanan diğer parametrelerle birlikte iç kanalı geçti.

## <a name="implementing-binding-element-and-binding"></a>Bağlama öğesi ve bağlamayı uygulama

`ChunkingBindingElement`, ve oluşturmaktan sorumludur `ChunkingChannelFactory` `ChunkingChannelListener` . , ' `ChunkingBindingElement` In ve türünde olup olmadığını denetler `CanBuildChannelFactory` \<T> `CanBuildChannelListener` \<T> `IDuplexSessionChannel` (parçalama kanalının desteklediği tek kanal) ve bağlamadaki diğer bağlama öğelerinin bu kanal türünü destekleyip desteklemediğini denetler.

`BuildChannelFactory`\<T>İlk olarak, istenen kanal türünün oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır. Daha fazla bilgi için aşağıdaki bölüme bakın. Daha sonra `ChunkingChannelFactory` , iç kanal fabrikası (öğesinden döndürülen `context.BuildInnerChannelFactory<IDuplexSessionChannel>` ), ileti eylemlerinin listesi ve arabelleğe alınan en fazla parça sayısı gibi yeni bir geçirme oluşturur. En fazla parça sayısı `MaxBufferedChunks` , tarafından açığa çıkarılan adlı bir özellikten gelir `ChunkingBindingElement` .

`BuildChannelListener<T>`, `ChunkingChannelListener` iç kanal dinleyicisi oluşturma ve geçirme için benzer bir uygulamaya sahiptir.

Bu örneğe eklenen örnek bir bağlama vardır `TcpChunkingBinding` . Bu bağlama iki bağlama öğesinden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement` . Özelliği ayarlamanın yanı sıra `MaxBufferedChunks` , bağlama gibi bazı özellikler de ayarlanır `TcpTransportBindingElement` `MaxReceivedMessageSize` ( `ChunkingUtils.ChunkSize` üst bilgiler için + 100 KB bayt olarak ayarlanır).

`TcpChunkingBinding`Ayrıca `IBindingRuntimePreferences` `ReceiveSynchronously` , yalnızca zaman uyumlu alma çağrılarının uygulandığını belirten yönteminden true değerini uygular.

### <a name="determining-which-messages-to-chunk"></a>Hangi Iletileri öbekte belirleme

Öbek oluşturma kanalı yalnızca özniteliği aracılığıyla tanımlanan iletileri parçalara parçalar `ChunkingBehavior` . `ChunkingBehavior`Sınıfı, `IOperationBehavior` yöntemini çağırarak uygular ve uygulanır `AddBindingParameter` . Bu yöntemde, `ChunkingBehavior` `AppliesTo` `InMessage` `OutMessage` hangi iletilerin öbekli olması gerektiğini belirleyen, özelliğin değerini (veya her ikisi) inceler. Daha sonra bu iletilerin her birinin eylemini alır (üzerindeki Iletiler koleksiyonundan `OperationDescription` ) ve örneği içinde yer alan bir dize koleksiyonuna ekler `ChunkingBindingParameter` . Daha sonra bunu `ChunkingBindingParameter` , belirtilen öğesine ekler `BindingParameterCollection` .

Bu, bağlama `BindingParameterCollection` `BindingContext` öğesi kanal fabrikası veya kanal dinleyicisi oluşturduğunda bağlamadaki her bağlama öğesinin içine geçirilir. `ChunkingBindingElement`' Nin uygulanması `BuildChannelFactory<T>` ve bu uygulamadan `BuildChannelListener<T>` `ChunkingBindingParameter` çekmesi `BindingContext’` `BindingParameterCollection` . İçinde yer alan eylemlerin koleksiyonu `ChunkingBindingParameter` daha sonra veya ' a geçirilir ve `ChunkingChannelFactory` Bu da ' a geçirilir `ChunkingChannelListener` `ChunkingDuplexSessionChannel` .

## <a name="running-the-sample"></a>Örnek çalıştırma

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

5. Önce Service. exe ' yi çalıştırın, sonra Client. exe ' yi çalıştırın ve çıktı için hem konsol pencerelerini izleyin.

Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.

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
