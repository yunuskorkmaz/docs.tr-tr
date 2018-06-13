---
title: Akış
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 96b77d0135a4dac1dcb8406a1b9a1372d0c4a35d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508221"
---
# <a name="stream"></a><span data-ttu-id="c6cd4-102">Akış</span><span class="sxs-lookup"><span data-stu-id="c6cd4-102">Stream</span></span>
<span data-ttu-id="c6cd4-103">Akış örnek akış aktarım modu iletişimi kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="c6cd4-104">Hizmet akışları gönderip çeşitli işlemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="c6cd4-105">Bu örnek kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-105">This sample is self-hosted.</span></span> <span data-ttu-id="c6cd4-106">Hem istemci hem de hizmet konsol programlardır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6cd4-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c6cd4-108">Windows Communication Foundation (WCF) iki aktarım modlarında iletişim — arabelleğe alınan veya akış.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="c6cd4-109">Bir alıcı okumadan önce varsayılan arabelleğe alınan aktarım modunda bir ileti tamamen teslim edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="c6cd4-110">Akış aktarım modu tamamen teslim edilmeden önce iletiyi işlemek alıcı başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="c6cd4-111">Geçirilen bilgi uzun olduğunda ve seri olarak işlenebilen akış modu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="c6cd4-112">Akış modu de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="c6cd4-113">Akış ve hizmet sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="c6cd4-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="c6cd4-114">Akış bir hizmet sözleşmesini tasarlarken olarak kabul edilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="c6cd4-115">Bir işlem alır veya büyük miktarlarda verinin döndürür, giriş veya çıkış iletilerin ara belleğe alma nedeniyle yüksek bellek kullanımı önlemek için bu veri akış düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="c6cd4-116">Veri akışı için verileri iletisi tek parametre olmalıdır tutan parametresi.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="c6cd4-117">Örneğin, giriş ileti akışını ise, işlemi tam olarak bir giriş parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="c6cd4-118">Benzer şekilde, çıktı ileti akışı, işlemi tam olarak bir çıkış parametresi veya dönüş değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="c6cd4-119">Durum, parametre veya dönüş değeri türü ya da olmalıdır `Stream`, `Message`, veya `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="c6cd4-120">Bu akış örnekte kullanılan hizmet sözleşmesini verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-120">The following is the service contract used in this streaming sample.</span></span>  
  
