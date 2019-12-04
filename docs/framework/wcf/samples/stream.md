---
title: Akış
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: d4166ac0258001b3e4eb0b8ece0f5163863359a4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716654"
---
# <a name="stream"></a><span data-ttu-id="a785a-102">Akış</span><span class="sxs-lookup"><span data-stu-id="a785a-102">Stream</span></span>
<span data-ttu-id="a785a-103">Akış örneği, akış aktarım modu iletişiminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a785a-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="a785a-104">Hizmet, akışları gönderen ve alan birkaç işlem sunar.</span><span class="sxs-lookup"><span data-stu-id="a785a-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="a785a-105">Bu örnek kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="a785a-105">This sample is self-hosted.</span></span> <span data-ttu-id="a785a-106">Hem istemci hem de hizmet konsol programlarıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a785a-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a785a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a785a-108">Windows Communication Foundation (WCF), iki Aktarım modunda (ara belleğe alınmış veya akış) iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="a785a-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="a785a-109">Varsayılan arabellekli Aktarım modunda, bir alıcının okuyabilmesi için bir iletinin tamamen teslim edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a785a-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="a785a-110">Akış Aktarım modunda, alıcı tamamen teslim edilmeden önce iletiyi işlemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a785a-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="a785a-111">Aktarım modu, iletilen bilgiler uzun olduğunda ve hizmet dışı olarak işlenebilmesi durumunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="a785a-112">İleti tamamen arabelleğe alınamayacak kadar büyük olduğunda akış modu da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="a785a-113">Akış ve hizmet sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="a785a-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="a785a-114">Akış, bir hizmet sözleşmesi tasarlarken göz önünde bulundurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="a785a-115">Bir işlem büyük miktarlarda veri alırsa veya döndürürse, giriş veya çıkış iletilerinin arabelleğe alınması nedeniyle yüksek bellek kullanımının oluşmaması için bu verileri akışını göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a785a-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="a785a-116">Veri akışı için, bu verileri tutan parametre iletideki tek parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="a785a-117">Örneğin, giriş iletisi akışla bir giriş ise, işlemin tam olarak bir giriş parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="a785a-118">Benzer şekilde, çıkış iletisi akışı ise, işlemin tam olarak bir çıkış parametresi veya dönüş değeri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a785a-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="a785a-119">Her iki durumda da parametre ya da dönüş değeri türü `Stream`, `Message`veya `IXmlSerializable`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a785a-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="a785a-120">Bu akış örneğinde kullanılan hizmet sözleşmesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a785a-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="a785a-121">`GetStream` işlemi, arabelleğe alınmış bir dize olarak bazı giriş verilerini alır ve akış olan bir `Stream`döndürür.</span><span class="sxs-lookup"><span data-stu-id="a785a-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="a785a-122">Buna karşılık `UploadStream`, bir `Stream` (akışlı) alır ve bir `bool` (arabelleğe alınmış) döndürür.</span><span class="sxs-lookup"><span data-stu-id="a785a-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="a785a-123">`EchoStream` alır ve `Stream` döndürür ve giriş ve çıkış iletilerinin her ikisi de akışındaki bir işlem örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a785a-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="a785a-124">Son olarak, `GetReversedStream` giriş gerçekleşmez ve bir `Stream` (akışlı) döndürmez.</span><span class="sxs-lookup"><span data-stu-id="a785a-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="a785a-125">Akışlı aktarımları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a785a-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="a785a-126">Daha önce açıklandığı gibi, işlem sözleşmelerini tanımlama, programlama modeli düzeyinde akış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a785a-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="a785a-127">Bunu durdurursanız, aktarım, tüm ileti içeriğini arabelleğe almaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="a785a-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="a785a-128">Aktarım akışını etkinleştirmek için, taşımanın bağlama öğesinde bir aktarım modu seçin.</span><span class="sxs-lookup"><span data-stu-id="a785a-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="a785a-129">Binding öğesi `Buffered`, `Streamed`, `StreamedRequest`veya `StreamedResponse`olarak ayarlanabilir bir `TransferMode` özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a785a-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="a785a-130">Aktarım modunun `Streamed` olarak ayarlanması her iki yönde de akış iletişimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a785a-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="a785a-131">Aktarım modunun `StreamedRequest` veya `StreamedResponse` olarak ayarlanması, sırasıyla yalnızca istekte veya yanıtta akış iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a785a-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="a785a-132">`basicHttpBinding` bağlamada `TransferMode` özelliğini `NetTcpBinding` ve `NetNamedPipeBinding`olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a785a-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="a785a-133">Diğer aktarımlar için, aktarım modunu ayarlamak üzere özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a785a-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="a785a-134">Örnekteki aşağıdaki yapılandırma kodu, `TransferMode` özelliğini `basicHttpBinding` ve özel bir HTTP bağlamasındaki akışa ayarlamayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="a785a-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="a785a-135">`transferMode`, `Streamed`olarak ayarlamaya ek olarak, önceki yapılandırma kodu, `maxReceivedMessageSize` 64MB olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a785a-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="a785a-136">Bir savunma mekanizması olarak `maxReceivedMessageSize`, alım sırasında izin verilen en fazla ileti boyutuna bir üst sınır koyar.</span><span class="sxs-lookup"><span data-stu-id="a785a-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="a785a-137">Varsayılan `maxReceivedMessageSize`, genellikle akış senaryolarında çok düşük olan 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="a785a-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="a785a-138">Akış sırasında verileri işleme</span><span class="sxs-lookup"><span data-stu-id="a785a-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="a785a-139">İşlemler `GetStream`, `UploadStream` ve `EchoStream` tüm verileri doğrudan bir dosyadan göndermeye veya alınan verileri doğrudan bir dosyaya kaydetmeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a785a-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="a785a-140">Ancak bazı durumlarda, büyük miktarlarda veri gönderilmesi veya alınması ve verilerin gönderildiği veya alındığı şekilde öbeklerinde bazı işlemler gerçekleştirme gereksinimi vardır.</span><span class="sxs-lookup"><span data-stu-id="a785a-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="a785a-141">Bu tür senaryoları ele almanın bir yolu, okunan veya yazıldığı gibi verileri işleyen özel bir akış (<xref:System.IO.Stream>türetilen bir sınıf) yazmak.</span><span class="sxs-lookup"><span data-stu-id="a785a-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="a785a-142">`GetReversedStream` işlemi ve `ReverseStream` sınıfı buna bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a785a-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="a785a-143">`GetReversedStream`, `ReverseStream`yeni bir örneğini oluşturur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="a785a-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="a785a-144">Gerçek işleme, sistem bu `ReverseStream` nesnesinden okurken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a785a-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="a785a-145">`ReverseStream.Read` uygulama, temel alınan dosyadaki bir bayt öbeğini okur, bu dosyaları ters çevirir ve ters bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="a785a-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="a785a-146">Bu, tüm dosya içeriğini tersine döndürmez; tek seferde bir bayt öbeğini tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="a785a-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="a785a-147">Bu, içerik okunmakta veya akışa yazılırken akış işlemeyi nasıl gerçekleştirebileceğini gösteren bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a785a-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="a785a-148">Örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a785a-148">Running the Sample</span></span>  
 <span data-ttu-id="a785a-149">Örneği çalıştırmak için, önce bu belgenin sonundaki yönergeleri izleyerek hem hizmeti hem de istemciyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="a785a-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="a785a-150">Ardından hizmeti ve istemciyi iki farklı konsol penceresinde başlatın.</span><span class="sxs-lookup"><span data-stu-id="a785a-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="a785a-151">İstemci başladığında, hizmet hazırlanıyor, ENTER tuşuna basmanız bekler.</span><span class="sxs-lookup"><span data-stu-id="a785a-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="a785a-152">İstemci daha sonra HTTP üzerinden ve ardından TCP üzerinden `GetStream()`, `UploadStream()` ve `GetReversedStream()` yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="a785a-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="a785a-153">Aşağıda, istemciden gelen örnek çıktıyı izleyen bir örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a785a-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="a785a-154">Hizmet çıkışı:</span><span class="sxs-lookup"><span data-stu-id="a785a-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="a785a-155">İstemci çıkışı:</span><span class="sxs-lookup"><span data-stu-id="a785a-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------   
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a785a-156">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a785a-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a785a-157">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a785a-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a785a-158">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a785a-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a785a-159">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a785a-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a785a-160">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil. exe ' yi kullanırsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a785a-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a785a-161">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a785a-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a785a-162">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a785a-162">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a785a-163">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a785a-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a785a-164">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a785a-164">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
