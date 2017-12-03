---
title: "Akış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0cbbae6ae8ba486791c525b70e8d208880661d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="stream"></a>Akış
Akış örnek akış aktarım modu iletişimi kullanımını gösterir. Hizmet akışları gönderip çeşitli işlemleri gösterir. Bu örnek kendiliğinden barındırılır. Hem istemci hem de hizmet konsol programlardır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]iki aktarım modlarında iletişim kurabilir — arabelleğe alınan veya akış. Bir alıcı okumadan önce varsayılan arabelleğe alınan aktarım modunda bir ileti tamamen teslim edilmelidir. Akış aktarım modu tamamen teslim edilmeden önce iletiyi işlemek alıcı başlayabilirsiniz. Geçirilen bilgi uzun olduğunda ve seri olarak işlenebilen akış modu yararlıdır. Akış modu de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.  
  
## <a name="streaming-and-service-contracts"></a>Akış ve hizmet sözleşmeleri  
 Akış bir hizmet sözleşmesini tasarlarken olarak kabul edilmesi için kullanılır. Bir işlem alır veya büyük miktarlarda verinin döndürür, giriş veya çıkış iletilerin ara belleğe alma nedeniyle yüksek bellek kullanımı önlemek için bu veri akış düşünmelisiniz. Veri akışı için verileri iletisi tek parametre olmalıdır tutan parametresi. Örneğin, giriş ileti akışını ise, işlemi tam olarak bir giriş parametresi olmalıdır. Benzer şekilde, çıktı ileti akışı, işlemi tam olarak bir çıkış parametresi veya dönüş değeri olmalıdır. Durum, parametre veya dönüş değeri türü ya da olmalıdır `Stream`, `Message`, veya `IXmlSerializable`. Bu akış örnekte kullanılan hizmet sözleşmesini verilmiştir.  
  
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
  
 `GetStream` İşlemi arabelleğe alınıp ve döndüren bir dize olarak bazı giriş verileri alan bir `Stream`, akışı. Buna karşılık, `UploadStream` alır bir `Stream` (akışı) ve döndüren bir `bool` (arabelleğe). `EchoStream`alan ve döndüren `Stream` ve bir işlemin girişi örneğidir ve çıktı iletileri her ikisi de akışı. Son olarak, `GetReversedStream` hiç giriş alıp döndüren bir `Stream` (akış).  
  
## <a name="enabling-streamed-transfers"></a>Akış aktarımları etkinleştirme  
 Daha önce açıklandığı gibi işlem sözleşmeleri tanımlama programlama modeli düzeyinde akışı sağlar. Var. durdurursanız, taşıma hala tüm ileti içeriği arabelleğe alır. Aktarım akışını etkinleştirmek için taşıma bağlama öğesi üzerindeki bir aktarım modu seçin. Bağlama öğeye sahip bir `TransferMode` ayarlanabilir özelliği `Buffered`, `Streamed`, `StreamedRequest`, veya `StreamedResponse`. Aktarım Modu ayarını `Streamed` akış iki yönlü iletişimi etkinleştirir. Aktarım Modu ayarını `StreamedRequest` veya `StreamedResponse` yalnızca istek veya yanıtı iletişiminde sırasıyla Akış etkinleştirir.  
  
 `basicHttpBinding` Sunan `TransferMode` yaptığı gibi bağlama özellikte `NetTcpBinding` ve `NetNamedPipeBinding`. Diğer aktarımı için aktarım modu ayarlamak için özel bağlama oluşturmanız gerekir.  
  
 Ayar örneği aşağıdaki yapılandırma koddan gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel HTTP bağlama:  
  
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
  
 Ayar yanı sıra `transferMode` için `Streamed`, önceki yapılandırma kod kümeleri `maxReceivedMessageSize` 64 MB. Bir koruma mekanizması olarak `maxReceivedMessageSize` yerde bir sınır uygulanıyor iletileri izin verilen en büyük boyutunu alır. Varsayılan `maxReceivedMessageSize` genellikle senaryoları akış için çok düşük 64 KB ' tır.  
  
## <a name="processing-data-as-it-is-streamed"></a>Veri akışı gerçekleştirilir gibi işlem  
 İşlemleri `GetStream`, `UploadStream` ve `EchoStream` tüm işlem doğrudan bir dosyadan veri gönderme veya bir dosyaya doğrudan alınan veri kaydetme. Bazı durumlarda, yoktur ancak göndermek veya büyük miktarlarda veri almak ve yüklenmekte olan gibi bazı veri öbekleri üzerinde işlem gerçekleştirmek için bir gereksinim gönderilen veya alınan. Bu tür senaryoların çözmenin bir yolu olan özel bir akış yazmak için (türeyen bir sınıf <xref:System.IO.Stream>) okunabilir veya yazılabilir gibi veri işlemler. `GetReversedStream` İşlemi ve `ReverseStream` sınıfı bu örneği bulunur.  
  
 `GetReversedStream`oluşturur ve yeni bir örneğini döndürür `ReverseStream`. Sistem, okuduğu gerçek işleme olur `ReverseStream` nesnesi. `ReverseStream.Read` Uygulama bayt bir öbek temel alınan dosyayı okur, bunları geri alır ve ardından ters bayt döndürür. Bu, tüm dosya içeriği ters; bir kerede bir öbek bayt tersine çevirir. Bu içerik olarak akış işleme nasıl gerçekleştirebilirsiniz göstermek için bir örnektir okuma ya da from ve to akış yazılmış.  
  
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
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
 Örneği çalıştırmak için önce hem hizmet hem de istemci bu belgenin sonundaki yönergeleri izleyerek oluşturun. Daha sonra hizmet ve istemci içindeki iki farklı konsol pencerelerinin başlatın. İstemci başlatıldığında, hizmet hazır olduğunda ENTER tuşuna basın için bekler. İstemci ardından yöntemlerini çağıran `GetStream()`, `UploadStream()` ve `GetReversedStream()` ilk HTTP üzerinden ve sonra TCP üzerinden. Aşağıda, istemciden örnek çıktı tarafından takip hizmetinden bir örnek çıktı verilmiştir:  
  
 Hizmet çıktı:  
  
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
  
 İstemci çıktı:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Ayrıca Bkz.
