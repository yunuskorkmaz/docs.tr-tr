---
title: Öbekleme Kanalı
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: fafaef5f9e255adc9d8ff50748c7c82a7888c4cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073825"
---
# <a name="chunking-channel"></a><span data-ttu-id="269d5-102">Öbekleme Kanalı</span><span class="sxs-lookup"><span data-stu-id="269d5-102">Chunking Channel</span></span>
<span data-ttu-id="269d5-103">Windows Communication Foundation (WCF) kullanarak büyük iletileri gönderirken, genellikle bu iletileri arabelleğe almak için kullanılan bellek miktarını sınırlamak için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="269d5-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="269d5-104">Olası bir çözüm (toplu veri gövdesinde olduğunu varsayarak) ileti akışı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="269d5-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="269d5-105">Ancak bazı protokoller, iletinin tamamı arabelleğe alma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="269d5-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="269d5-106">Güvenilir Mesajlaşma ve güvenlik gibi iki örnek verilebilir.</span><span class="sxs-lookup"><span data-stu-id="269d5-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="269d5-107">Başka bir olası öbekleri adlı küçük iletilere büyük ileti ayırmak, söz konusu öbekleri bir öbek teker teker gönderilir ve alıcı tarafında büyük ileti yeniden oluşturmak için bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="269d5-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="269d5-108">Uygulama bu parçalama yapabilirsiniz ve serbest Öbekleme veya özel bir kanalda yapmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="269d5-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="269d5-109">Kümeleme kanal örnek nasıl bir özel protokolü veya katmanlı kanal Öbekleme ve büyük iletilerin XML'deki Öbekleme yapmak için kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="269d5-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="269d5-110">Gönderilecek iletinin tamamı bir yalnızca oluşturulan sonra Öbekleme her zaman işe.</span><span class="sxs-lookup"><span data-stu-id="269d5-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="269d5-111">Kümeleme kanal her zaman bir güvenlik kanalı ve bir güvenilir oturum kanalı altında katmanlı.</span><span class="sxs-lookup"><span data-stu-id="269d5-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="269d5-112">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="269d5-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="269d5-113">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="269d5-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="269d5-114">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="269d5-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="269d5-115">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="269d5-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="269d5-116">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="269d5-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="269d5-117">Kümeleme kanal varsayımlar ve sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="269d5-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="269d5-118">İleti yapısı</span><span class="sxs-lookup"><span data-stu-id="269d5-118">Message Structure</span></span>  
 <span data-ttu-id="269d5-119">Kümeleme kanalın iletilerin öbekli aşağıdaki ileti yapısını varsayılır:</span><span class="sxs-lookup"><span data-stu-id="269d5-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
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
  
 <span data-ttu-id="269d5-120">ServiceModel kullanırken, 1 giriş parametresi kendi giriş iletisi iletisinin bu şekli ile uyumlu olan işlemler sözleşme.</span><span class="sxs-lookup"><span data-stu-id="269d5-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="269d5-121">Benzer şekilde, bu şekilde, çıktı iletisi iletisinin 1 çıkış parametresi veya dönüş değeri sözleşme işlemleri uyumlu.</span><span class="sxs-lookup"><span data-stu-id="269d5-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="269d5-122">Bu tür işlemlerine örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="269d5-122">The following are examples of such operations:</span></span>  
  
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
  
### <a name="sessions"></a><span data-ttu-id="269d5-123">Oturumlar</span><span class="sxs-lookup"><span data-stu-id="269d5-123">Sessions</span></span>  
 <span data-ttu-id="269d5-124">Kümeleme kanal iletileri (parçalar) iletilerin sıralı teslim, kesinlikle bir kerelik teslim edilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="269d5-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="269d5-125">Bu, arka plandaki kanal yığın kapatamaması olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="269d5-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="269d5-126">Oturumlarının kapatamaması Protokolü kanal (örneğin, ReliableSession kanal) veya aktarım (örneğin, TCP taşıma) tarafından sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="269d5-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="269d5-127">Zaman uyumsuz gönderme ve alma</span><span class="sxs-lookup"><span data-stu-id="269d5-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="269d5-128">Zaman uyumsuz yöntemler gönderip kümeleme kanal örnek bu sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="269d5-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="269d5-129">Kümeleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="269d5-129">Chunking Protocol</span></span>  
 <span data-ttu-id="269d5-130">Kümeleme kanal başlangıç ve yanı sıra her bir öbeği sıra numarası öbekleri bir dizi sonuna belirten bir protokol tanımlar.</span><span class="sxs-lookup"><span data-stu-id="269d5-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="269d5-131">Aşağıdaki üç örnek iletileri başlangıcı, her önemli noktaları açıklayan bir yorum ile öbek ve son iletileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="269d5-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="269d5-132">Başlangıç iletisi</span><span class="sxs-lookup"><span data-stu-id="269d5-132">Start Message</span></span>  
  
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
  
