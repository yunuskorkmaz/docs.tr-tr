---
description: 'Daha fazla bilgi edinin: öbek oluşturma kanalı'
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 826db33186aa8e01ade9123d6b0d8b696b7e77ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778782"
---
# <a name="chunking-channel"></a><span data-ttu-id="10703-103">Öbekleme Kanalı</span><span class="sxs-lookup"><span data-stu-id="10703-103">Chunking Channel</span></span>

<span data-ttu-id="10703-104">Windows Communication Foundation (WCF) kullanarak büyük iletiler gönderirken, bu iletileri arabelleğe almak için kullanılan bellek miktarının sınırlanmasından genellikle tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="10703-104">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="10703-105">Olası bir çözüm, ileti gövdesinin akışını (verilerin toplu olarak gövdesinde olduğu varsayıldığında) sağlar.</span><span class="sxs-lookup"><span data-stu-id="10703-105">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="10703-106">Ancak bazı protokollerin iletinin tamamının arabelleğe alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10703-106">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="10703-107">Güvenilir Mesajlaşma ve güvenlik iki tür örnektir.</span><span class="sxs-lookup"><span data-stu-id="10703-107">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="10703-108">Diğer bir olası çözüm de büyük iletiyi öbek adı verilen küçük iletilere bölmek, bu öbekleri tek seferde bir öbek göndermek ve alma tarafında büyük iletiyi edilmeyen.</span><span class="sxs-lookup"><span data-stu-id="10703-108">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="10703-109">Uygulamanın kendisi bu parçalama ve parçalama işlemlerini yapmak için özel bir kanal kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="10703-109">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="10703-110">Öbek oluşturma kanalı örneği, özel bir protokol veya katmanlı kanalın, rastgele büyük iletileri parçalama ve parçalama için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10703-110">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="10703-111">Parçalama her zaman yalnızca gönderilecek iletinin tamamı oluşturulduktan sonra kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10703-111">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="10703-112">Bir parçalama kanalının her zaman bir güvenlik kanalının ve güvenilir bir oturum kanalının altında katmanlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10703-112">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="10703-113">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="10703-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10703-114">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="10703-114">The samples may already be installed on your machine.</span></span> <span data-ttu-id="10703-115">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10703-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="10703-116">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="10703-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10703-117">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="10703-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="10703-118">Kanal varsayımları ve sınırlamaları parçalama</span><span class="sxs-lookup"><span data-stu-id="10703-118">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="10703-119">İleti yapısı</span><span class="sxs-lookup"><span data-stu-id="10703-119">Message Structure</span></span>

<span data-ttu-id="10703-120">Öbek oluşturma kanalı, iletilerin öbeklenmesini sağlamak için aşağıdaki ileti yapısını varsayar:</span><span class="sxs-lookup"><span data-stu-id="10703-120">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="10703-121">ServiceModel kullanılırken, 1 girdi parametresine sahip sözleşme işlemleri giriş iletileri için bu ileti şekliyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10703-121">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="10703-122">Benzer şekilde, 1 çıkış parametresi veya dönüş değeri olan sözleşme işlemleri, çıkış iletileri için bu ileti şekliyle uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="10703-122">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="10703-123">Bu tür işlemlere örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="10703-123">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="10703-124">Oturumlar</span><span class="sxs-lookup"><span data-stu-id="10703-124">Sessions</span></span>

<span data-ttu-id="10703-125">Öbek oluşturma kanalı, iletilerin sıralı iletiler (öbekler) tesliminde tam olarak bir kez teslim edilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="10703-125">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="10703-126">Bu, temeldeki kanal yığınının oturumsuz olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="10703-126">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="10703-127">Oturumlar, taşıma (örneğin, TCP aktarımı) veya bir oturum Protokolü kanalı (örneğin, Reliableoturum kanalı) tarafından sağlanırlar.</span><span class="sxs-lookup"><span data-stu-id="10703-127">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="10703-128">Zaman uyumsuz gönderme ve alma</span><span class="sxs-lookup"><span data-stu-id="10703-128">Asynchronous Send and Receive</span></span>

