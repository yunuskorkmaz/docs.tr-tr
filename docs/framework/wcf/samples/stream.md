---
title: Akış
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f22339ca298f053fa636cc37281276051c70f6d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183325"
---
# <a name="stream"></a><span data-ttu-id="7e559-102">Akış</span><span class="sxs-lookup"><span data-stu-id="7e559-102">Stream</span></span>
<span data-ttu-id="7e559-103">Akış örneği, aktarım modu iletişiminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e559-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="7e559-104">Hizmet, akış gönderen ve alan çeşitli işlemleri ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="7e559-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="7e559-105">Bu örnek kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="7e559-105">This sample is self-hosted.</span></span> <span data-ttu-id="7e559-106">Hem istemci hem de hizmet konsol programlarıdır.</span><span class="sxs-lookup"><span data-stu-id="7e559-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e559-107">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="7e559-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7e559-108">Windows Communication Foundation (WCF), arabelleğe alan veya akışlı iki aktarım modunda iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="7e559-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="7e559-109">Varsayılan arabelleğe alınan aktarım modunda, bir iletinin bir alıcının okuyabilmesi için tamamen teslim edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e559-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="7e559-110">Akış aktarım modunda, alıcı iletiyi tamamen teslim edilmeden önce işlemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7e559-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="7e559-111">Akış modu, geçirilen bilgiler uzun olduğunda ve seri olarak işlenebilirse yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e559-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="7e559-112">Akış modu, ileti tamamen arabelleğe alınamayacak kadar büyükolduğunda da kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e559-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="7e559-113">Akış ve Hizmet Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="7e559-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="7e559-114">Akış, bir hizmet sözleşmesi tasarlarken göz önünde bulundurulması gereken bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="7e559-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="7e559-115">Bir işlem büyük miktarda veri alıyor veya döndürürse, giriş veya çıktı iletilerinin arabelleğe alınması nedeniyle yüksek bellek kullanımını önlemek için bu verileri akışı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7e559-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="7e559-116">Veri akışı için, bu verileri tutan parametre iletideki tek parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e559-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="7e559-117">Örneğin, giriş iletisi akış için bir işlem varsa, işlem tam olarak bir giriş parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e559-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="7e559-118">Benzer şekilde, çıktı iletisi akış olacaksa, işlemin tam olarak bir çıkış parametresi veya bir iade değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e559-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="7e559-119">Her iki durumda da, parametre veya `Stream`iade `Message`değeri `IXmlSerializable`türü , , veya .</span><span class="sxs-lookup"><span data-stu-id="7e559-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="7e559-120">Aşağıda, bu akış örneğinde kullanılan hizmet sözleşmesi ve</span><span class="sxs-lookup"><span data-stu-id="7e559-120">The following is the service contract used in this streaming sample.</span></span>  
  
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
  
 <span data-ttu-id="7e559-121">İşlem, `GetStream` arabelleğe alınan bir dize olarak bazı giriş `Stream`verileri alır ve akışlı bir , döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e559-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="7e559-122">Tersine, `UploadStream` bir `Stream` (akış) alır ve `bool` bir (arabelleğe alındı) döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e559-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="7e559-123">`EchoStream`alır ve `Stream` döndürür ve giriş ve çıktı iletileri hem akış lı bir işlem örneğidir.</span><span class="sxs-lookup"><span data-stu-id="7e559-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="7e559-124">Son `GetReversedStream` olarak, hiçbir giriş `Stream` alır ve bir (akış) döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e559-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="7e559-125">Akışlı Aktarımları Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7e559-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="7e559-126">Daha önce açıklandığı gibi işlem sözleşmeleri tanımlanması programlama modeli düzeyinde akış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e559-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="7e559-127">Burada durursanız, aktarım hala tüm ileti içeriğini arabellekte.</span><span class="sxs-lookup"><span data-stu-id="7e559-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="7e559-128">Aktarım akışını etkinleştirmek için, aktarım öğesi üzerinde bir aktarım modu seçin.</span><span class="sxs-lookup"><span data-stu-id="7e559-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="7e559-129">`TransferMode` Bağlama `Buffered`öğesi, , , `Streamed` `StreamedRequest`, veya `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="7e559-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="7e559-130">Aktarım modunu `Streamed` her iki yönde de iletişim akışı sağlayacak şekilde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="7e559-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="7e559-131">Aktarım modunu `StreamedRequest` `StreamedResponse` sırasıyla yalnızca istek veya yanıtta akış iletişimine ayarlamak veya etkinleştirmek.</span><span class="sxs-lookup"><span data-stu-id="7e559-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="7e559-132">Bu `basicHttpBinding` özellik, `TransferMode` olduğu `NetTcpBinding` gibi bağlama `NetNamedPipeBinding`özelliğini ortaya çıkarır ve .</span><span class="sxs-lookup"><span data-stu-id="7e559-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="7e559-133">Diğer aktarımlar için aktarım modunu ayarlamak için özel bir bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e559-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="7e559-134">Örnekteki aşağıdaki yapılandırma kodu, `TransferMode` özelliği akışa `basicHttpBinding` ayarlayarak özel bir HTTP bağlamayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="7e559-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="7e559-135">Ayarı `transferMode` ek olarak `Streamed`, önceki yapılandırma `maxReceivedMessageSize` kodu 64MB ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7e559-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="7e559-136">Bir savunma mekanizması `maxReceivedMessageSize` olarak, alınan iletilerin izin verilen maksimum boyutuna bir kapak yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="7e559-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="7e559-137">Varsayılan `maxReceivedMessageSize` 64 KB, genellikle çok düşük akış senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="7e559-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="7e559-138">Veriler Akış olarak işlenirken</span><span class="sxs-lookup"><span data-stu-id="7e559-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="7e559-139">İşlemler `GetStream` `UploadStream` ve `EchoStream` tüm işlemler, doğrudan bir dosyadan veri gönderme veya alınan verileri doğrudan bir dosyaya kaydetme ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="7e559-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="7e559-140">Ancak bazı durumlarda, büyük miktarda veri göndermek veya almak ve gönderilirken veya alınırken verilerin yığınları üzerinde bazı işlemler gerçekleştirme zorunluluğu vardır.</span><span class="sxs-lookup"><span data-stu-id="7e559-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="7e559-141">Bu tür senaryoları ele almanın bir yolu, verileri okunurken <xref:System.IO.Stream>veya yazılırken işleyen özel bir akış (türetilen bir sınıf) yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="7e559-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="7e559-142">İşlem `GetReversedStream` ve `ReverseStream` sınıf buna bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="7e559-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="7e559-143">`GetReversedStream`yeni bir örnek oluşturur `ReverseStream`ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e559-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="7e559-144">Gerçek işleme, sistem bu `ReverseStream` nesneden okurken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7e559-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="7e559-145">Uygulama, `ReverseStream.Read` temel dosyadan bayt bir yığın okur, bunları tersine çevirir ve sonra ters bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="7e559-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="7e559-146">Bu, tüm dosya içeriğini tersine çevirmez; bir seferde bir bayt parçasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="7e559-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="7e559-147">Bu, içerik okunurken veya akıştan ve akışa doğru yazılırken akış işlemeyi nasıl gerçekleştirebileceğinizi gösteren bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="7e559-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="7e559-148">Örneği Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7e559-148">Running the Sample</span></span>  
 <span data-ttu-id="7e559-149">Örneği çalıştırmak için, önce bu belgenin sonundaki yönergeleri izleyerek hem hizmeti hem de istemciyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e559-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="7e559-150">Ardından hizmeti ve istemciyi iki farklı konsol penceresinde başlatın.</span><span class="sxs-lookup"><span data-stu-id="7e559-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="7e559-151">İstemci başlatıldığında, hizmet hazır olduğunda ENTER tuşuna basmanızı bekler.</span><span class="sxs-lookup"><span data-stu-id="7e559-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="7e559-152">İstemci daha `GetStream()`sonra `UploadStream()` `GetReversedStream()` yöntemleri çağırır ve önce HTTP üzerinden, sonra TCP üzerinden.</span><span class="sxs-lookup"><span data-stu-id="7e559-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="7e559-153">Aşağıda, istemciden örnek çıktının ardından hizmetten örnek bir çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7e559-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="7e559-154">Hizmet Çıktısı:</span><span class="sxs-lookup"><span data-stu-id="7e559-154">Service Output:</span></span>  
  
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
  
 <span data-ttu-id="7e559-155">İstemci Çıktısı:</span><span class="sxs-lookup"><span data-stu-id="7e559-155">Client Output:</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e559-156">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7e559-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7e559-157">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="7e559-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7e559-158">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7e559-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7e559-159">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7e559-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e559-160">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7e559-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7e559-161">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e559-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e559-162">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7e559-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7e559-163">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="7e559-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e559-164">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="7e559-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
