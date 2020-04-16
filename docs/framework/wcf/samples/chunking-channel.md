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
# <a name="chunking-channel"></a><span data-ttu-id="a27cd-102">Öbekleme Kanalı</span><span class="sxs-lookup"><span data-stu-id="a27cd-102">Chunking Channel</span></span>

<span data-ttu-id="a27cd-103">Windows Communication Foundation (WCF) kullanarak büyük iletiler gönderirken, genellikle bu iletileri arabelleğe almak için kullanılan bellek miktarını sınırlamak istenir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="a27cd-104">Olası bir çözüm ileti gövdesini akış (verilerin büyük bir kısmının gövdede olduğunu varsayarak).</span><span class="sxs-lookup"><span data-stu-id="a27cd-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="a27cd-105">Ancak bazı protokoller tüm iletinin arabelleğe alınmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="a27cd-106">Güvenilir mesajlaşma ve güvenlik bu iki örnektir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="a27cd-107">Başka bir olası çözüm, büyük iletiyi parçalar olarak adlandırılan daha küçük iletilere bölmek, bu parçaları her seferinde bir yığın göndermek ve büyük iletiyi alıcı tarafta yeniden oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="a27cd-108">Uygulamanın kendisi bu yığın ve de-chunking yapabilir veya bunu yapmak için özel bir kanal kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a27cd-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="a27cd-109">Chunking kanal örneği, özel bir protokolün veya katmanlı kanalın rasgele büyük iletilerin öğrlemeyi ve parçalarını ayrıştma yapmak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="a27cd-110">Chunking her zaman yalnızca gönderilecek tüm ileti oluşturulduktan sonra kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="a27cd-111">Bir yığın kanalı her zaman bir güvenlik kanalı nın ve güvenilir bir oturum kanalının altına katmanlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="a27cd-112">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a27cd-113">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a27cd-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a27cd-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a27cd-116">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="a27cd-117">Kanal Varsayımlarını ve Sınırlamalarını Parçalama</span><span class="sxs-lookup"><span data-stu-id="a27cd-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="a27cd-118">İleti Yapısı</span><span class="sxs-lookup"><span data-stu-id="a27cd-118">Message Structure</span></span>

<span data-ttu-id="a27cd-119">Yığın kanalı, iletilerin parçalanması için aşağıdaki ileti yapısını varsayar:</span><span class="sxs-lookup"><span data-stu-id="a27cd-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="a27cd-120">ServiceModel'i kullanırken, 1 giriş parametresi olan sözleşme işlemleri, giriş iletisi için bu ileti şekline uygundur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="a27cd-121">Benzer şekilde, 1 çıktı parametresi veya iade değeri olan sözleşme işlemleri, çıktı iletisi için bu ileti şekline uygundur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="a27cd-122">Bu tür işlemlere örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a27cd-122">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="a27cd-123">Oturumlar</span><span class="sxs-lookup"><span data-stu-id="a27cd-123">Sessions</span></span>

<span data-ttu-id="a27cd-124">Yığın kanalı, iletilerin (öbek) sırayla teslim edilmesinde iletilerin tam olarak bir kez teslim edilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="a27cd-125">Bu, temel kanal yığınının oturum dolusu olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="a27cd-126">Oturumlar aktarım (örneğin, TCP aktarım) veya oturum lu bir protokol kanalı (örneğin, ReliableSession kanalı) tarafından sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="a27cd-127">Asynchronous Gönder ve Al</span><span class="sxs-lookup"><span data-stu-id="a27cd-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="a27cd-128">Asynchronous gönderme ve alma yöntemleri, yığın kanalı örneğinin bu sürümünde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="a27cd-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="a27cd-129">Parçalama Protokolü</span><span class="sxs-lookup"><span data-stu-id="a27cd-129">Chunking Protocol</span></span>

