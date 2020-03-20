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
# <a name="stream"></a>Akış
Akış örneği, aktarım modu iletişiminin kullanımını gösterir. Hizmet, akış gönderen ve alan çeşitli işlemleri ortaya çıkarır. Bu örnek kendi kendine barındırılır. Hem istemci hem de hizmet konsol programlarıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Windows Communication Foundation (WCF), arabelleğe alan veya akışlı iki aktarım modunda iletişim kurabilir. Varsayılan arabelleğe alınan aktarım modunda, bir iletinin bir alıcının okuyabilmesi için tamamen teslim edilmesi gerekir. Akış aktarım modunda, alıcı iletiyi tamamen teslim edilmeden önce işlemeye başlayabilir. Akış modu, geçirilen bilgiler uzun olduğunda ve seri olarak işlenebilirse yararlıdır. Akış modu, ileti tamamen arabelleğe alınamayacak kadar büyükolduğunda da kullanışlıdır.  
  
## <a name="streaming-and-service-contracts"></a>Akış ve Hizmet Sözleşmeleri  
 Akış, bir hizmet sözleşmesi tasarlarken göz önünde bulundurulması gereken bir şeydir. Bir işlem büyük miktarda veri alıyor veya döndürürse, giriş veya çıktı iletilerinin arabelleğe alınması nedeniyle yüksek bellek kullanımını önlemek için bu verileri akışı düşünmelisiniz. Veri akışı için, bu verileri tutan parametre iletideki tek parametre olmalıdır. Örneğin, giriş iletisi akış için bir işlem varsa, işlem tam olarak bir giriş parametresi olmalıdır. Benzer şekilde, çıktı iletisi akış olacaksa, işlemin tam olarak bir çıkış parametresi veya bir iade değeri olmalıdır. Her iki durumda da, parametre veya `Stream`iade `Message`değeri `IXmlSerializable`türü , , veya . Aşağıda, bu akış örneğinde kullanılan hizmet sözleşmesi ve  
  
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
  
 İşlem, `GetStream` arabelleğe alınan bir dize olarak bazı giriş `Stream`verileri alır ve akışlı bir , döndürür. Tersine, `UploadStream` bir `Stream` (akış) alır ve `bool` bir (arabelleğe alındı) döndürür. `EchoStream`alır ve `Stream` döndürür ve giriş ve çıktı iletileri hem akış lı bir işlem örneğidir. Son `GetReversedStream` olarak, hiçbir giriş `Stream` alır ve bir (akış) döndürür.  
  
## <a name="enabling-streamed-transfers"></a>Akışlı Aktarımları Etkinleştirme  
 Daha önce açıklandığı gibi işlem sözleşmeleri tanımlanması programlama modeli düzeyinde akış sağlar. Burada durursanız, aktarım hala tüm ileti içeriğini arabellekte. Aktarım akışını etkinleştirmek için, aktarım öğesi üzerinde bir aktarım modu seçin. `TransferMode` Bağlama `Buffered`öğesi, , , `Streamed` `StreamedRequest`, veya `StreamedResponse`. Aktarım modunu `Streamed` her iki yönde de iletişim akışı sağlayacak şekilde ayarlama. Aktarım modunu `StreamedRequest` `StreamedResponse` sırasıyla yalnızca istek veya yanıtta akış iletişimine ayarlamak veya etkinleştirmek.  
  
 Bu `basicHttpBinding` özellik, `TransferMode` olduğu `NetTcpBinding` gibi bağlama `NetNamedPipeBinding`özelliğini ortaya çıkarır ve . Diğer aktarımlar için aktarım modunu ayarlamak için özel bir bağlama oluşturmanız gerekir.  
  
 Örnekteki aşağıdaki yapılandırma kodu, `TransferMode` özelliği akışa `basicHttpBinding` ayarlayarak özel bir HTTP bağlamayı gösterir:  
  
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
  
 Ayarı `transferMode` ek olarak `Streamed`, önceki yapılandırma `maxReceivedMessageSize` kodu 64MB ayarlar. Bir savunma mekanizması `maxReceivedMessageSize` olarak, alınan iletilerin izin verilen maksimum boyutuna bir kapak yerleştirir. Varsayılan `maxReceivedMessageSize` 64 KB, genellikle çok düşük akış senaryoları için.  
  
## <a name="processing-data-as-it-is-streamed"></a>Veriler Akış olarak işlenirken  
 İşlemler `GetStream` `UploadStream` ve `EchoStream` tüm işlemler, doğrudan bir dosyadan veri gönderme veya alınan verileri doğrudan bir dosyaya kaydetme ile ilgilenir. Ancak bazı durumlarda, büyük miktarda veri göndermek veya almak ve gönderilirken veya alınırken verilerin yığınları üzerinde bazı işlemler gerçekleştirme zorunluluğu vardır. Bu tür senaryoları ele almanın bir yolu, verileri okunurken <xref:System.IO.Stream>veya yazılırken işleyen özel bir akış (türetilen bir sınıf) yazmaktır. İşlem `GetReversedStream` ve `ReverseStream` sınıf buna bir örnektir.  
  
 `GetReversedStream`yeni bir örnek oluşturur `ReverseStream`ve döndürür. Gerçek işleme, sistem bu `ReverseStream` nesneden okurken gerçekleşir. Uygulama, `ReverseStream.Read` temel dosyadan bayt bir yığın okur, bunları tersine çevirir ve sonra ters bayt döndürür. Bu, tüm dosya içeriğini tersine çevirmez; bir seferde bir bayt parçasını tersine çevirir. Bu, içerik okunurken veya akıştan ve akışa doğru yazılırken akış işlemeyi nasıl gerçekleştirebileceğinizi gösteren bir örnektir.  
  
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
  
## <a name="running-the-sample"></a>Örneği Çalıştırma  
 Örneği çalıştırmak için, önce bu belgenin sonundaki yönergeleri izleyerek hem hizmeti hem de istemciyi oluşturun. Ardından hizmeti ve istemciyi iki farklı konsol penceresinde başlatın. İstemci başlatıldığında, hizmet hazır olduğunda ENTER tuşuna basmanızı bekler. İstemci daha `GetStream()`sonra `UploadStream()` `GetReversedStream()` yöntemleri çağırır ve önce HTTP üzerinden, sonra TCP üzerinden. Aşağıda, istemciden örnek çıktının ardından hizmetten örnek bir çıktı verilmiştir:  
  
 Hizmet Çıktısı:  
  
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
  
 İstemci Çıktısı:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!NOTE]
> Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
