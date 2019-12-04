---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 3811f7e7229dec1a46585a558b96f94bb202902f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716037"
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
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

Parçalama kanalı, yüksek düzeyde olan ve tipik kanal mimarisinden sonraki bir `IDuplexSessionChannel`. `ChunkingChannelFactory` ve `ChunkingChannelListener`oluşturabileceğiniz bir `ChunkingBindingElement` vardır. `ChunkingChannelFactory`, istendiğinde `ChunkingChannel` örnekleri oluşturur. `ChunkingChannelListener`, yeni bir iç kanal kabul edildiğinde `ChunkingChannel` örnekleri oluşturur. `ChunkingChannel` kendi kendine ileti göndermekten ve onlardan sorumludur.

Bir sonraki düzey aşağı `ChunkingChannel`, öbek protokolünü uygulamak için birkaç bileşene bağımlıdır. Gönderme tarafında kanal, gerçek parçalama yapan `ChunkingWriter` adlı özel bir <xref:System.Xml.XmlDictionaryWriter> kullanır. `ChunkingWriter`, öbek göndermek için doğrudan iç kanalı kullanır. Özel `XmlDictionaryWriter` kullanmak, özgün iletinin büyük gövdesi yazıldığı için öbekleri göndermemizi sağlar. Bu, tüm özgün iletiyi arabelleğe sunduğumuz anlamına gelir.

![Parçalama kanalı gönderme mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-send.gif)

Alma tarafında `ChunkingChannel`, iç kanaldan iletiler çeker ve bunları, gelen öbeklerden özgün iletiyi reconstitutes `ChunkingReader`adlı özel bir <xref:System.Xml.XmlDictionaryReader> sağlar. `ChunkingChannel`, bu `ChunkingReader` `ChunkingMessage` adlı özel bir `Message` uygulamasına sarar ve bu iletiyi yukarıdaki katmana döndürür. Bu `ChunkingReader` ve `ChunkingMessage` birleşimi özgün ileti gövdesinin tüm özgün ileti gövdesini arabelleğe almak yerine, yukarıdaki katman tarafından okunmakta olduğu gibi serbest bırakmamızı sağlar. `ChunkingReader`, gelen öbekleri en fazla yapılandırılabilir sayıda arabelleğe alınmış parçalara kadar arabelleğe aldığı bir kuyruğa sahiptir. Bu en fazla sınıra ulaşıldığında, okuyucu yukarıdaki katmanda bulunan (yani yalnızca özgün ileti gövdesinden okunarak) veya en fazla alma zaman aşımına ulaşılana kadar iletilerin kuyruktan dönmesini bekler.