<span data-ttu-id="a27cd-130">Yığın kanalı, bir dizi parçanın başlangıç ve sonunu ve her bir parçanın sıra numarasını gösteren bir protokol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a27cd-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="a27cd-131">Aşağıdaki üç örnek ileti, her birinin temel yönlerini açıklayan açıklamalarla başlangıç, öbek ve bitiş iletilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="a27cd-132">İletiyi Başlat</span><span class="sxs-lookup"><span data-stu-id="a27cd-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="a27cd-133">Öbek İletisi</span><span class="sxs-lookup"><span data-stu-id="a27cd-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="a27cd-134">İletiyi Sonla</span><span class="sxs-lookup"><span data-stu-id="a27cd-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="a27cd-135">Chunking Kanal Mimarisi</span><span class="sxs-lookup"><span data-stu-id="a27cd-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="a27cd-136">Chunking kanalı, `IDuplexSessionChannel` yüksek düzeyde, tipik kanal mimarisini izleyen bir kanaldır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="a27cd-137">Bir ve `ChunkingBindingElement` bir `ChunkingChannelFactory` inşa edebilirsiniz bir `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="a27cd-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="a27cd-138">`ChunkingChannel` İstendiğinde `ChunkingChannelFactory` örnekler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="a27cd-139">Yeni `ChunkingChannelListener` bir iç `ChunkingChannel` kanal kabul edildiğinde örnekler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="a27cd-140">İletilerin `ChunkingChannel` gönderilmesi nden ve alınmasından kendisi sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="a27cd-141">Bir sonraki düzeyde `ChunkingChannel` aşağı, parçalama protokolü uygulamak için çeşitli bileşenlere dayanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="a27cd-142">Gönder tarafında, kanal gerçek ötme yapan bir özel <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` kullanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="a27cd-143">`ChunkingWriter`parçaları göndermek için doğrudan iç kanalı kullanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="a27cd-144">Bir özel `XmlDictionaryWriter` kullanarak bize orijinal iletinin büyük gövdesi yazılı olarak parçalar göndermek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="a27cd-145">Bu, özgün iletinin tamamını arabelleğe almadığımız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-145">This means we do not buffer the entire original message.</span></span>