<span data-ttu-id="10703-129">Zaman uyumsuz gönderme ve alma yöntemleri, parçalama kanalı örneğinin bu sürümünde uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="10703-129">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="10703-130">Kümeleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="10703-130">Chunking Protocol</span></span>

<span data-ttu-id="10703-131">Öbek oluşturma kanalı, bir dizi öbekin başlangıcını ve sonunu ve her öbekin sıra numarasını belirten bir protokol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10703-131">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="10703-132">Aşağıdaki üç örnek ileti, her birinin ana yönlerini tanımlayan yorumlarla başlangıç, öbek ve son iletileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="10703-132">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="10703-133">Iletiyi Başlat</span><span class="sxs-lookup"><span data-stu-id="10703-133">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="10703-134">Öbek Iletisi</span><span class="sxs-lookup"><span data-stu-id="10703-134">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="10703-135">Bitiş Iletisi</span><span class="sxs-lookup"><span data-stu-id="10703-135">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="10703-136">Parçalama kanalı mimarisi</span><span class="sxs-lookup"><span data-stu-id="10703-136">Chunking Channel Architecture</span></span>

<span data-ttu-id="10703-137">Öbek oluşturma kanalı, `IDuplexSessionChannel` yüksek düzeyde olan ve tipik kanal mimarisini izleyen bir düzeydir.</span><span class="sxs-lookup"><span data-stu-id="10703-137">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="10703-138">`ChunkingBindingElement`Ve bir oluşturabilir `ChunkingChannelFactory` `ChunkingChannelListener` .</span><span class="sxs-lookup"><span data-stu-id="10703-138">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="10703-139">, İstendiğinde `ChunkingChannelFactory` örnek oluşturur `ChunkingChannel` .</span><span class="sxs-lookup"><span data-stu-id="10703-139">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="10703-140">, `ChunkingChannelListener` `ChunkingChannel` Yeni bir iç kanal kabul edildiğinde örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10703-140">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="10703-141">`ChunkingChannel`Kendi kendine ileti göndermekten ve onlardan sorumlu olur.</span><span class="sxs-lookup"><span data-stu-id="10703-141">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="10703-142">Bir sonraki düzeyde, `ChunkingChannel` öbek protokolünü uygulamak için çeşitli bileşenlere bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="10703-142">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="10703-143">Gönderme tarafında kanal, <xref:System.Xml.XmlDictionaryWriter> `ChunkingWriter` gerçek parçalama yapan bir özel çağırılır.</span><span class="sxs-lookup"><span data-stu-id="10703-143">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="10703-144">`ChunkingWriter` öbekleri göndermek için doğrudan iç kanalı kullanır.</span><span class="sxs-lookup"><span data-stu-id="10703-144">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="10703-145">Özel kullanmak, `XmlDictionaryWriter` özgün iletinin büyük gövdesi yazıldığı için öbekleri göndermemizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="10703-145">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="10703-146">Bu, tüm özgün iletiyi arabelleğe sunduğumuz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="10703-146">This means we do not buffer the entire original message.</span></span>

