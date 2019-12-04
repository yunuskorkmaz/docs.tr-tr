---
title: Adres Üstbilgileri
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 3bc8512fb2492a7249c81fc33a3c7b83904f1ccd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715222"
---
# <a name="address-headers"></a>Adres Üstbilgileri

Adres üstbilgileri örneği, istemcilerin Windows Communication Foundation (WCF) kullanarak başvuru parametrelerini bir hizmete nasıl geçirebileceğinizi gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

WS-Addressing belirtimi, belirli bir Web hizmeti uç noktasını ele almanın bir yolu olarak bir uç nokta başvurusunun kavramını tanımlar. WCF 'de, uç nokta başvuruları `EndpointAddress` sınıfı kullanılarak modellenir-`EndpointAddress`, `ServiceEndpoint` sınıfının adres alanının türüdür.

Uç nokta başvuru modelinin bir bölümü, her başvurunun ek tanımlayıcı bilgi ekleyen bazı başvuru parametrelerini taşıyacağından oluşur. WCF 'de, bu başvuru parametreleri `AddressHeader` sınıfının örnekleri olarak modellenir.

Bu örnekte istemci, istemci uç noktasının `EndpointAddress` bir başvuru parametresi ekler. Hizmet bu başvuru parametresini arar ve "Hello" hizmet işleminin mantığındaki değerini kullanır.

## <a name="client"></a>İstemci

İstemcinin başvuru parametresi gönderebilmesi için, `ServiceEndpoint``EndpointAddress` bir `AddressHeader` eklemesi gerekir. `EndpointAddress` sınıfı sabit olduğundan, bir uç nokta adresinin değiştirilmesi `EndpointAddressBuilder` sınıfı kullanılarak yapılmalıdır. Aşağıdaki kod, iletisinin bir parçası olarak bir başvuru parametresi göndermek için istemcisini başlatır.

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

Kod, özgün `EndpointAddress` bir başlangıç değeri olarak kullanarak bir `EndpointAddressBuilder` oluşturur. Daha sonra yeni oluşturulan bir adres üst bilgisi ekler; `CreateAddressHeader` çağrısı, belirli bir ad, ad alanı ve değer içeren bir üst bilgi oluşturur. Burada değer "John" dır. Üst bilgi, oluşturucuya eklendikten sonra, `ToEndpointAddress()` yöntemi (kesilebilir) oluşturucuyu, istemci uç noktasının adres alanına geri atanan (değişmez) bir uç nokta adresine dönüştürür.

İstemci `Console.WriteLine(client.Hello());`çağırdığında, hizmet bu adres parametresinin değerini istemcinin ortaya çıkan çıktısında görüldüğü gibi alabilir.

`Hello, John`

## <a name="server"></a>Sunucusu

`Hello()` hizmet işleminin uygulanması, gelen iletideki üstbilgilerin değerlerini incelemek için geçerli `OperationContext` kullanır.

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

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