![Yığın lama kanalını gösteren diyagram mimari gönder.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="a27cd-147">Alma tarafında, `ChunkingChannel` iletileri iç kanaldan çeker ve gelen <xref:System.Xml.XmlDictionaryReader> parçalardan gelen orijinal iletiyi yeniden oluşturan `ChunkingReader`özel bir özele teslim eder.</span><span class="sxs-lookup"><span data-stu-id="a27cd-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="a27cd-148">`ChunkingChannel`bu `ChunkingReader` özel bir `Message` uygulama `ChunkingMessage` denir sarar ve yukarıdaki katmana bu iletiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="a27cd-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="a27cd-149">Bu kombinasyon `ChunkingReader` `ChunkingMessage` ve bize tüm orijinal ileti gövdesi arabelleğe almak zorunda yerine yukarıdaki katman tarafından okunuyor gibi orijinal ileti gövdesi de-chunk sağlar.</span><span class="sxs-lookup"><span data-stu-id="a27cd-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="a27cd-150">`ChunkingReader`en fazla yapılandırılmış arabellekli parça sayısına kadar gelen parçaları arabelleğe aldığı bir kuyruğa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="a27cd-151">Bu maksimum sınıra ulaşıldığında, okuyucu iletilerin yukarıdaki katman tarafından (diğer bir şekilde orijinal ileti gövdesinden okunarak) veya maksimum alma zaman aşımına ulaşılAna kadar sıradan boşaltılmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Yığın kanalını gösteren diyagram mimari alır.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="a27cd-153">Chunking Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="a27cd-153">Chunking Programming Model</span></span>

<span data-ttu-id="a27cd-154">Hizmet geliştiriciler, sözleşme içindeki işlemlere öznitelik uygulayarak `ChunkingBehavior` hangi iletilerin ödeneceğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="a27cd-155">Öznitelik, geliştiricinin `AppliesTo` öbeklemenin giriş iletisi, çıktı iletisi veya her ikisi için de geçerli olup olmadığını belirtmesine olanak tanıyan bir özelliği ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="a27cd-156">Aşağıdaki örnek, öznitelik `ChunkingBehavior` kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a27cd-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="a27cd-157">Bu programlama modelinden, `ChunkingBindingElement` ödenecek iletileri tanımlayan bir eylem UUI listesi derler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="a27cd-158">Giden her iletinin eylemi, iletinin parçalanmış mı yoksa doğrudan gönderilmesi mi gerektiğini belirlemek için bu listeyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="a27cd-159">Gönderme İşleminin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="a27cd-159">Implementing the Send Operation</span></span>

<span data-ttu-id="a27cd-160">Yüksek düzeyde, Gönderen işlemi önce giden iletinin parçalanıp tıkanması gerekmediğini denetler ve değilse, iletiyi doğrudan iç kanalı kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="a27cd-161">İletinin parçalanmış olması gerekiyorsa, Gönder `ChunkingWriter` yeni `WriteBodyContents` bir oluşturma ve bu `ChunkingWriter`iletiyi geçen giden iletiyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="a27cd-162">Daha `ChunkingWriter` sonra ileti ödenebilir (başlangıç öbek iletisine özgün ileti üstbilgilerinin kopyalanması dahil) yapar ve iç kanalı kullanarak öbek gönderir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="a27cd-163">Kayda değer birkaç ayrıntı:</span><span class="sxs-lookup"><span data-stu-id="a27cd-163">A few details worth noting:</span></span>

- <span data-ttu-id="a27cd-164">Açıldığından `CommunicationState` `ThrowIfDisposedOrNotOpened` emin olmak için ilk aramaları gönderin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="a27cd-165">Gönderme, her oturum için aynı anda yalnızca bir ileti gönderilebilmek için eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="a27cd-166">Bir yığın `ManualResetEvent` `sendingDone` ileti gönderilirken sıfırlanan bir ad vardır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="a27cd-167">Son öbek iletisi gönderildikten sonra, bu olay ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="a27cd-168">Gönder yöntemi, giden iletiyi göndermeye çalışır önce bu olayın ayarını bekler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="a27cd-169">Gönderirken `CommunicationObject.ThisLock` eşitlenmiş durum değişikliklerini önlemek için kilitleri gönder.</span><span class="sxs-lookup"><span data-stu-id="a27cd-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="a27cd-170">Durumlar <xref:System.ServiceModel.Channels.CommunicationObject> ve durum makinesi <xref:System.ServiceModel.Channels.CommunicationObject> hakkında daha fazla bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="a27cd-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="a27cd-171">Gönder'e geçirilen zaman aşımı, tüm parçaları göndermeyi içeren tüm gönderme işlemi için zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="a27cd-172">Özel <xref:System.Xml.XmlDictionaryWriter> tasarım, tüm orijinal ileti gövdesinin arabelleğe alınışını önlemek için seçildi.</span><span class="sxs-lookup"><span data-stu-id="a27cd-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="a27cd-173">Eğer tüm vücudu <xref:System.Xml.XmlDictionaryReader> kullanarak `message.GetReaderAtBodyContents` bir ceset alırsanız tamponlanmış oluruz.</span><span class="sxs-lookup"><span data-stu-id="a27cd-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="a27cd-174">Bunun yerine, biz <xref:System.Xml.XmlDictionaryWriter> geçirilen bir `message.WriteBodyContents`özel var.</span><span class="sxs-lookup"><span data-stu-id="a27cd-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="a27cd-175">İleti yazarüzerinde WriteBase64 çağırır gibi, yazar mesajları içine yığınlar kadar paketleri ve iç kanalı kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="a27cd-176">Yığın gönderilene kadar Base64 bloklarını yazın.</span><span class="sxs-lookup"><span data-stu-id="a27cd-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="a27cd-177">Alma İşleminin Uygulanması</span><span class="sxs-lookup"><span data-stu-id="a27cd-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="a27cd-178">Yüksek düzeyde, Alma işlemi ilk olarak gelen iletinin `null` olmadığını ve eyleminin `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="a27cd-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="a27cd-179">Her iki ölçüte de uymuyorsa, ileti Receive'tan değiştirilmeden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a27cd-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="a27cd-180">Aksi takdirde, Receive `ChunkingReader` yeni ve `ChunkingMessage` yeni bir sarılmış `GetNewChunkingMessage`(arayarak) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="a27cd-181">Bu yeni `ChunkingMessage`döndürmeden önce , Receive yürütmek `ReceiveChunkLoop`için `innerChannel.Receive` bir threadpool iş parçacığı kullanır `ChunkingReader` , bir döngü içinde çağırır ve son yığın iletisi alınana veya alma zaman acısı isabet kadar parçaları kapalı eller.</span><span class="sxs-lookup"><span data-stu-id="a27cd-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="a27cd-182">Kayda değer birkaç ayrıntı:</span><span class="sxs-lookup"><span data-stu-id="a27cd-182">A few details worth noting:</span></span>

- <span data-ttu-id="a27cd-183">Gönder gibi, Açıldığından `ThrowIfDisposedOrNotOepned` `CommunicationState` emin olmak için ilk çağrıları alın.</span><span class="sxs-lookup"><span data-stu-id="a27cd-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="a27cd-184">Alma, oturumdan aynı anda yalnızca bir ileti alınabilmesi için eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="a27cd-185">Bu özellikle önemlidir, çünkü bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm iletilerin bir son öbek iletisi alınana kadar bu yeni yığın dizisi içinde parçalar olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="a27cd-186">İletiye ait tüm parçalar şu anda parçalanan ileti ye gelene kadar iç kanaldan ileti çekemez.</span><span class="sxs-lookup"><span data-stu-id="a27cd-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="a27cd-187">Bunu gerçekleştirmek için, `ManualResetEvent` Receive, son öbek iletisi alındığı zaman ayarlanan ve yeni bir başlangıç öycesi iletisi aldığında sıfırlanan bir adlandırılmış `currentMessageCompleted`kullanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="a27cd-188">Gönder'in aksine, Receive alırken eşitlenmiş durum geçişlerini engellemez.</span><span class="sxs-lookup"><span data-stu-id="a27cd-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="a27cd-189">Örneğin, teslim alırken Kapat çağrılabilir ve özgün iletinin bekleyen alabilmesi tamamlanana veya belirtilen zaman sonu değerine ulaşılAna kadar bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="a27cd-190">Receive için geçirilen zaman aşımı, tüm parçaları almayı içeren tüm alma işlemi için zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="a27cd-191">İletiyi tüketen katman ileti gövdesini gelen öbek iletilerinin hızından daha düşük bir `ChunkingReader` oranda tüketiyorsa, gelen öbek, gelen öbek'leri ' tarafından `ChunkingBindingElement.MaxBufferedChunks`belirtilen sınıra kadar arabellek</span><span class="sxs-lookup"><span data-stu-id="a27cd-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="a27cd-192">Bu sınıra ulaşıldıktan sonra, arabelleğe alınan bir yığın tüketilene veya alma zaman aşıntısına ulaşılına kadar alt katmandan başka parça çekilmez.</span><span class="sxs-lookup"><span data-stu-id="a27cd-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="a27cd-193">İletişimNesne Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="a27cd-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="a27cd-194">Açık Açık</span><span class="sxs-lookup"><span data-stu-id="a27cd-194">OnOpen</span></span>

<span data-ttu-id="a27cd-195">`OnOpen`iç `innerChannel.Open` kanalı açmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="a27cd-196">Onclose</span><span class="sxs-lookup"><span data-stu-id="a27cd-196">OnClose</span></span>

<span data-ttu-id="a27cd-197">`OnClose`durdurmak `stopReceive` için `true` bekleyen `ReceiveChunkLoop` sinyal için ilk ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a27cd-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="a27cd-198">Daha sonra durur `receiveStopped` <xref:System.Threading.ManualResetEvent>ayarlanır `ReceiveChunkLoop` , bekler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="a27cd-199">Belirtilen `ReceiveChunkLoop` zaman anına kadar `OnClose` `innerChannel.Close` durakları varsayarsak, kalan zaman amıyla çağırır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="a27cd-200">Onabort</span><span class="sxs-lookup"><span data-stu-id="a27cd-200">OnAbort</span></span>

<span data-ttu-id="a27cd-201">`OnAbort`iç `innerChannel.Abort` kanalı iptal etmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="a27cd-202">Bekleyen `ReceiveChunkLoop` bir arama varsa, bekleyen `innerChannel.Receive` aramadan bir özel durum alır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="a27cd-203">Hatalı</span><span class="sxs-lookup"><span data-stu-id="a27cd-203">OnFaulted</span></span>

<span data-ttu-id="a27cd-204">Kanal `ChunkingChannel` arızalandığında özel davranış gerektirmez, bu `OnFaulted` nedenle geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="a27cd-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="a27cd-205">Kanal Fabrikası'nın Uygulanması</span><span class="sxs-lookup"><span data-stu-id="a27cd-205">Implementing Channel Factory</span></span>

<span data-ttu-id="a27cd-206">İç `ChunkingChannelFactory` kanal fabrikasına `ChunkingDuplexSessionChannel` devlet geçişlerinin örneklerini oluşturmaktan ve basamaklamadurumundan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="a27cd-207">`OnCreateChannel`bir `IDuplexSessionChannel` iç kanal oluşturmak için iç kanal fabrikasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="a27cd-208">Daha sonra, bu `ChunkingDuplexSessionChannel` iç kanalda, ötülecek ileti eylemlerinin listesi ve aldıktan sonra arabelleğe alınacak en fazla parça sayısı yla birlikte yeni bir geçiş oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="a27cd-209">Parçalanacak ileti eylemlerinin listesi ve arabellek için kullanılacak en fazla parça `ChunkingChannelFactory` sayısı, oluşturucusunda geçirilen iki parametredir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="a27cd-210">Bu `ChunkingBindingElement` değerlerin nereden geldiğini açıklayan bölüm.</span><span class="sxs-lookup"><span data-stu-id="a27cd-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="a27cd-211">, `OnOpen` `OnClose` `OnAbort` ve onların eşzamanlı eşdeğerleri iç kanal fabrikasında karşılık gelen durum geçiş yöntemi ni çağırır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="a27cd-212">Kanal Dinleyicisi Uygulama</span><span class="sxs-lookup"><span data-stu-id="a27cd-212">Implementing Channel Listener</span></span>

<span data-ttu-id="a27cd-213">Bir `ChunkingChannelListener` iç kanal dinleyici etrafında bir sarmalayıcı.</span><span class="sxs-lookup"><span data-stu-id="a27cd-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="a27cd-214">Ana işlevi, bu iç kanal dinleyiciiçin delege çağrıları `ChunkingDuplexSessionChannels` yanı sıra, iç kanal dinleyici kabul kanalları etrafında yeni sarmak için.</span><span class="sxs-lookup"><span data-stu-id="a27cd-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="a27cd-215">Bu yapılır `OnAcceptChannel` ve `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="a27cd-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="a27cd-216">Yeni oluşturulan `ChunkingDuplexSessionChannel` daha önce açıklanan diğer parametrelerile birlikte iç kanal geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="a27cd-217">Bağlama Öğesi nin Uygulanması ve Bağlama</span><span class="sxs-lookup"><span data-stu-id="a27cd-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="a27cd-218">`ChunkingBindingElement`oluşturmaktan sorumludur `ChunkingChannelFactory` ve `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="a27cd-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="a27cd-219">T `ChunkingBindingElement`> ve `CanBuildChannelFactory` \< `CanBuildChannelListener` \<T>'daki T'nin türde `IDuplexSessionChannel` olup olmadığını (öbeklenme kanalı tarafından desteklenen tek kanal) ve bağlamadaki diğer bağlama öğelerinin bu kanal türünü desteklediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="a27cd-220">`BuildChannelFactory`\<T> önce istenen kanal türünün oluşturulabileceğini denetler ve ardından parçalanacak ileti eylemlerinin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="a27cd-221">Daha fazla bilgi için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="a27cd-221">For more information, see the following section.</span></span> <span data-ttu-id="a27cd-222">Daha sonra yeni `ChunkingChannelFactory` bir geçiş o iç kanal `context.BuildInnerChannelFactory<IDuplexSessionChannel>`fabrika (döndürülen), ileti eylemleri listesi ve arabellek için parçaların maksimum sayısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a27cd-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="a27cd-223">En fazla parça `MaxBufferedChunks` `ChunkingBindingElement`sayısı, 'nin maruz kalan özelliğinden gelir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="a27cd-224">`BuildChannelListener<T>`oluşturmak `ChunkingChannelListener` ve iç kanal dinleyici geçmek için benzer bir uygulama vardır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="a27cd-225">Bu örnekte .. `TcpChunkingBinding`</span><span class="sxs-lookup"><span data-stu-id="a27cd-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="a27cd-226">Bu bağlama iki bağlayıcı `TcpTransportBindingElement` öğeden oluşur: ve `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="a27cd-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="a27cd-227">Özelliği açığa çıkarmanın `MaxBufferedChunks` yanı sıra, bağlama gibi `TcpTransportBindingElement` bazı `MaxReceivedMessageSize` özellikleri de `ChunkingUtils.ChunkSize` ayarlar (üstbilgi için + 100KB bayt ayarlar).</span><span class="sxs-lookup"><span data-stu-id="a27cd-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="a27cd-228">`TcpChunkingBinding`ayrıca yalnızca `IBindingRuntimePreferences` senkron Receive `ReceiveSynchronously` çağrılarının uygulandığını belirten yöntemden doğru olarak uygular ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="a27cd-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="a27cd-229">Hangi İletilerin Öbek Olarak Belirlene</span><span class="sxs-lookup"><span data-stu-id="a27cd-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="a27cd-230">Yığın kanalı yalnızca öznitelik üzerinden `ChunkingBehavior` tanımlanan iletileri parçalar.</span><span class="sxs-lookup"><span data-stu-id="a27cd-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="a27cd-231">Sınıf `ChunkingBehavior` uygular `IOperationBehavior` ve `AddBindingParameter` yöntemi çağırarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a27cd-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="a27cd-232">Bu yöntemde, `ChunkingBehavior` hangi iletilerin `AppliesTo` parçalanılması gerektiğini belirlemek için özelliğinin`InMessage` `OutMessage` (veya her ikisinin) değerini inceler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="a27cd-233">Daha sonra bu iletilerin her birinin eylemini alır `OperationDescription`(Üzerindeki İletiler koleksiyonundan) ve bir `ChunkingBindingParameter`örnek içinde bulunan bir dize koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="a27cd-234">Daha sonra `ChunkingBindingParameter` sağlanan `BindingParameterCollection`bu ekler.</span><span class="sxs-lookup"><span data-stu-id="a27cd-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="a27cd-235">Bu `BindingParameterCollection` bağlama öğesi `BindingContext` kanal fabrikası veya kanal dinleyici oluşturur zaman bağlama her bağlayıcı öğe içinde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a27cd-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="a27cd-236">'uygulama `ChunkingBindingElement` `BuildChannelFactory<T>` ve `BuildChannelListener<T>` `ChunkingBindingParameter` `BindingContext’`s `BindingParameterCollection`bu çekin .</span><span class="sxs-lookup"><span data-stu-id="a27cd-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="a27cd-237">İçinde `ChunkingBindingParameter` yer alan eylemlerin toplanması daha `ChunkingChannelFactory` sonra `ChunkingChannelListener`ya da , sırayla geçer `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="a27cd-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="a27cd-238">Örneği Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a27cd-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a27cd-239">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a27cd-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a27cd-240">Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="a27cd-241">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="a27cd-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="a27cd-242">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="a27cd-243">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="a27cd-244">Önce Service.exe'yi çalıştırın, sonra Client.exe'yi çalıştırın ve çıktı için her iki konsol penceresini de izleyin.</span><span class="sxs-lookup"><span data-stu-id="a27cd-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="a27cd-245">Örneği çalıştırırken, aşağıdaki çıktı bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="a27cd-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="a27cd-246">İstemci:</span><span class="sxs-lookup"><span data-stu-id="a27cd-246">Client:</span></span>

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

<span data-ttu-id="a27cd-247">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="a27cd-247">Server:</span></span>

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