![Parçalama kanalı gönderme mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="10703-148">Alma tarafında, `ChunkingChannel` iç kanaldan iletiler çeker ve bunları <xref:System.Xml.XmlDictionaryReader> `ChunkingReader` gelen öbeklerden özgün iletiyi reconstitutes bir özel çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="10703-148">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="10703-149">`ChunkingChannel` Bunu `ChunkingReader` adlı özel bir `Message` uygulamada sarmalanmış `ChunkingMessage` ve bu iletiyi yukarıdaki katmana döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="10703-149">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="10703-150">Bu ve birleşimi, özgün ileti gövdesinin `ChunkingReader` `ChunkingMessage` tüm özgün ileti gövdesini arabelleğe almak yerine yukarıdaki katman tarafından okunmakta olduğundan, özgün ileti gövdesini serbest bırakmamızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="10703-150">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="10703-151">`ChunkingReader` , gelen öbekleri en fazla yapılandırılabilir sayıda arabelleğe alınmış parçalara kadar arabelleğe aldığı bir kuyruğa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="10703-151">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="10703-152">Bu en fazla sınıra ulaşıldığında, okuyucu yukarıdaki katmanda bulunan (yani yalnızca özgün ileti gövdesinden okunarak) veya en fazla alma zaman aşımına ulaşılana kadar iletilerin kuyruktan dönmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="10703-152">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Parçalama kanalı alma mimarisini gösteren diyagram.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="10703-154">Öbek programlama modeli</span><span class="sxs-lookup"><span data-stu-id="10703-154">Chunking Programming Model</span></span>

<span data-ttu-id="10703-155">Hizmet geliştiricileri, `ChunkingBehavior` sözleşme içindeki işlemlere özniteliği uygulayarak hangi iletilerin öbeklere göre olduğunu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="10703-155">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="10703-156">Özniteliği, `AppliesTo` geliştiricinin giriş mesajı, çıkış iletisi veya her ikisi için de parçalama uygulanıp uygulanmadığını belirtmesini sağlayan bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="10703-156">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="10703-157">Aşağıdaki örnek özniteliğin kullanımını gösterir `ChunkingBehavior` :</span><span class="sxs-lookup"><span data-stu-id="10703-157">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="10703-158">Bu programlama modelinde, `ChunkingBindingElement` iletileri öbekli olacak şekilde tanımlayan eylem URI 'lerinin bir listesini derler.</span><span class="sxs-lookup"><span data-stu-id="10703-158">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="10703-159">Her giden ileti eylemi, iletinin öbekli olarak mı yoksa doğrudan mi gönderileceğini öğrenmek için bu listeyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="10703-159">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="10703-160">Gönderme Işlemini uygulama</span><span class="sxs-lookup"><span data-stu-id="10703-160">Implementing the Send Operation</span></span>

<span data-ttu-id="10703-161">Yüksek düzeyde, Gönder işlemi önce giden iletinin öbekli olup olmadığını denetler ve yoksa iletiyi doğrudan iç kanalı kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="10703-161">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="10703-162">İleti öbekli olması gerekiyorsa, Send `ChunkingWriter` `WriteBodyContents` bunu geçirerek giden iletide yeni bir ve çağrılar oluşturur `ChunkingWriter` .</span><span class="sxs-lookup"><span data-stu-id="10703-162">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="10703-163">`ChunkingWriter`Ardından ileti öbek (özgün ileti üstbilgilerini başlangıç öbeğiyle kopyalama dahil) ve iç kanalı kullanarak öbekleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="10703-163">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="10703-164">Dikkat edilecek bazı ayrıntılar:</span><span class="sxs-lookup"><span data-stu-id="10703-164">A few details worth noting:</span></span>

- <span data-ttu-id="10703-165">`ThrowIfDisposedOrNotOpened`Açık olduğundan emin olmak için ilk çağrıları gönderin `CommunicationState` .</span><span class="sxs-lookup"><span data-stu-id="10703-165">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="10703-166">Gönderme, her oturum için tek seferde yalnızca bir ileti gönderilebilmesi için eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="10703-166">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="10703-167">`ManualResetEvent` `sendingDone` Bir öbekli ileti gönderilirken sıfırlanan bir adlandırılmış adı vardır.</span><span class="sxs-lookup"><span data-stu-id="10703-167">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="10703-168">Öbek iletisi gönderildikten sonra bu olay ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="10703-168">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="10703-169">Send yöntemi, giden iletiyi göndermeyi denemeden önce bu olayın ayarlanmış olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="10703-169">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="10703-170">Gönderme, `CommunicationObject.ThisLock` gönderme sırasında eşitlenen durum değişikliklerini engellemek için ' a kilitler.</span><span class="sxs-lookup"><span data-stu-id="10703-170">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="10703-171"><xref:System.ServiceModel.Channels.CommunicationObject>Durumlar ve durum makinesi hakkında daha fazla bilgi için belgelere bakın <xref:System.ServiceModel.Channels.CommunicationObject> .</span><span class="sxs-lookup"><span data-stu-id="10703-171">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="10703-172">Gönderme için geçirilen zaman aşımı, tüm öbeklerin gönderilmesini içeren gönderme işleminin tamamına yönelik zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10703-172">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="10703-173">Özel <xref:System.Xml.XmlDictionaryWriter> Tasarım, özgün ileti gövdesinin tamamını arabelleğe almayı önlemek için seçildi.</span><span class="sxs-lookup"><span data-stu-id="10703-173">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="10703-174">Gövdeyi <xref:System.Xml.XmlDictionaryReader> kullanarak gövdenin `message.GetReaderAtBodyContents` tamamını kullanırsanız, tüm gövdenin ara belleğe alınacaksa.</span><span class="sxs-lookup"><span data-stu-id="10703-174">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="10703-175">Bunun yerine, öğesine geçirilen özel bir sunuyoruz  <xref:System.Xml.XmlDictionaryWriter> `message.WriteBodyContents` .</span><span class="sxs-lookup"><span data-stu-id="10703-175">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="10703-176">İleti, yazıcı üzerinde WriteBase64 çağırdığında, yazıcı paketleri ileti halinde parçalara ayırır ve bunları iç kanalı kullanarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="10703-176">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="10703-177">WriteBase64 blokları öbek gönderilene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="10703-177">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="10703-178">Alma Işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="10703-178">Implementing the Receive Operation</span></span>

<span data-ttu-id="10703-179">Yüksek düzeyde, alma işlemi önce gelen iletinin olmadığını `null` ve eyleminin olduğunu denetler `ChunkingAction` .</span><span class="sxs-lookup"><span data-stu-id="10703-179">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="10703-180">Her iki ölçütü de karşılamıyorsa ileti alma işleminden değişmeden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="10703-180">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="10703-181">Aksi takdirde, alma yeni bir `ChunkingReader` ve etrafında yeni bir `ChunkingMessage` sarmalanmış oluşturur (çağırarak `GetNewChunkingMessage` ).</span><span class="sxs-lookup"><span data-stu-id="10703-181">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="10703-182">Bu yeni döndürmeden önce `ChunkingMessage` , alma işlemi yürütmek için bir ThreadPool iş parçacığı kullanır, bu, `ReceiveChunkLoop` `innerChannel.Receive` döngü içinde çağrı yapan ve `ChunkingReader` son öbek iletisi alınana veya alma zaman aşımı alınana kadar öbeklerin parçalara geçmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="10703-182">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="10703-183">Dikkat edilecek bazı ayrıntılar:</span><span class="sxs-lookup"><span data-stu-id="10703-183">A few details worth noting:</span></span>

- <span data-ttu-id="10703-184">Send gibi, `ThrowIfDisposedOrNotOepned` açık olduğundan emin olmak için ilk çağrıları alın `CommunicationState` .</span><span class="sxs-lookup"><span data-stu-id="10703-184">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="10703-185">Alma işlemi, oturumdan bir seferde yalnızca bir ileti alınabilmesi için de eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="10703-185">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="10703-186">Bu durum, bir başlangıç öbek iletisi alındıktan sonra, sonraki tüm alınan iletilerin, son öbek iletisi alınana kadar bu yeni öbek sırası içinde öbeklerinin olması beklendiğinden özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="10703-186">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="10703-187">Alma, şu anda öbekli olmayan bir iletiye ait olan tüm parçalar alındığından iç kanaldan ileti çekmez.</span><span class="sxs-lookup"><span data-stu-id="10703-187">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="10703-188">Bunu gerçekleştirmek için al, yeni bir `ManualResetEvent` `currentMessageCompleted` öbek iletisi alındığında son öbek iletisi alındığında ve sıfırlandığında ayarlanan adlandırılmış bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="10703-188">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="10703-189">Gönderme, alma işleminden farklı olarak alma sırasında eşitlenmiş durum geçişlerini engellemez.</span><span class="sxs-lookup"><span data-stu-id="10703-189">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="10703-190">Örneğin, alma sırasında çağrılabilir ve özgün iletinin bekleyen alımı tamamlanana veya belirtilen zaman aşımı değerine ulaşılana kadar beklenebilir.</span><span class="sxs-lookup"><span data-stu-id="10703-190">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="10703-191">Alma işlemi sırasında geçen zaman aşımı, tüm öbeklerin alınması dahil olmak üzere tüm alma işlemleri için zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10703-191">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="10703-192">İletiyi tüketen katman, gelen öbek iletilerinin hızından daha düşük bir hızda ileti gövdesini kullanıyorsa, `ChunkingReader` gelen öbeklerin tarafından belirtilen sınıra kadar olan arabelleklerini arabelleğe alır `ChunkingBindingElement.MaxBufferedChunks` .</span><span class="sxs-lookup"><span data-stu-id="10703-192">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="10703-193">Bu sınıra ulaşıldığında, arabelleğe alınmış bir öbek tüketilene veya alma zaman aşımına ulaşılana kadar alt katmandan daha fazla öbek çekilmeyen bir değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="10703-193">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="10703-194">CommunicationObject geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="10703-194">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="10703-195">OnOpen</span><span class="sxs-lookup"><span data-stu-id="10703-195">OnOpen</span></span>

<span data-ttu-id="10703-196">`OnOpen``innerChannel.Open`iç kanalı açmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="10703-196">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="10703-197">OnClose</span><span class="sxs-lookup"><span data-stu-id="10703-197">OnClose</span></span>

<span data-ttu-id="10703-198">`OnClose` ilk `stopReceive` olarak `true` , durdurmak için bekleyen ' i işaret etmek üzere ayarlar `ReceiveChunkLoop` .</span><span class="sxs-lookup"><span data-stu-id="10703-198">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="10703-199">Ardından, `receiveStopped` <xref:System.Threading.ManualResetEvent> durdurulduğunda ayarlanan için bekler `ReceiveChunkLoop` .</span><span class="sxs-lookup"><span data-stu-id="10703-199">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="10703-200">`ReceiveChunkLoop`Belirtilen zaman aşımı süresi içinde durduğu varsayılarak, `OnClose` `innerChannel.Close` kalan zaman aşımı ile çağrılar yapılır.</span><span class="sxs-lookup"><span data-stu-id="10703-200">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="10703-201">OnAbort</span><span class="sxs-lookup"><span data-stu-id="10703-201">OnAbort</span></span>

<span data-ttu-id="10703-202">`OnAbort``innerChannel.Abort`iç kanalı durdurmak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="10703-202">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="10703-203">Bekleyen bir sorun varsa, `ReceiveChunkLoop` bekleyen çağrıdan bir özel durum alır `innerChannel.Receive` .</span><span class="sxs-lookup"><span data-stu-id="10703-203">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="10703-204">Onhatalı</span><span class="sxs-lookup"><span data-stu-id="10703-204">OnFaulted</span></span>

<span data-ttu-id="10703-205">`ChunkingChannel`Kanal hata verdi durumunda özel bir davranış gerektirmez, bu nedenle `OnFaulted` geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="10703-205">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="10703-206">Kanal fabrikası uygulama</span><span class="sxs-lookup"><span data-stu-id="10703-206">Implementing Channel Factory</span></span>

<span data-ttu-id="10703-207">, `ChunkingChannelFactory` `ChunkingDuplexSessionChannel` İç kanal fabrikasına basamaklı durum geçişleri için ve örneklerinin oluşturulmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="10703-207">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="10703-208">`OnCreateChannel` iç kanal fabrikası oluşturmak için iç kanal fabrikasını kullanır `IDuplexSessionChannel` .</span><span class="sxs-lookup"><span data-stu-id="10703-208">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="10703-209">Daha sonra `ChunkingDuplexSessionChannel` Bu iç kanalı, yığın olarak kullanılacak ileti eylemlerinin listesi ve alma sırasında arabelleğe eklenecek en fazla parça sayısı ile birlikte geçen yeni bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10703-209">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="10703-210">Yığın olarak kullanılacak ileti eylemlerinin listesi ve arabellekteki öbeklerin en fazla sayısı, oluşturucusunda iki parametre olarak geçirilir `ChunkingChannelFactory` .</span><span class="sxs-lookup"><span data-stu-id="10703-210">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="10703-211">Üzerindeki bölümü, `ChunkingBindingElement` Bu değerlerin nereden geldiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10703-211">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="10703-212">`OnOpen`, `OnClose` `OnAbort` Ve zaman uyumsuz eşdeğerleri, iç kanal fabrikasında karşılık gelen durum geçiş yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="10703-212">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="10703-213">Kanal dinleyicisi uygulama</span><span class="sxs-lookup"><span data-stu-id="10703-213">Implementing Channel Listener</span></span>

<span data-ttu-id="10703-214">, Bir `ChunkingChannelListener` iç kanal dinleyicisi etrafında bir sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="10703-214">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="10703-215">Ana işlevinin, bu iç kanal dinleyicisine yönelik temsilci çağrılarının yanı sıra, `ChunkingDuplexSessionChannels` iç kanal dinleyicisinden kabul edilen yeni kanallar etrafında sarmalaması de vardır.</span><span class="sxs-lookup"><span data-stu-id="10703-215">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="10703-216">Bu, ve ' de yapılır `OnAcceptChannel` `OnEndAcceptChannel` .</span><span class="sxs-lookup"><span data-stu-id="10703-216">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="10703-217">Yeni oluşturulan, `ChunkingDuplexSessionChannel` daha önce açıklanan diğer parametrelerle birlikte iç kanalı geçti.</span><span class="sxs-lookup"><span data-stu-id="10703-217">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="10703-218">Bağlama öğesi ve bağlamayı uygulama</span><span class="sxs-lookup"><span data-stu-id="10703-218">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="10703-219">`ChunkingBindingElement` , ve oluşturmaktan sorumludur `ChunkingChannelFactory` `ChunkingChannelListener` .</span><span class="sxs-lookup"><span data-stu-id="10703-219">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="10703-220">, ' `ChunkingBindingElement` In ve türünde olup olmadığını denetler `CanBuildChannelFactory` \<T> `CanBuildChannelListener` \<T> `IDuplexSessionChannel` (parçalama kanalının desteklediği tek kanal) ve bağlamadaki diğer bağlama öğelerinin bu kanal türünü destekleyip desteklemediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="10703-220">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="10703-221">`BuildChannelFactory`\<T> İlk olarak, istenen kanal türünün oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="10703-221">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="10703-222">Daha fazla bilgi için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="10703-222">For more information, see the following section.</span></span> <span data-ttu-id="10703-223">Daha sonra `ChunkingChannelFactory` , iç kanal fabrikası (öğesinden döndürülen `context.BuildInnerChannelFactory<IDuplexSessionChannel>` ), ileti eylemlerinin listesi ve arabelleğe alınan en fazla parça sayısı gibi yeni bir geçirme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10703-223">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="10703-224">En fazla parça sayısı `MaxBufferedChunks` , tarafından açığa çıkarılan adlı bir özellikten gelir `ChunkingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="10703-224">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="10703-225">`BuildChannelListener<T>` , `ChunkingChannelListener` iç kanal dinleyicisi oluşturma ve geçirme için benzer bir uygulamaya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="10703-225">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="10703-226">Bu örneğe eklenen örnek bir bağlama vardır `TcpChunkingBinding` .</span><span class="sxs-lookup"><span data-stu-id="10703-226">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="10703-227">Bu bağlama iki bağlama öğesinden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="10703-227">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="10703-228">Özelliği ayarlamanın yanı sıra `MaxBufferedChunks` , bağlama gibi bazı özellikler de ayarlanır `TcpTransportBindingElement` `MaxReceivedMessageSize` ( `ChunkingUtils.ChunkSize` üst bilgiler için + 100 KB bayt olarak ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="10703-228">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="10703-229">`TcpChunkingBinding` Ayrıca `IBindingRuntimePreferences` `ReceiveSynchronously` , yalnızca zaman uyumlu alma çağrılarının uygulandığını belirten yönteminden true değerini uygular.</span><span class="sxs-lookup"><span data-stu-id="10703-229">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="10703-230">Hangi Iletileri öbekte belirleme</span><span class="sxs-lookup"><span data-stu-id="10703-230">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="10703-231">Öbek oluşturma kanalı yalnızca özniteliği aracılığıyla tanımlanan iletileri parçalara parçalar `ChunkingBehavior` .</span><span class="sxs-lookup"><span data-stu-id="10703-231">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="10703-232">`ChunkingBehavior`Sınıfı, `IOperationBehavior` yöntemini çağırarak uygular ve uygulanır `AddBindingParameter` .</span><span class="sxs-lookup"><span data-stu-id="10703-232">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="10703-233">Bu yöntemde, `ChunkingBehavior` `AppliesTo` `InMessage` `OutMessage` hangi iletilerin öbekli olması gerektiğini belirleyen, özelliğin değerini (veya her ikisi) inceler.</span><span class="sxs-lookup"><span data-stu-id="10703-233">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="10703-234">Daha sonra bu iletilerin her birinin eylemini alır (üzerindeki Iletiler koleksiyonundan `OperationDescription` ) ve örneği içinde yer alan bir dize koleksiyonuna ekler `ChunkingBindingParameter` .</span><span class="sxs-lookup"><span data-stu-id="10703-234">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="10703-235">Daha sonra bunu `ChunkingBindingParameter` , belirtilen öğesine ekler `BindingParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="10703-235">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="10703-236">Bu, bağlama `BindingParameterCollection` `BindingContext` öğesi kanal fabrikası veya kanal dinleyicisi oluşturduğunda bağlamadaki her bağlama öğesinin içine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="10703-236">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="10703-237">`ChunkingBindingElement`' Nin uygulanması `BuildChannelFactory<T>` ve bu uygulamadan `BuildChannelListener<T>` `ChunkingBindingParameter` çekmesi `BindingContext’` `BindingParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="10703-237">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="10703-238">İçinde yer alan eylemlerin koleksiyonu `ChunkingBindingParameter` daha sonra veya ' a geçirilir ve `ChunkingChannelFactory` Bu da ' a geçirilir `ChunkingChannelListener` `ChunkingDuplexSessionChannel` .</span><span class="sxs-lookup"><span data-stu-id="10703-238">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="10703-239">Örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="10703-239">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="10703-240">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="10703-240">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="10703-241">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="10703-241">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="10703-242">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="10703-242">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="10703-243">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="10703-243">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="10703-244">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="10703-244">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="10703-245">Önce Service.exe çalıştırın, sonra Client.exe çalıştırıp her iki çıkış için de konsol pencerelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="10703-245">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="10703-246">Örneği çalıştırırken aşağıdaki çıktı beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="10703-246">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="10703-247">İstemci:</span><span class="sxs-lookup"><span data-stu-id="10703-247">Client:</span></span>

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

<span data-ttu-id="10703-248">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="10703-248">Server:</span></span>

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
