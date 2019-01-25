---
title: Akış
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: c16f12e6fb122fbba7dc46abb26859be49c08f74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662601"
---
# <a name="stream"></a>Akış
Stream örnek aktarım modu iletişim akış kullanımını gösterir. Hizmet, akışları gönderip birkaç işlemini kullanıma sunar. Bu örnek kendiliğinden barındırılır. Hem istemci hem de hizmet Konsolu programlardır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Windows Communication Foundation (WCF) iki aktarımı modda iletişim kurabilir; arabelleğe alınan veya akış. Bir alıcı okumadan önce varsayılan arabelleğe alınan aktarım modunda bir ileti tamamen teslim edilmelidir. Akış aktarım modu tamamen teslim edilmeden önce iletiyi işlemek alıcı başlayabilirsiniz. Akış modunda iletilen bilgiler uzun ve seri olarak işlenebilecek yararlı olur. Akış modunda de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.  
  
## <a name="streaming-and-service-contracts"></a>Akış ve hizmet sözleşmeleri  
 Akış, bir hizmet sözleşmesini tasarlarken değerlendirilmesi için kullanılır. Bir işlem alır ya da büyük miktarlarda verinin döndürür, akış giriş veya çıkış iletileri arabelleğe alma nedeniyle yüksek bellek kullanımı önlemek için bu verileri düşünmelisiniz. Akış verileri için veri iletisinde tek parametre olmalıdır tutan parametresi. Örneğin, giriş iletisine akışla birine ise, işlemi tam olarak bir girdi parametreniz olmalıdır. Benzer şekilde, çıktı iletisi akışını ise işlemi tam olarak bir çıkış parametresi ya da dönüş değeri olması gerekir. Tür çalışması, parametre veya dönüş değerindeki olmalıdır `Stream`, `Message`, veya `IXmlSerializable`. Akış Bu örnekte kullanılan hizmet sözleşmesini verilmiştir.  
  
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
  
 `GetStream` İşlemi yürütülmeden ve döndüren bir dize olarak bazı giriş verileri alan bir `Stream`, hangi akış. Buna karşılık, `UploadStream` alır bir `Stream` (akış) ve döndüren bir `bool` (arabelleğe). `EchoStream` alan ve döndüren `Stream` işlem girişi örneğidir ve çıkış iletileri hem de akış. Son olarak, `GetReversedStream` giriş alan ve döndüren bir `Stream` (akış).  
  
## <a name="enabling-streamed-transfers"></a>Akış aktarımları etkinleştirme  
 Daha önce açıklandığı gibi işlem sözleşmeleri tanımlama programlama modeli düzeyinde akış sağlar. Orada durdurursanız, taşıma hala tüm ileti içeriği arabelleğe alır. Aktarım akışını etkinleştirmek için bir aktarım bağlama öğesinin aktarım modunu seçin. Bağlama öğesi olan bir `TransferMode` ayarlanabilir özelliği `Buffered`, `Streamed`, `StreamedRequest`, veya `StreamedResponse`. Aktarım Modu ayarını `Streamed` akış çift yönlü iletişimi sağlar. Aktarım Modu ayarını `StreamedRequest` veya `StreamedResponse` sırasıyla Akış yalnızca istek veya yanıtı iletişimi etkinleştirir.  
  
 `basicHttpBinding` Sunan `TransferMode` gibi bağlama özelliği `NetTcpBinding` ve `NetNamedPipeBinding`. Diğer aktarımı için aktarım modu ayarlamak için özel bir bağlama oluşturmanız gerekir.  
  
 Ayar örneği aşağıdaki yapılandırma koddan gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel bir HTTP bağlaması:  
  
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
  
 Ek olarak `transferMode` için `Streamed`, önceki yapılandırma kod kümesi `maxReceivedMessageSize` 64 MB. Bir koruma mekanizması olarak `maxReceivedMessageSize` yerler iletileri izin verilen en büyük boyutu için üst sınır alırsınız. Varsayılan `maxReceivedMessageSize` genellikle akış senaryoları için düşükse, 64 KB ' tır.  
  
## <a name="processing-data-as-it-is-streamed"></a>Bu akış olarak veri işleme  
 İşlemleri `GetStream`, `UploadStream` ve `EchoStream` tüm baş doğrudan bir dosyadan veri gönderen veya alınan verileri bir dosyaya kaydetme. Bazı durumlarda, yoktur ancak göndermek veya büyük miktarlarda veri almak ve olarak bazı veri öbekleri üzerinde işlem yapmak için bir gereksinim gönderilen veya alınan. Bu tür senaryolara yollarından biri olan özel bir akış yazmak için (türetildiği bir sınıf <xref:System.IO.Stream>) olarak okunabilir veya yazılabilir veri işlemler. `GetReversedStream` İşlemi ve `ReverseStream` sınıfı bunun bir örneği bulunur.  
  
 `GetReversedStream` oluşturur ve yeni bir örneğini döndürür `ReverseStream`. Sistem, okuduğu gerçek işleme olur `ReverseStream` nesne. `ReverseStream.Read` Uygulama bayt öbeğini temel alınan dosyadan okur, bunları tersine çevirir ve sonra ters bayt sayısını döndürür. Bu, tüm dosya içeriğini ters; bir kerede bir bayt bir öbek tersine çevirir. Bir örnek içerik olarak akış işlemede nasıl gerçekleştirebileceğinizi gösterir gelen ve akış yazılamaz veya okunamaz.  
  
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
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örneği çalıştırmak için önce hem hizmet hem de istemci bu belgenin sonundaki yönergeleri izleyerek oluşturun. Daha sonra hizmet ve istemci, iki farklı konsol pencerelerinde başlatın. İstemci başlatıldığında, hizmet hazır olduğunda ENTER tuşuna basın için bekler. İstemci ardından yöntemlerini çağıran `GetStream()`, `UploadStream()` ve `GetReversedStream()` HTTP üzerinden ilk ve daha sonra TCP üzerinden. Örnek çıktı tarafından takip istemciden hizmetinden bir örnek çıktı aşağıdaki gibidir:  
  
 Hizmet çıktısı:  
  
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
  
 İstemci çıktısı:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Ayrıca bkz.