```  
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
  
 <span data-ttu-id="c6cd4-121">`GetStream` İşlemi arabelleğe alınıp ve döndüren bir dize olarak bazı giriş verileri alan bir `Stream`, akışı.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="c6cd4-122">Buna karşılık, `UploadStream` alır bir `Stream` (akışı) ve döndüren bir `bool` (arabelleğe).</span><span class="sxs-lookup"><span data-stu-id="c6cd4-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="c6cd4-123">`EchoStream` alan ve döndüren `Stream` ve bir işlemin girişi örneğidir ve çıktı iletileri her ikisi de akışı.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="c6cd4-124">Son olarak, `GetReversedStream` hiç giriş alıp döndüren bir `Stream` (akış).</span><span class="sxs-lookup"><span data-stu-id="c6cd4-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="c6cd4-125">Akış aktarımları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="c6cd4-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="c6cd4-126">Daha önce açıklandığı gibi işlem sözleşmeleri tanımlama programlama modeli düzeyinde akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="c6cd4-127">Var. durdurursanız, taşıma hala tüm ileti içeriği arabelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="c6cd4-128">Aktarım akışını etkinleştirmek için taşıma bağlama öğesi üzerindeki bir aktarım modu seçin.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="c6cd4-129">Bağlama öğeye sahip bir `TransferMode` ayarlanabilir özelliği `Buffered`, `Streamed`, `StreamedRequest`, veya `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="c6cd4-130">Aktarım Modu ayarını `Streamed` akış iki yönlü iletişimi etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="c6cd4-131">Aktarım Modu ayarını `StreamedRequest` veya `StreamedResponse` yalnızca istek veya yanıtı iletişiminde sırasıyla Akış etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="c6cd4-132">`basicHttpBinding` Sunan `TransferMode` yaptığı gibi bağlama özellikte `NetTcpBinding` ve `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="c6cd4-133">Diğer aktarımı için aktarım modu ayarlamak için özel bağlama oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="c6cd4-134">Ayar örneği aşağıdaki yapılandırma koddan gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel HTTP bağlama:</span><span class="sxs-lookup"><span data-stu-id="c6cd4-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
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
  
 <span data-ttu-id="c6cd4-135">Ayar yanı sıra `transferMode` için `Streamed`, önceki yapılandırma kod kümeleri `maxReceivedMessageSize` 64 MB.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="c6cd4-136">Bir koruma mekanizması olarak `maxReceivedMessageSize` yerde bir sınır uygulanıyor iletileri izin verilen en büyük boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="c6cd4-137">Varsayılan `maxReceivedMessageSize` genellikle senaryoları akış için çok düşük 64 KB ' tır.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="c6cd4-138">Veri akışı gerçekleştirilir gibi işlem</span><span class="sxs-lookup"><span data-stu-id="c6cd4-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="c6cd4-139">İşlemleri `GetStream`, `UploadStream` ve `EchoStream` tüm işlem doğrudan bir dosyadan veri gönderme veya bir dosyaya doğrudan alınan veri kaydetme.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="c6cd4-140">Bazı durumlarda, yoktur ancak göndermek veya büyük miktarlarda veri almak ve yüklenmekte olan gibi bazı veri öbekleri üzerinde işlem gerçekleştirmek için bir gereksinim gönderilen veya alınan.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="c6cd4-141">Bu tür senaryoların çözmenin bir yolu olan özel bir akış yazmak için (türeyen bir sınıf <xref:System.IO.Stream>) okunabilir veya yazılabilir gibi veri işlemler.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="c6cd4-142">`GetReversedStream` İşlemi ve `ReverseStream` sınıfı bu örneği bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="c6cd4-143">`GetReversedStream` oluşturur ve yeni bir örneğini döndürür `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="c6cd4-144">Sistem, okuduğu gerçek işleme olur `ReverseStream` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="c6cd4-145">`ReverseStream.Read` Uygulama bayt bir öbek temel alınan dosyayı okur, bunları geri alır ve ardından ters bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="c6cd4-146">Bu, tüm dosya içeriği ters; bir kerede bir öbek bayt tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="c6cd4-147">Bu içerik olarak akış işleme nasıl gerçekleştirebilirsiniz göstermek için bir örnektir okuma ya da from ve to akış yazılmış.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="c6cd4-148">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="c6cd4-148">Running the Sample</span></span>  
 <span data-ttu-id="c6cd4-149">Örneği çalıştırmak için önce hem hizmet hem de istemci bu belgenin sonundaki yönergeleri izleyerek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="c6cd4-150">Daha sonra hizmet ve istemci içindeki iki farklı konsol pencerelerinin başlatın.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="c6cd4-151">İstemci başlatıldığında, hizmet hazır olduğunda ENTER tuşuna basın için bekler.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="c6cd4-152">İstemci ardından yöntemlerini çağıran `GetStream()`, `UploadStream()` ve `GetReversedStream()` ilk HTTP üzerinden ve sonra TCP üzerinden.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="c6cd4-153">Aşağıda, istemciden örnek çıktı tarafından takip hizmetinden bir örnek çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c6cd4-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="c6cd4-154">Hizmet çıktı:</span><span class="sxs-lookup"><span data-stu-id="c6cd4-154">Service Output:</span></span>  
  
```  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="c6cd4-155">İstemci çıktı:</span><span class="sxs-lookup"><span data-stu-id="c6cd4-155">Client Output:</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6cd4-156">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c6cd4-156">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6cd4-157">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6cd4-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c6cd4-158">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6cd4-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c6cd4-159">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c6cd4-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6cd4-160">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6cd4-161">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6cd4-162">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-162">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6cd4-163">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6cd4-164">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-164">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a><span data-ttu-id="c6cd4-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-165">See Also</span></span>