### <a name="chunk-message"></a><span data-ttu-id="269d5-133">Öbek iletisi</span><span class="sxs-lookup"><span data-stu-id="269d5-133">Chunk Message</span></span>  
  
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
  
### <a name="end-message"></a><span data-ttu-id="269d5-134">Son ileti</span><span class="sxs-lookup"><span data-stu-id="269d5-134">End Message</span></span>  
  
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
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="269d5-135">Öbekleme kanalı mimarisi</span><span class="sxs-lookup"><span data-stu-id="269d5-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="269d5-136">Kümeleme kanal bir `IDuplexSessionChannel` tipik kanal mimari, yüksek bir düzeyde izler.</span><span class="sxs-lookup"><span data-stu-id="269d5-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="269d5-137">Var olan bir `ChunkingBindingElement` , yapılandırılabilir bir `ChunkingChannelFactory` ve `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="269d5-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="269d5-138">`ChunkingChannelFactory` Örneklerini oluşturur `ChunkingChannel` zaman bunu istenir.</span><span class="sxs-lookup"><span data-stu-id="269d5-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="269d5-139">`ChunkingChannelListener` Örneklerini oluşturur `ChunkingChannel` ne zaman yeni bir iç kanal kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="269d5-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="269d5-140">`ChunkingChannel` Kendisi ileti gönderme ve alma için sorumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="269d5-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="269d5-141">Aşağı, sonraki düzeyde `ChunkingChannel` kümeleme Protokolü uygulamak için çeşitli bileşenleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="269d5-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="269d5-142">Gönderme tarafında, özel bir kanal kullanan <xref:System.Xml.XmlDictionaryWriter> adlı `ChunkingWriter` gerçek Öbekleme yapar.</span><span class="sxs-lookup"><span data-stu-id="269d5-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> `ChunkingWriter` <span data-ttu-id="269d5-143">İç kanal öbekleri doğrudan göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="269d5-143">uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="269d5-144">Özel bir kullanarak `XmlDictionaryWriter` büyük iletisinin gövdesi, özgün yazıldığı gibi öbekleri göndermemizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="269d5-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="269d5-145">Bu, biz özgün iletinin tamamı arabellek yok anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="269d5-145">This means we do not buffer the entire original message.</span></span>  
  
 <span data-ttu-id="269d5-146">![Öbekleme kanalı](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span><span class="sxs-lookup"><span data-stu-id="269d5-146">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span></span>  
  
 <span data-ttu-id="269d5-147">Alma tarafında `ChunkingChannel` iç kanal gelen iletileri alır ve bunları özel bir uygulamalı <xref:System.Xml.XmlDictionaryReader> adlı `ChunkingReader`, gelen öbek özgün iletiden reconstitutes.</span><span class="sxs-lookup"><span data-stu-id="269d5-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> `ChunkingChannel` <span data-ttu-id="269d5-148">Bu sarmalar `ChunkingReader` özel `Message` adlı uygulama `ChunkingMessage` ve bu iletiyi yukarıdaki katmana döndürür.</span><span class="sxs-lookup"><span data-stu-id="269d5-148">wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="269d5-149">Bu birleşimi `ChunkingReader` ve `ChunkingMessage` tüm özgün ileti gövdesini arabelleğe alıp zorunda kalmak yerine katmanın üzerinde okunduğu şekilde özgün ileti gövdesi serbest öbek olanak sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="269d5-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> `ChunkingReader` <span data-ttu-id="269d5-150">bir kuyruk, burada arabelleğe alınan öbekleri yapılandırılabilir en fazla sayıya kadar gelen öbekleri arabelleğe alır sahiptir.</span><span class="sxs-lookup"><span data-stu-id="269d5-150">has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="269d5-151">Bu maksimum sınıra ulaşıldığında, okuyucu iletilerin kuyruktan yukarıdaki katmanı tarafından boşaltılır bekler (diğer bir deyişle, yalnızca özgün iletinin gövdesinden okuyarak) veya en fazla alana kadar zaman aşımına ulaşıldığı.</span><span class="sxs-lookup"><span data-stu-id="269d5-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 <span data-ttu-id="269d5-152">![Öbekleme kanalı](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span><span class="sxs-lookup"><span data-stu-id="269d5-152">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span></span>  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="269d5-153">Programlama modeli Öbekleme</span><span class="sxs-lookup"><span data-stu-id="269d5-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="269d5-154">Hizmet geliştiricileri, iletileri uygulayarak öbekli üzeresiniz belirtebilirsiniz `ChunkingBehavior` sözleşme işlemlerini özniteliği.</span><span class="sxs-lookup"><span data-stu-id="269d5-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="269d5-155">Öznitelik sunan bir `AppliesTo` Öbekleme giriş iletisi, çıktı iletisi veya her ikisi de uygulanıp uygulanmayacağını belirtmek Geliştirici izin veren özellik.</span><span class="sxs-lookup"><span data-stu-id="269d5-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="269d5-156">Aşağıdaki örnek, kullanımını gösterir. `ChunkingBehavior` özniteliği:</span><span class="sxs-lookup"><span data-stu-id="269d5-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
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
  
 <span data-ttu-id="269d5-157">Bu programlama modelinden `ChunkingBindingElement` eylem öbekli için iletileri tanımlayan bir URI'leri listesini derler.</span><span class="sxs-lookup"><span data-stu-id="269d5-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="269d5-158">Eylemin her Giden iletinin ileti öbekli veya doğrudan gönderilen belirlemek için bu listeyi karşı karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="269d5-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="269d5-159">Gönderme işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="269d5-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="269d5-160">Yüksek düzeyde, gönderme işlemi ilk giden ileti öbekli gerekir aksi takdirde, iç kanal kullanarak doğrudan ileti gönderir olup olmadığını ve denetler.</span><span class="sxs-lookup"><span data-stu-id="269d5-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="269d5-161">İleti öbekli, gönderme yeni bir oluşturur `ChunkingWriter` ve çağrıları `WriteBodyContents` giden iletide bu iletmeden `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="269d5-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="269d5-162">`ChunkingWriter` (Başlangıç öbek iletiyi özgün ileti üstbilgileri kopyalama dahil) ileti Öbekleme yapar ve iç kanal kullanarak öbekleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="269d5-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="269d5-163">Önemli birkaç ayrıntıları:</span><span class="sxs-lookup"><span data-stu-id="269d5-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="269d5-164">İlk çağrı gönderme `ThrowIfDisposedOrNotOpened` emin olmak için `CommunicationState` açılır.</span><span class="sxs-lookup"><span data-stu-id="269d5-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="269d5-165">Her oturum için bir kerede yalnızca bir ileti gönderilmesi için gönderme eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="269d5-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="269d5-166">Var olan bir `ManualResetEvent` adlı `sendingDone` öbekli bir ileti gönderildiğinde sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="269d5-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="269d5-167">Son öbek ileti gönderildikten sonra bu olay ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="269d5-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="269d5-168">Send yöntemi giden ileti göndermeye çalışmadan önce ayarlamak bu olay için bekler.</span><span class="sxs-lookup"><span data-stu-id="269d5-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="269d5-169">Kilitleri Gönder `CommunicationObject.ThisLock` önlemek için eşitleme durumu değişiklikleri gönderilirken.</span><span class="sxs-lookup"><span data-stu-id="269d5-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="269d5-170">Bkz: <xref:System.ServiceModel.Channels.CommunicationObject> hakkında daha fazla bilgi için belgelere <xref:System.ServiceModel.Channels.CommunicationObject> durumları ve Durum makinesi.</span><span class="sxs-lookup"><span data-stu-id="269d5-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="269d5-171">Gönderme geçirilen zaman aşımı, tüm öbekleri gönderme içeren tüm gönderme işlemi için zaman aşımı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="269d5-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="269d5-172">Özel <xref:System.Xml.XmlDictionaryWriter> tasarım, tüm özgün ileti gövdesini arabelleğe almayı önlemek için seçildi.</span><span class="sxs-lookup"><span data-stu-id="269d5-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="269d5-173">Alınacak olsaydık bir <xref:System.Xml.XmlDictionaryReader> gövdesi kullanma `message.GetReaderAtBodyContents` tüm gövdesinin arabelleğe.</span><span class="sxs-lookup"><span data-stu-id="269d5-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="269d5-174">Bunun yerine, özel bir sahibiz <xref:System.Xml.XmlDictionaryWriter> yapan `message.WriteBodyContents`.</span><span class="sxs-lookup"><span data-stu-id="269d5-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="269d5-175">İletiyi WriteBase64 yazıcısı, yazıcı iletileri parçalara'kurmak paketleri ve bunları gönderir çağrıları iç kanal kullanma.</span><span class="sxs-lookup"><span data-stu-id="269d5-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="269d5-176">Öbek gönderilene kadar WriteBase64 engeller.</span><span class="sxs-lookup"><span data-stu-id="269d5-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="269d5-177">Uygulama alma işlemi</span><span class="sxs-lookup"><span data-stu-id="269d5-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="269d5-178">Yüksek bir düzeyde alma işlemi önce gelen ileti olmadığını denetler `null` ve sahip olduğu eylem ise `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="269d5-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="269d5-179">Her iki ölçütleri karşılamıyorsa ileti alma değiştirilmeden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="269d5-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="269d5-180">Aksi takdirde, Al yeni bir oluşturur `ChunkingReader` ve yeni bir `ChunkingMessage` etrafında sarmalanmış (çağırarak `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="269d5-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="269d5-181">Bu yeni döndürmeden önce `ChunkingMessage`, alma kullanan bir iş parçacığı havuzu iş parçacığını yürütmek için `ReceiveChunkLoop`, çağıran `innerChannel.Receive` döngü ve öbekleri için ellerini `ChunkingReader` son öbek ileti alındığında veya alma işlemi zamanı aşımını isabet kadar.</span><span class="sxs-lookup"><span data-stu-id="269d5-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="269d5-182">Önemli birkaç ayrıntıları:</span><span class="sxs-lookup"><span data-stu-id="269d5-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="269d5-183">İlk çağrı gönderme gibi alan `ThrowIfDisposedOrNotOepned` emin olmak için `CommunicationState` açılır.</span><span class="sxs-lookup"><span data-stu-id="269d5-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="269d5-184">Alma oturum aynı anda yalnızca bir ileti alınabilmesi için de eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="269d5-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="269d5-185">Bu, başlangıç öbek iletisi alındıktan sonra sonraki alınan iletilerin tümünü bir son öbeği iletisi alınana kadar bu yeni öbek dizisi içindeki öbekleri olmaları beklenir çünkü özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="269d5-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="269d5-186">Alma şu anda devre dışı bırakmak öbekli iletinin ait öbeklerin tümü alınana kadar iç kanal iletilerden çekme gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="269d5-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="269d5-187">Bunu gerçekleştirmek için kullandığı almak bir `ManualResetEvent` adlı `currentMessageCompleted`, son öbek ileti alındı ve yeni bir başlangıç öbek ileti alındığında sıfırlama sırasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="269d5-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="269d5-188">Gönderme, alma alma sırasında eşitlenmiş durumu geçişleri engellemez.</span><span class="sxs-lookup"><span data-stu-id="269d5-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="269d5-189">Örneğin, yakın alma ve bekler sırasında özgün iletinin bekleyen alma tamamlandı veya belirtilen zaman aşımı değeri ulaşılana kadar çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="269d5-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="269d5-190">Alınacak geçirilen zaman aşımı tamamı için zaman aşımını alma gibi tüm parçalar içeren işlemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="269d5-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="269d5-191">İleti gövdesi gelen öbek iletileri hızdan daha düşük bir hızda iletiyi tüketir katmanı kullanıp kullanmadığına `ChunkingReader` tarafından belirtilen sınıra kadar gelen söz konusu öbekleri arabelleği `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="269d5-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="269d5-192">Bu sınıra ulaşıldığında, öbeği arabelleğe alınan bir Öbek ile kullanılan ya da alma zaman aşımı ulaşılana kadar daha düşük bir katmandan diğerine alınır.</span><span class="sxs-lookup"><span data-stu-id="269d5-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="269d5-193">CommunicationObject geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="269d5-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="269d5-194">Açıldığında</span><span class="sxs-lookup"><span data-stu-id="269d5-194">OnOpen</span></span>  
 `OnOpen` <span data-ttu-id="269d5-195">çağrıları `innerChannel.Open` iç kanal açın.</span><span class="sxs-lookup"><span data-stu-id="269d5-195">calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="269d5-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="269d5-196">OnClose</span></span>  
 `OnClose` <span data-ttu-id="269d5-197">öncelikle ayarlar `stopReceive` için `true` göstermek için bekleyen `ReceiveChunkLoop` durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="269d5-197">first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="269d5-198">Ardından bekler `receiveStopped` <xref:System.Threading.ManualResetEvent>, ne zaman ayarlanır `ReceiveChunkLoop` durdurur.</span><span class="sxs-lookup"><span data-stu-id="269d5-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="269d5-199">Varsayılarak `ReceiveChunkLoop` durdurur belirtilen süre içinde `OnClose` çağrıları `innerChannel.Close` kalan zaman aşımı ile.</span><span class="sxs-lookup"><span data-stu-id="269d5-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="269d5-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="269d5-200">OnAbort</span></span>  
 `OnAbort` <span data-ttu-id="269d5-201">çağrıları `innerChannel.Abort` iç kanal iptal etmek için.</span><span class="sxs-lookup"><span data-stu-id="269d5-201">calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="269d5-202">Varsa bir bekleyen `ReceiveChunkLoop` adresinden bir özel durum alır bekleyen `innerChannel.Receive` çağırın.</span><span class="sxs-lookup"><span data-stu-id="269d5-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="269d5-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="269d5-203">OnFaulted</span></span>  
 <span data-ttu-id="269d5-204">`ChunkingChannel` Kanal olduğunda özel davranış hatalı bunu gerektirmez `OnFaulted` değil geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="269d5-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="269d5-205">Kanal fabrikası uygulama</span><span class="sxs-lookup"><span data-stu-id="269d5-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="269d5-206">`ChunkingChannelFactory` Örneklerini oluşturmaktan sorumlu `ChunkingDuplexSessionChannel` ve iç kanal fabrikası basamaklı durumuna geçişler.</span><span class="sxs-lookup"><span data-stu-id="269d5-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 `OnCreateChannel` <span data-ttu-id="269d5-207">İç kanal fabrikası oluşturmak için kullandığı bir `IDuplexSessionChannel` iç kanal.</span><span class="sxs-lookup"><span data-stu-id="269d5-207">uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="269d5-208">Ardından yeni bir oluşturur `ChunkingDuplexSessionChannel` öbekli için ileti Eylemler ve öbekleri alma sırasında arabelleğe alınacak en fazla sayısını listesi ile birlikte bu iç kanal geçirme.</span><span class="sxs-lookup"><span data-stu-id="269d5-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="269d5-209">Öbekli için ileti Eylemler ve öbekleri arabelleğe alınacak en fazla sayısını listesi olan iki parametre geçirilen `ChunkingChannelFactory` kendi oluşturucusuna.</span><span class="sxs-lookup"><span data-stu-id="269d5-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="269d5-210">Bölüm `ChunkingBindingElement` bu değerlerin nereden geldiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="269d5-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="269d5-211">`OnOpen`, `OnClose`, `OnAbort` Ve zaman uyumsuz eşdeğerlerine üzerinde iç kanal fabrikası karşılık gelen durum geçiş yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="269d5-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="269d5-212">Kanal dinleyicisi uygulama</span><span class="sxs-lookup"><span data-stu-id="269d5-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="269d5-213">`ChunkingChannelListener` Bir iç kanal dinleyicisi çevresinde bir sarmalayıcı olan.</span><span class="sxs-lookup"><span data-stu-id="269d5-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="269d5-214">Ana işlevi, bu iç kanal dinleyicisi temsilci çağrılarını yanı sıra yeni sarmaktır `ChunkingDuplexSessionChannels` iç kanal dinleyicisinden kabul kanalları geçici bir çözüm.</span><span class="sxs-lookup"><span data-stu-id="269d5-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="269d5-215">Bu yapılır `OnAcceptChannel` ve `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="269d5-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="269d5-216">Yeni oluşturulan `ChunkingDuplexSessionChannel` iç kanal daha önce açıklanan diğer parametreler birlikte geçirilir.</span><span class="sxs-lookup"><span data-stu-id="269d5-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="269d5-217">Uygulama bağlama öğesi ve bağlama</span><span class="sxs-lookup"><span data-stu-id="269d5-217">Implementing Binding Element and Binding</span></span>  
 `ChunkingBindingElement` <span data-ttu-id="269d5-218">oluşturmaktan sorumlu `ChunkingChannelFactory` ve `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="269d5-218">is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="269d5-219">`ChunkingBindingElement` Denetler olup olmadığını T `CanBuildChannelFactory` \<T > ve `CanBuildChannelListener` \<T > türü `IDuplexSessionChannel` (yalnızca kanalı kümeleme kanalı tarafından desteklenen) ve bağlamayı diğer bağlama öğeleri bu destek Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="269d5-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 `BuildChannelFactory`<span data-ttu-id="269d5-220">\<T > ilk denetler istenen kanal türü oluşturulabilir ve ardından öbekli için ileti eylemlerin bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="269d5-220">\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="269d5-221">Daha fazla bilgi için aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="269d5-221">For more information, see the following section.</span></span> <span data-ttu-id="269d5-222">Ardından yeni bir oluşturur `ChunkingChannelFactory` iç kanal fabrikası geçirme (döndürülen `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), ileti Eylemler ve öbekleri arabelleğe alınacak en fazla sayısını listesi.</span><span class="sxs-lookup"><span data-stu-id="269d5-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="269d5-223">Adlı bir özellikten öbekleri sayısı gelir `MaxBufferedChunks` tarafından kullanıma sunulan `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="269d5-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 `BuildChannelListener<T>` <span data-ttu-id="269d5-224">oluşturmak için benzer bir uygulamaya sahip `ChunkingChannelListener` ve iç kanal dinleyicisi geçirme.</span><span class="sxs-lookup"><span data-stu-id="269d5-224">has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="269d5-225">Bu örnekte adlı bulunan bir örnek bağlaması var. `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="269d5-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="269d5-226">Bu bağlamanın iki bağlama öğelerden oluşur: `TcpTransportBindingElement` ve `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="269d5-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="269d5-227">Gösterme yanı sıra `MaxBufferedChunks` özelliği, bağlama de ayarlar bazı `TcpTransportBindingElement` gibi özellikler `MaxReceivedMessageSize` (ayarlar `ChunkingUtils.ChunkSize` + 100 KB bayt üst bilgileri için).</span><span class="sxs-lookup"><span data-stu-id="269d5-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 `TcpChunkingBinding` <span data-ttu-id="269d5-228">Ayrıca uygulayan `IBindingRuntimePreferences` ve öğesinden true değerini döndürür `ReceiveSynchronously` yalnızca zaman uyumlu alma çağrıları uyguladığını gösteren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="269d5-228">also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="269d5-229">Hangi öbek için iletileri belirleme</span><span class="sxs-lookup"><span data-stu-id="269d5-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="269d5-230">Kümeleme kanal aracılığıyla tanıtılan iletileri chunks `ChunkingBehavior` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="269d5-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="269d5-231">`ChunkingBehavior` Sınıfının Implements `IOperationBehavior` ve çağırarak uygulanan `AddBindingParameter` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="269d5-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="269d5-232">Bu yöntemde, `ChunkingBehavior` değerini inceler, `AppliesTo` özelliği (`InMessage`, `OutMessage` veya her ikisi) hangi iletileri öbekli belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="269d5-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="269d5-233">Ardından eylem her birinin bu iletileri alır (üzerinde iletileri koleksiyondan `OperationDescription`) ve örneği içinde yer alan bir dize koleksiyonu ekler `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="269d5-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="269d5-234">Ardından bu ekler `ChunkingBindingParameter` için sağlanan `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="269d5-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="269d5-235">Bu `BindingParameterCollection` içine geçirilen `BindingContext` bağlamasında, bağlama öğesi kanal fabrikası ya da kanal dinleyicisi oluşturduğunda her bağlama öğesi için.</span><span class="sxs-lookup"><span data-stu-id="269d5-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="269d5-236">`ChunkingBindingElement`'S uygulaması `BuildChannelFactory<T>` ve `BuildChannelListener<T>` bu çekme `ChunkingBindingParameter` tanesi `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="269d5-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="269d5-237">Koleksiyonu içinde bulunan Eylemler `ChunkingBindingParameter` geçirilerek `ChunkingChannelFactory` veya `ChunkingChannelListener`, sırayla Geçiren kendisine `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="269d5-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="269d5-238">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="269d5-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="269d5-239">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="269d5-239">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="269d5-240">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="269d5-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="269d5-241">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="269d5-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="269d5-242">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="269d5-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="269d5-243">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="269d5-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="269d5-244">Service.exe ilk çalıştırma, Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleyin.</span><span class="sxs-lookup"><span data-stu-id="269d5-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="269d5-245">Örnek çalıştırırken aşağıdaki çıktı beklenir.</span><span class="sxs-lookup"><span data-stu-id="269d5-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="269d5-246">İstemci:</span><span class="sxs-lookup"><span data-stu-id="269d5-246">Client:</span></span>  
  
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
  
 <span data-ttu-id="269d5-247">Sunucu:</span><span class="sxs-lookup"><span data-stu-id="269d5-247">Server:</span></span>  
  
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