![Parçalama kanalı alma mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Öbek programlama modeli

Hizmet geliştiricileri, sözleşme içindeki işlemlere `ChunkingBehavior` özniteliğini uygulayarak hangi iletilerin öbekli olduğunu belirtebilir. Özniteliği, geliştiricinin giriş mesajı, çıkış iletisi veya her ikisi için de uygulanıp uygulanmadığını belirtmesini sağlayan bir `AppliesTo` özelliği sunar. Aşağıdaki örnek `ChunkingBehavior` özniteliğin kullanımını gösterir:

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

`ChunkingBindingElement`, bu programlama modelinden, iletileri öbekli olacak şekilde tanımlayan eylem URI 'lerinin bir listesini derler. Her giden ileti eylemi, iletinin öbekli olarak mı yoksa doğrudan mi gönderileceğini öğrenmek için bu listeyle karşılaştırılır.

## <a name="implementing-the-send-operation"></a>Gönderme Işlemini uygulama

Yüksek düzeyde, Gönder işlemi önce giden iletinin öbekli olup olmadığını denetler ve yoksa iletiyi doğrudan iç kanalı kullanarak gönderir.

İleti öbekli olması gerekiyorsa, Send yeni bir `ChunkingWriter` oluşturur ve bu `ChunkingWriter`geçirerek giden iletide `WriteBodyContents` çağırır. `ChunkingWriter`, ileti öbek oluşturma (özgün ileti üstbilgilerini başlangıç öbek iletisine kopyalama dahil) ve iç kanalı kullanarak öbekleri gönderir.

Dikkat edilecek bazı ayrıntılar:

- `CommunicationState` açık olduğundan emin olmak için ilk çağrıları `ThrowIfDisposedOrNotOpened` gönderin.

- Gönderme, her oturum için tek seferde yalnızca bir ileti gönderilebilmesi için eşitlenir. Bir öbekli ileti gönderilirken sıfırlanan `sendingDone` adlı bir `ManualResetEvent` vardır. Öbek iletisi gönderildikten sonra bu olay ayarlanır. Send yöntemi, giden iletiyi göndermeyi denemeden önce bu olayın ayarlanmış olmasını bekler.

- Send, gönderirken eşitlenen durum değişikliklerini engellemek için `CommunicationObject.ThisLock` kilitler. <xref:System.ServiceModel.Channels.CommunicationObject> durumlar ve durum makinesi hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.CommunicationObject> belgelerine bakın.

- Gönderme için geçirilen zaman aşımı, tüm öbeklerin gönderilmesini içeren gönderme işleminin tamamına yönelik zaman aşımı olarak kullanılır.

- Özgün ileti gövdesinin tamamını arabelleğe almayı önlemek için özel <xref:System.Xml.XmlDictionaryWriter> tasarımı seçildi. `message.GetReaderAtBodyContents` kullanarak gövdede <xref:System.Xml.XmlDictionaryReader> alırız, tüm gövdenin ara belleğe alınır. Bunun yerine, `message.WriteBodyContents`geçirilen özel bir <xref:System.Xml.XmlDictionaryWriter> vardır. İleti, yazıcı üzerinde WriteBase64 çağırdığında, yazıcı paketleri ileti halinde parçalara ayırır ve bunları iç kanalı kullanarak gönderir. WriteBase64 blokları öbek gönderilene kadar engeller.

## <a name="implementing-the-receive-operation"></a>Alma Işlemi uygulama

Yüksek düzeyde, alma işlemi ilk önce gelen iletinin `null` olmadığını ve eyleminin `ChunkingAction`olduğunu denetler. Her iki ölçütü de karşılamıyorsa ileti alma işleminden değişmeden döndürülür. Aksi takdirde, al yeni bir `ChunkingReader` ve etrafında Sarmalanan yeni bir `ChunkingMessage` oluşturur (`GetNewChunkingMessage`çağırarak). Bu yeni `ChunkingMessage`döndürmeden önce, bir döngüsünde `innerChannel.Receive` çağıran ve son öbek iletisi alınana veya alma zaman aşımı düzeltilinceye kadar `ChunkingReader` öbeklere sahip olan `ReceiveChunkLoop`yürütmek için bir ThreadPool iş parçacığı kullanır.

Dikkat edilecek bazı ayrıntılar:

- Gönder gibi, `CommunicationState` açık olduğundan emin olmak için ilk çağrı Al `ThrowIfDisposedOrNotOepned`.

- Alma işlemi, oturumdan bir seferde yalnızca bir ileti alınabilmesi için de eşitlenir. Bu durum, bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm alınan iletilerin, son öbek iletisi alınana kadar bu yeni öbek sırası içinde öbeklerinin olması beklendiğinden özellikle önemlidir. Alma, şu anda öbekli olmayan bir iletiye ait olan tüm parçalar alındığından iç kanaldan ileti çekmez. Bunu gerçekleştirmek için al, yeni bir öbek iletisi alındığında bitiş öbek iletisi alındığında ve sıfırlandığında ayarlanan `currentMessageCompleted`adlı `ManualResetEvent` kullanır.

- Gönderme, alma işleminden farklı olarak alma sırasında eşitlenmiş durum geçişlerini engellemez. Örneğin, alma sırasında çağrılabilir ve özgün iletinin bekleyen alımı tamamlanana veya belirtilen zaman aşımı değerine ulaşılana kadar beklenebilir.

- Alma işlemi sırasında geçen zaman aşımı, tüm öbeklerin alınması dahil olmak üzere tüm alma işlemleri için zaman aşımı olarak kullanılır.

- İletiyi kullanan Katman, gelen öbek iletilerinin hızından daha düşük bir hızda ileti gövdesini kullanıyorsa, `ChunkingReader` bu gelen öbekleri `ChunkingBindingElement.MaxBufferedChunks`belirtilen sınıra kadar arabelleğe alır. Bu sınıra ulaşıldığında, arabelleğe alınmış bir öbek tüketilene veya alma zaman aşımına ulaşılana kadar alt katmandan daha fazla öbek çekilmeyen bir değer yoktur.

## <a name="communicationobject-overrides"></a>CommunicationObject geçersiz kılmaları

### <a name="onopen"></a>OnOpen

`OnOpen`, iç kanalı açmak için `innerChannel.Open` çağırır.

### <a name="onclose"></a>OnClose

`OnClose`, `true` `stopReceive`, durdurmak için bekleyen `ReceiveChunkLoop` sinyali verecek şekilde ayarlar. Daha sonra, `ReceiveChunkLoop` durdurulduğunda ayarlanan `receiveStopped` <xref:System.Threading.ManualResetEvent>bekler. `ReceiveChunkLoop` belirtilen zaman aşımı süresi içinde durduğu varsayılarak, geri kalan zaman aşımı ile `innerChannel.Close` `OnClose` çağırır.

### <a name="onabort"></a>OnAbort

`OnAbort`, iç kanalı durdurmak için `innerChannel.Abort` çağırır. Bekleyen bir `ReceiveChunkLoop` varsa, bekleyen `innerChannel.Receive` çağrısından bir özel durum alır.

### <a name="onfaulted"></a>Onhatalı

`ChunkingChannel` kanal hata verdi ve `OnFaulted` geçersiz kılınmadığında özel bir davranış gerektirmez.

## <a name="implementing-channel-factory"></a>Kanal fabrikası uygulama

`ChunkingChannelFactory`, iç kanal fabrikasında `ChunkingDuplexSessionChannel` örnekleri ve basamaklı durum geçişleri oluşturmaktan sorumludur.

`OnCreateChannel`, iç kanal fabrikası kullanarak `IDuplexSessionChannel` bir iç kanal oluşturur. Daha sonra bu iç kanalı, yığın olarak kullanılacak ileti eylemlerinin listesiyle birlikte geçirerek yeni bir `ChunkingDuplexSessionChannel` oluşturur. Yığın olarak kullanılacak ileti eylemlerinin listesi ve arabellekteki öbeklerin en fazla sayısı, oluşturucusunun `ChunkingChannelFactory` geçirilen iki parametredir. `ChunkingBindingElement` bölümünde bu değerlerin nereden geldiği açıklanmaktadır.

`OnOpen`, `OnClose`, `OnAbort` ve zaman uyumsuz eşdeğerleri, iç kanal fabrikasında karşılık gelen durum geçiş yöntemini çağırır.

## <a name="implementing-channel-listener"></a>Kanal dinleyicisi uygulama

`ChunkingChannelListener`, iç kanal dinleyicisinin etrafındaki bir sarmalayıcıdır. Ana işlevi, bu iç kanal dinleyicisine yapılan temsilci çağrılarının yanı sıra yeni `ChunkingDuplexSessionChannels` iç kanal dinleyicisinden kabul edilen kanallara sarmalıdır. Bu `OnAcceptChannel` ve `OnEndAcceptChannel`yapılır. Yeni oluşturulan `ChunkingDuplexSessionChannel`, daha önce açıklanan diğer parametrelerle birlikte iç kanalı geçti.

## <a name="implementing-binding-element-and-binding"></a>Bağlama öğesi ve bağlamayı uygulama

`ChunkingBindingElement`, `ChunkingChannelFactory` ve `ChunkingChannelListener`oluşturmaktan sorumludur. `ChunkingBindingElement`, `CanBuildChannelFactory`\<T > ve `CanBuildChannelListener`\<T > türü `IDuplexSessionChannel` (parçalama kanalının desteklediği tek kanal) ve bağlamadaki diğer bağlama öğelerinin bu kanal türünü destekleyip desteklemediğini denetler.

`BuildChannelFactory`\<T > öncelikle istenen kanal türünün oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır. Daha fazla bilgi için aşağıdaki bölüme bakın. Daha sonra, iç kanal fabrikasını (`context.BuildInnerChannelFactory<IDuplexSessionChannel>`döndürülen), ileti eylemlerinin listesini ve arabelleğe alınan en fazla parça sayısını geçirerek yeni bir `ChunkingChannelFactory` oluşturur. En fazla parça sayısı, `ChunkingBindingElement`tarafından sunulan `MaxBufferedChunks` adlı bir özellikten gelir.

`BuildChannelListener<T>`, `ChunkingChannelListener` oluşturmak ve bunu iç kanal dinleyicisi geçirmek için benzer bir uygulamaya sahiptir.

Bu örnekte `TcpChunkingBinding`adında bir örnek bağlama bulunur. Bu bağlama iki bağlama öğesinden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement`. `MaxBufferedChunks` özelliğini ayarlamanın yanı sıra, bağlama Ayrıca `MaxReceivedMessageSize` gibi bazı `TcpTransportBindingElement` özellikleri de ayarlar (üstbilgiler için `ChunkingUtils.ChunkSize` + 100KB bayt olarak ayarlar).

`TcpChunkingBinding` Ayrıca, `IBindingRuntimePreferences` uygular ve yalnızca zaman uyumlu alma çağrılarının uygulandığını belirten `ReceiveSynchronously` yönteminden true değerini döndürür.

### <a name="determining-which-messages-to-chunk"></a>Hangi Iletileri öbekte belirleme

Öbek oluşturma kanalı yalnızca `ChunkingBehavior` özniteliği aracılığıyla tanımlanan iletileri parçalara parçalar. `ChunkingBehavior` sınıfı `IOperationBehavior` uygular ve `AddBindingParameter` metodu çağırarak uygulanır. Bu yöntemde `ChunkingBehavior`, hangi iletilerin öbekli olması gerektiğini belirleyen `AppliesTo` özelliğinin (`InMessage`, `OutMessage` veya her ikisi) değerini inceler. Daha sonra bu iletilerin her birinin eylemini alır (`OperationDescription`Ileti koleksiyonundan) ve bir `ChunkingBindingParameter`örneği içinde bulunan bir dize koleksiyonuna ekler. Daha sonra bu `ChunkingBindingParameter`, belirtilen `BindingParameterCollection`ekler.

Bu `BindingParameterCollection`, bağlama öğesi kanal fabrikası veya kanal dinleyicisi oluşturduğunda bağlamadaki her bağlama öğesine `BindingContext` geçirilir. `ChunkingBindingElement``BuildChannelFactory<T>` ve `BuildChannelListener<T>`, bu `ChunkingBindingParameter` `BindingContext’`s `BindingParameterCollection`dışına çekin. `ChunkingBindingParameter` içinde yer alan eylemler koleksiyonu `ChunkingChannelFactory` veya `ChunkingChannelListener`geçirilir ve bu da `ChunkingDuplexSessionChannel`geçirir.

## <a name="running-the-sample"></a>Örnek çalıştırma

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

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
