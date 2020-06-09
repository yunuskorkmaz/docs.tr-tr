---
title: Adres Üstbilgileri
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 133826bbbea62b660bdcdd884ce657528ad30873
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576011"
---
# <a name="address-headers"></a>Adres Üstbilgileri

Adres üstbilgileri örneği, istemcilerin Windows Communication Foundation (WCF) kullanarak başvuru parametrelerini bir hizmete nasıl geçirebileceğinizi gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

WS-Addressing belirtimi, belirli bir Web hizmeti uç noktasını ele almanın bir yolu olarak bir uç nokta başvurusunun kavramını tanımlar. WCF 'de, uç nokta başvuruları sınıfı kullanılarak modellenir, `EndpointAddress` `EndpointAddress` sınıfının adres alanının türüdür `ServiceEndpoint` .

Uç nokta başvuru modelinin bir bölümü, her başvurunun ek tanımlayıcı bilgi ekleyen bazı başvuru parametrelerini taşıyacağından oluşur. WCF 'de, bu başvuru parametreleri sınıfının örnekleri olarak modellenir `AddressHeader` .

Bu örnekte istemci, istemci uç noktasının öğesine bir başvuru parametresi ekler `EndpointAddress` . Hizmet bu başvuru parametresini arar ve "Hello" hizmet işleminin mantığındaki değerini kullanır.

## <a name="client"></a>İstemci

İstemcisinin bir başvuru parametresi gönderebilmesi için, `AddressHeader` öğesinin öğesine öğesine eklemesi gerekir `EndpointAddress` `ServiceEndpoint` . `EndpointAddress`Sınıf sabit olduğundan, bir uç nokta adresinin değiştirilmesi sınıfı kullanılarak yapılmalıdır `EndpointAddressBuilder` . Aşağıdaki kod, iletisinin bir parçası olarak bir başvuru parametresi göndermek için istemcisini başlatır.

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

Kod, başlangıçtaki `EndpointAddressBuilder` değeri olarak bir using `EndpointAddress` değeri oluşturur. Daha sonra yeni oluşturulan bir adres üst bilgisi ekler; çağrısı, `CreateAddressHeader` belirli bir ad, ad alanı ve değer içeren bir üst bilgi oluşturur. Burada değer "John" dır. Üstbilgi, oluşturucuya eklendikten sonra, `ToEndpointAddress()` Yöntemi (kesilebilir) oluşturucuyu, istemci uç noktasının adres alanına geri atanan bir (değişmez) uç nokta adresine dönüştürür.

Artık istemci çağırdığında `Console.WriteLine(client.Hello());` , hizmet bu adres parametresinin değerini istemcinin ortaya çıkan çıktısında görüldüğü gibi alabilir.

`Hello, John`

## <a name="server"></a>Sunucu

Hizmet işleminin uygulanması, `Hello()` `OperationContext` gelen iletideki üst bilgilerin değerlerini incelemek için geçerli öğeyi kullanır.

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

Kod, gelen iletideki tüm üst bilgilerin üzerinde yinelenir ve belirli bir ada sahip başvuru parametreleri olan üst bilgileri arar. Parametre bulunduğunda, parametrenin değerini okur ve bunu "ID" değişkeninde depolar.

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
