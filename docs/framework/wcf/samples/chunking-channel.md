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
# <a name="chunking-channel"></a><span data-ttu-id="ecc32-102">Öbekleme Kanalı</span><span class="sxs-lookup"><span data-stu-id="ecc32-102">Chunking Channel</span></span>

<span data-ttu-id="ecc32-103">Windows Communication Foundation (WCF) kullanarak büyük iletiler gönderirken, bu iletileri arabelleğe almak için kullanılan bellek miktarının sınırlanmasından genellikle tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="ecc32-104">Olası bir çözüm, ileti gövdesinin akışını (verilerin toplu olarak gövdesinde olduğu varsayıldığında) sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="ecc32-105">Ancak bazı protokollerin iletinin tamamının arabelleğe alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="ecc32-106">Güvenilir Mesajlaşma ve güvenlik iki tür örnektir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="ecc32-107">Diğer bir olası çözüm de büyük iletiyi öbek adı verilen küçük iletilere bölmek, bu öbekleri tek seferde bir öbek göndermek ve alma tarafında büyük iletiyi edilmeyen.</span><span class="sxs-lookup"><span data-stu-id="ecc32-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="ecc32-108">Uygulamanın kendisi bu parçalama ve parçalama işlemlerini yapmak için özel bir kanal kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="ecc32-109">Öbek oluşturma kanalı örneği, özel bir protokol veya katmanlı kanalın, rastgele büyük iletileri parçalama ve parçalama için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="ecc32-110">Parçalama her zaman yalnızca gönderilecek iletinin tamamı oluşturulduktan sonra kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="ecc32-111">Bir parçalama kanalının her zaman bir güvenlik kanalının ve güvenilir bir oturum kanalının altında katmanlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="ecc32-112">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecc32-113">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ecc32-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ecc32-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecc32-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="ecc32-117">Kanal varsayımları ve sınırlamaları parçalama</span><span class="sxs-lookup"><span data-stu-id="ecc32-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="ecc32-118">İleti yapısı</span><span class="sxs-lookup"><span data-stu-id="ecc32-118">Message Structure</span></span>

<span data-ttu-id="ecc32-119">Öbek oluşturma kanalı, iletilerin öbeklenmesini sağlamak için aşağıdaki ileti yapısını varsayar:</span><span class="sxs-lookup"><span data-stu-id="ecc32-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="ecc32-120">ServiceModel kullanılırken, 1 girdi parametresine sahip sözleşme işlemleri giriş iletileri için bu ileti şekliyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="ecc32-121">Benzer şekilde, 1 çıkış parametresi veya dönüş değeri olan sözleşme işlemleri, çıkış iletileri için bu ileti şekliyle uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="ecc32-122">Bu tür işlemlere örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ecc32-122">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="ecc32-123">Oturumlar</span><span class="sxs-lookup"><span data-stu-id="ecc32-123">Sessions</span></span>

<span data-ttu-id="ecc32-124">Öbek oluşturma kanalı, iletilerin sıralı iletiler (öbekler) tesliminde tam olarak bir kez teslim edilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="ecc32-125">Bu, temeldeki kanal yığınının oturumsuz olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="ecc32-126">Oturumlar, taşıma (örneğin, TCP aktarımı) veya bir oturum Protokolü kanalı (örneğin, Reliableoturum kanalı) tarafından sağlanırlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="ecc32-127">Zaman uyumsuz gönderme ve alma</span><span class="sxs-lookup"><span data-stu-id="ecc32-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="ecc32-128">Zaman uyumsuz gönderme ve alma yöntemleri, parçalama kanalı örneğinin bu sürümünde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="ecc32-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="ecc32-129">Kümeleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="ecc32-129">Chunking Protocol</span></span>

