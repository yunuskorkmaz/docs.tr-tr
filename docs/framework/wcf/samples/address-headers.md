---
title: Adres Üstbilgileri
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: d2e38c674e0a3ea10df2e8363e90f4adf7edc9da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503082"
---
# <a name="address-headers"></a>Adres Üstbilgileri
Adres üstbilgileri örnek istemciler Windows Communication Foundation (WCF) kullanarak bir hizmet için başvuru parametreleri nasıl geçirebilirsiniz gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 WS-Addressing belirtimi bir şekilde belirli bir Web Hizmeti uç noktası adresi için bir uç nokta başvurusu kavramını tanımlar. WCF'de, uç nokta başvuruları kullanılarak modellendiği durumda `EndpointAddress` sınıfı - `EndpointAddress` adres alanının türü `ServiceEndpoint` sınıfı.  
  
 Uç nokta başvuru modelini her başvuru ek tanımlayıcı bilgiler ekleyin bazı başvuru parametreleri devam edebileceğinizden parçasıdır. WCF'de, bu başvuru parametreleri örnekleri olarak modellenir `AddressHeader` sınıfı.  
  
 Bu örnekte, bir başvuru parametresi için bir istemci ekler `EndpointAddress` istemcisi bitiş noktası. Hizmet için bu başvuru parametresi arar ve değeri, "Hello" hizmet işlemi mantığı kullanır.  
  
## <a name="client"></a>İstemci  
 İstemcinin bir başvuru parametresi göndermesini eklemeniz gerekir bir `AddressHeader` için `EndpointAddress` , `ServiceEndpoint`. Çünkü `EndpointAddress` sınıfı sabit, değiştirilmesini bir uç nokta adresi yapılmalıdır kullanarak `EndpointAddressBuilder` sınıfı. Aşağıdaki kod, bir başvuru parametresi kendi iletisinin bir parçası göndermek için istemci başlatır.  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 Kod oluşturur bir `EndpointAddressBuilder` özgün kullanarak `EndpointAddress` olarak başlangıç değeri. Ardından, yeni oluşturulan adres üstbilgisi ekler; çağrı `CreateAddressHeadercreates` belirli ad, ad alanı ve değere sahip bir üstbilgi. Burada "John" değeridir. Oluşturucuya, üst bilgi eklendikten sonra `ToEndpointAddress()` yöntemi (değişebilir) oluşturucu geri istemcisi bitiş noktasının adresini alana atanan geri bir (sabit) uç noktası adresi dönüştürür.  
  
 Artık istemciyi çağırdığında `Console.WriteLine(client.Hello());`, istemcinin elde edilen çıktıda görüldüğü şekilde hizmet bu adresi parametresinin değeri alınamadı.  
  
 `Hello, John`  
  
## <a name="server"></a>Sunucu  
 Hizmet işlemi uygulama `Hello()` geçerli kullanan `OperationContext` gelen ileti üst bilgilere değerlerini incelemek için.  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 Kod, başvuru parametreleri belirli bir ada sahip olan üst aranıyor gelen ileti, tüm üst bilgilere üzerinden yinelenir ve. Parametre bulunduğunda, parametre değerini okur ve "id" değişkeninde depolar.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Ayrıca Bkz.