<span data-ttu-id="ecc32-130">Öbek oluşturma kanalı, bir dizi öbekin başlangıcını ve sonunu ve her öbekin sıra numarasını belirten bir protokol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="ecc32-131">Aşağıdaki üç örnek ileti, her birinin ana yönlerini tanımlayan yorumlarla başlangıç, öbek ve son iletileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="ecc32-132">Iletiyi Başlat</span><span class="sxs-lookup"><span data-stu-id="ecc32-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="ecc32-133">Öbek Iletisi</span><span class="sxs-lookup"><span data-stu-id="ecc32-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="ecc32-134">Bitiş Iletisi</span><span class="sxs-lookup"><span data-stu-id="ecc32-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="ecc32-135">Parçalama kanalı mimarisi</span><span class="sxs-lookup"><span data-stu-id="ecc32-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="ecc32-136">Parçalama kanalı, yüksek düzeyde olan ve tipik kanal mimarisinden sonraki bir `IDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="ecc32-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="ecc32-137">`ChunkingChannelFactory` ve `ChunkingChannelListener`oluşturabileceğiniz bir `ChunkingBindingElement` vardır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="ecc32-138">`ChunkingChannelFactory`, istendiğinde `ChunkingChannel` örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="ecc32-139">`ChunkingChannelListener`, yeni bir iç kanal kabul edildiğinde `ChunkingChannel` örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="ecc32-140">`ChunkingChannel` kendi kendine ileti göndermekten ve onlardan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="ecc32-141">Bir sonraki düzey aşağı `ChunkingChannel`, öbek protokolünü uygulamak için birkaç bileşene bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="ecc32-142">Gönderme tarafında kanal, gerçek parçalama yapan `ChunkingWriter` adlı özel bir <xref:System.Xml.XmlDictionaryWriter> kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="ecc32-143">`ChunkingWriter`, öbek göndermek için doğrudan iç kanalı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="ecc32-144">Özel `XmlDictionaryWriter` kullanmak, özgün iletinin büyük gövdesi yazıldığı için öbekleri göndermemizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="ecc32-145">Bu, tüm özgün iletiyi arabelleğe sunduğumuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-145">This means we do not buffer the entire original message.</span></span>

![Parçalama kanalı gönderme mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="ecc32-147">Alma tarafında `ChunkingChannel`, iç kanaldan iletiler çeker ve bunları, gelen öbeklerden özgün iletiyi reconstitutes `ChunkingReader`adlı özel bir <xref:System.Xml.XmlDictionaryReader> sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="ecc32-148">`ChunkingChannel`, bu `ChunkingReader` `ChunkingMessage` adlı özel bir `Message` uygulamasına sarar ve bu iletiyi yukarıdaki katmana döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecc32-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="ecc32-149">Bu `ChunkingReader` ve `ChunkingMessage` birleşimi özgün ileti gövdesinin tüm özgün ileti gövdesini arabelleğe almak yerine, yukarıdaki katman tarafından okunmakta olduğu gibi serbest bırakmamızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="ecc32-150">`ChunkingReader`, gelen öbekleri en fazla yapılandırılabilir sayıda arabelleğe alınmış parçalara kadar arabelleğe aldığı bir kuyruğa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="ecc32-151">Bu en fazla sınıra ulaşıldığında, okuyucu yukarıdaki katmanda bulunan (yani yalnızca özgün ileti gövdesinden okunarak) veya en fazla alma zaman aşımına ulaşılana kadar iletilerin kuyruktan dönmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Parçalama kanalı alma mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="ecc32-153">Öbek programlama modeli</span><span class="sxs-lookup"><span data-stu-id="ecc32-153">Chunking Programming Model</span></span>

<span data-ttu-id="ecc32-154">Hizmet geliştiricileri, sözleşme içindeki işlemlere `ChunkingBehavior` özniteliğini uygulayarak hangi iletilerin öbekli olduğunu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="ecc32-155">Özniteliği, geliştiricinin giriş mesajı, çıkış iletisi veya her ikisi için de uygulanıp uygulanmadığını belirtmesini sağlayan bir `AppliesTo` özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="ecc32-156">Aşağıdaki örnek `ChunkingBehavior` özniteliğin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ecc32-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="ecc32-157">`ChunkingBindingElement`, bu programlama modelinden, iletileri öbekli olacak şekilde tanımlayan eylem URI 'lerinin bir listesini derler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="ecc32-158">Her giden ileti eylemi, iletinin öbekli olarak mı yoksa doğrudan mi gönderileceğini öğrenmek için bu listeyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="ecc32-159">Gönderme Işlemini uygulama</span><span class="sxs-lookup"><span data-stu-id="ecc32-159">Implementing the Send Operation</span></span>

<span data-ttu-id="ecc32-160">Yüksek düzeyde, Gönder işlemi önce giden iletinin öbekli olup olmadığını denetler ve yoksa iletiyi doğrudan iç kanalı kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="ecc32-161">İleti öbekli olması gerekiyorsa, Send yeni bir `ChunkingWriter` oluşturur ve bu `ChunkingWriter`geçirerek giden iletide `WriteBodyContents` çağırır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="ecc32-162">`ChunkingWriter`, ileti öbek oluşturma (özgün ileti üstbilgilerini başlangıç öbek iletisine kopyalama dahil) ve iç kanalı kullanarak öbekleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="ecc32-163">Dikkat edilecek bazı ayrıntılar:</span><span class="sxs-lookup"><span data-stu-id="ecc32-163">A few details worth noting:</span></span>

- <span data-ttu-id="ecc32-164">`CommunicationState` açık olduğundan emin olmak için ilk çağrıları `ThrowIfDisposedOrNotOpened` gönderin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="ecc32-165">Gönderme, her oturum için tek seferde yalnızca bir ileti gönderilebilmesi için eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="ecc32-166">Bir öbekli ileti gönderilirken sıfırlanan `sendingDone` adlı bir `ManualResetEvent` vardır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="ecc32-167">Öbek iletisi gönderildikten sonra bu olay ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="ecc32-168">Send yöntemi, giden iletiyi göndermeyi denemeden önce bu olayın ayarlanmış olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="ecc32-169">Send, gönderirken eşitlenen durum değişikliklerini engellemek için `CommunicationObject.ThisLock` kilitler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="ecc32-170"><xref:System.ServiceModel.Channels.CommunicationObject> durumlar ve durum makinesi hakkında daha fazla bilgi için <xref:System.ServiceModel.Channels.CommunicationObject> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ecc32-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="ecc32-171">Gönderme için geçirilen zaman aşımı, tüm öbeklerin gönderilmesini içeren gönderme işleminin tamamına yönelik zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="ecc32-172">Özgün ileti gövdesinin tamamını arabelleğe almayı önlemek için özel <xref:System.Xml.XmlDictionaryWriter> tasarımı seçildi.</span><span class="sxs-lookup"><span data-stu-id="ecc32-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="ecc32-173">`message.GetReaderAtBodyContents` kullanarak gövdede <xref:System.Xml.XmlDictionaryReader> alırız, tüm gövdenin ara belleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="ecc32-174">Bunun yerine, `message.WriteBodyContents`geçirilen özel bir <xref:System.Xml.XmlDictionaryWriter> vardır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="ecc32-175">İleti, yazıcı üzerinde WriteBase64 çağırdığında, yazıcı paketleri ileti halinde parçalara ayırır ve bunları iç kanalı kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="ecc32-176">WriteBase64 blokları öbek gönderilene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="ecc32-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="ecc32-177">Alma Işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="ecc32-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="ecc32-178">Yüksek düzeyde, alma işlemi ilk önce gelen iletinin `null` olmadığını ve eyleminin `ChunkingAction`olduğunu denetler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="ecc32-179">Her iki ölçütü de karşılamıyorsa ileti alma işleminden değişmeden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ecc32-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="ecc32-180">Aksi takdirde, al yeni bir `ChunkingReader` ve etrafında Sarmalanan yeni bir `ChunkingMessage` oluşturur (`GetNewChunkingMessage`çağırarak).</span><span class="sxs-lookup"><span data-stu-id="ecc32-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="ecc32-181">Bu yeni `ChunkingMessage`döndürmeden önce, bir döngüsünde `innerChannel.Receive` çağıran ve son öbek iletisi alınana veya alma zaman aşımı düzeltilinceye kadar `ChunkingReader` öbeklere sahip olan `ReceiveChunkLoop`yürütmek için bir ThreadPool iş parçacığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="ecc32-182">Dikkat edilecek bazı ayrıntılar:</span><span class="sxs-lookup"><span data-stu-id="ecc32-182">A few details worth noting:</span></span>

- <span data-ttu-id="ecc32-183">Gönder gibi, `CommunicationState` açık olduğundan emin olmak için ilk çağrı Al `ThrowIfDisposedOrNotOepned`.</span><span class="sxs-lookup"><span data-stu-id="ecc32-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="ecc32-184">Alma işlemi, oturumdan bir seferde yalnızca bir ileti alınabilmesi için de eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="ecc32-185">Bu durum, bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm alınan iletilerin, son öbek iletisi alınana kadar bu yeni öbek sırası içinde öbeklerinin olması beklendiğinden özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="ecc32-186">Alma, şu anda öbekli olmayan bir iletiye ait olan tüm parçalar alındığından iç kanaldan ileti çekmez.</span><span class="sxs-lookup"><span data-stu-id="ecc32-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="ecc32-187">Bunu gerçekleştirmek için al, yeni bir öbek iletisi alındığında bitiş öbek iletisi alındığında ve sıfırlandığında ayarlanan `currentMessageCompleted`adlı `ManualResetEvent` kullanır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="ecc32-188">Gönderme, alma işleminden farklı olarak alma sırasında eşitlenmiş durum geçişlerini engellemez.</span><span class="sxs-lookup"><span data-stu-id="ecc32-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="ecc32-189">Örneğin, alma sırasında çağrılabilir ve özgün iletinin bekleyen alımı tamamlanana veya belirtilen zaman aşımı değerine ulaşılana kadar beklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="ecc32-190">Alma işlemi sırasında geçen zaman aşımı, tüm öbeklerin alınması dahil olmak üzere tüm alma işlemleri için zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="ecc32-191">İletiyi kullanan Katman, gelen öbek iletilerinin hızından daha düşük bir hızda ileti gövdesini kullanıyorsa, `ChunkingReader` bu gelen öbekleri `ChunkingBindingElement.MaxBufferedChunks`belirtilen sınıra kadar arabelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="ecc32-192">Bu sınıra ulaşıldığında, arabelleğe alınmış bir öbek tüketilene veya alma zaman aşımına ulaşılana kadar alt katmandan daha fazla öbek çekilmeyen bir değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="ecc32-193">CommunicationObject geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="ecc32-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="ecc32-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="ecc32-194">OnOpen</span></span>

<span data-ttu-id="ecc32-195">`OnOpen`, iç kanalı açmak için `innerChannel.Open` çağırır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="ecc32-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="ecc32-196">OnClose</span></span>

<span data-ttu-id="ecc32-197">`OnClose`, `true` `stopReceive`, durdurmak için bekleyen `ReceiveChunkLoop` sinyali verecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="ecc32-198">Daha sonra, `ReceiveChunkLoop` durdurulduğunda ayarlanan `receiveStopped` <xref:System.Threading.ManualResetEvent>bekler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="ecc32-199">`ReceiveChunkLoop` belirtilen zaman aşımı süresi içinde durduğu varsayılarak, geri kalan zaman aşımı ile `innerChannel.Close` `OnClose` çağırır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="ecc32-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="ecc32-200">OnAbort</span></span>

<span data-ttu-id="ecc32-201">`OnAbort`, iç kanalı durdurmak için `innerChannel.Abort` çağırır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="ecc32-202">Bekleyen bir `ReceiveChunkLoop` varsa, bekleyen `innerChannel.Receive` çağrısından bir özel durum alır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="ecc32-203">Onhatalı</span><span class="sxs-lookup"><span data-stu-id="ecc32-203">OnFaulted</span></span>

<span data-ttu-id="ecc32-204">`ChunkingChannel` kanal hata verdi ve `OnFaulted` geçersiz kılınmadığında özel bir davranış gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="ecc32-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="ecc32-205">Kanal fabrikası uygulama</span><span class="sxs-lookup"><span data-stu-id="ecc32-205">Implementing Channel Factory</span></span>

<span data-ttu-id="ecc32-206">`ChunkingChannelFactory`, iç kanal fabrikasında `ChunkingDuplexSessionChannel` örnekleri ve basamaklı durum geçişleri oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="ecc32-207">`OnCreateChannel`, iç kanal fabrikası kullanarak `IDuplexSessionChannel` bir iç kanal oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="ecc32-208">Daha sonra bu iç kanalı, yığın olarak kullanılacak ileti eylemlerinin listesiyle birlikte geçirerek yeni bir `ChunkingDuplexSessionChannel` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="ecc32-209">Yığın olarak kullanılacak ileti eylemlerinin listesi ve arabellekteki öbeklerin en fazla sayısı, oluşturucusunun `ChunkingChannelFactory` geçirilen iki parametredir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="ecc32-210">`ChunkingBindingElement` bölümünde bu değerlerin nereden geldiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="ecc32-211">`OnOpen`, `OnClose`, `OnAbort` ve zaman uyumsuz eşdeğerleri, iç kanal fabrikasında karşılık gelen durum geçiş yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="ecc32-212">Kanal dinleyicisi uygulama</span><span class="sxs-lookup"><span data-stu-id="ecc32-212">Implementing Channel Listener</span></span>

<span data-ttu-id="ecc32-213">`ChunkingChannelListener`, iç kanal dinleyicisinin etrafındaki bir sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="ecc32-214">Ana işlevi, bu iç kanal dinleyicisine yapılan temsilci çağrılarının yanı sıra yeni `ChunkingDuplexSessionChannels` iç kanal dinleyicisinden kabul edilen kanallara sarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="ecc32-215">Bu `OnAcceptChannel` ve `OnEndAcceptChannel`yapılır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="ecc32-216">Yeni oluşturulan `ChunkingDuplexSessionChannel`, daha önce açıklanan diğer parametrelerle birlikte iç kanalı geçti.</span><span class="sxs-lookup"><span data-stu-id="ecc32-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="ecc32-217">Bağlama öğesi ve bağlamayı uygulama</span><span class="sxs-lookup"><span data-stu-id="ecc32-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="ecc32-218">`ChunkingBindingElement`, `ChunkingChannelFactory` ve `ChunkingChannelListener`oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="ecc32-219">`ChunkingBindingElement`, `CanBuildChannelFactory`\<T > ve `CanBuildChannelListener`\<T > türü `IDuplexSessionChannel` (parçalama kanalının desteklediği tek kanal) ve bağlamadaki diğer bağlama öğelerinin bu kanal türünü destekleyip desteklemediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="ecc32-220">`BuildChannelFactory`\<T > öncelikle istenen kanal türünün oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="ecc32-221">Daha fazla bilgi için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="ecc32-221">For more information, see the following section.</span></span> <span data-ttu-id="ecc32-222">Daha sonra, iç kanal fabrikasını (`context.BuildInnerChannelFactory<IDuplexSessionChannel>`döndürülen), ileti eylemlerinin listesini ve arabelleğe alınan en fazla parça sayısını geçirerek yeni bir `ChunkingChannelFactory` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="ecc32-223">En fazla parça sayısı, `ChunkingBindingElement`tarafından sunulan `MaxBufferedChunks` adlı bir özellikten gelir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="ecc32-224">`BuildChannelListener<T>`, `ChunkingChannelListener` oluşturmak ve bunu iç kanal dinleyicisi geçirmek için benzer bir uygulamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="ecc32-225">Bu örnekte `TcpChunkingBinding`adında bir örnek bağlama bulunur.</span><span class="sxs-lookup"><span data-stu-id="ecc32-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="ecc32-226">Bu bağlama iki bağlama öğesinden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="ecc32-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="ecc32-227">`MaxBufferedChunks` özelliğini ayarlamanın yanı sıra, bağlama Ayrıca `MaxReceivedMessageSize` gibi bazı `TcpTransportBindingElement` özellikleri de ayarlar (üstbilgiler için `ChunkingUtils.ChunkSize` + 100KB bayt olarak ayarlar).</span><span class="sxs-lookup"><span data-stu-id="ecc32-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="ecc32-228">`TcpChunkingBinding` Ayrıca, `IBindingRuntimePreferences` uygular ve yalnızca zaman uyumlu alma çağrılarının uygulandığını belirten `ReceiveSynchronously` yönteminden true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecc32-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="ecc32-229">Hangi Iletileri öbekte belirleme</span><span class="sxs-lookup"><span data-stu-id="ecc32-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="ecc32-230">Öbek oluşturma kanalı yalnızca `ChunkingBehavior` özniteliği aracılığıyla tanımlanan iletileri parçalara parçalar.</span><span class="sxs-lookup"><span data-stu-id="ecc32-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="ecc32-231">`ChunkingBehavior` sınıfı `IOperationBehavior` uygular ve `AddBindingParameter` metodu çağırarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ecc32-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="ecc32-232">Bu yöntemde `ChunkingBehavior`, hangi iletilerin öbekli olması gerektiğini belirleyen `AppliesTo` özelliğinin (`InMessage`, `OutMessage` veya her ikisi) değerini inceler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="ecc32-233">Daha sonra bu iletilerin her birinin eylemini alır (`OperationDescription`Ileti koleksiyonundan) ve bir `ChunkingBindingParameter`örneği içinde bulunan bir dize koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="ecc32-234">Daha sonra bu `ChunkingBindingParameter`, belirtilen `BindingParameterCollection`ekler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="ecc32-235">Bu `BindingParameterCollection`, bağlama öğesi kanal fabrikası veya kanal dinleyicisi oluşturduğunda bağlamadaki her bağlama öğesine `BindingContext` geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="ecc32-236">`ChunkingBindingElement``BuildChannelFactory<T>` ve `BuildChannelListener<T>`, bu `ChunkingBindingParameter` `BindingContext’`s `BindingParameterCollection`dışına çekin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="ecc32-237">`ChunkingBindingParameter` içinde yer alan eylemler koleksiyonu `ChunkingChannelFactory` veya `ChunkingChannelListener`geçirilir ve bu da `ChunkingDuplexSessionChannel`geçirir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="ecc32-238">Örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ecc32-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ecc32-239">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ecc32-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ecc32-240">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="ecc32-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="ecc32-241">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ecc32-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="ecc32-242">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="ecc32-243">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="ecc32-244">Önce Service. exe ' yi çalıştırın, sonra Client. exe ' yi çalıştırın ve çıktı için hem konsol pencerelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="ecc32-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="ecc32-245">Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ecc32-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="ecc32-246">İstemci:</span><span class="sxs-lookup"><span data-stu-id="ecc32-246">Client:</span></span>

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

<span data-ttu-id="ecc32-247">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="ecc32-247">Server:</span></span>

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
