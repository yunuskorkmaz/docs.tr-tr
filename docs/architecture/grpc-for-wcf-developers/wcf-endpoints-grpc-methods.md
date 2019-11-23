---
title: WCF son noktaları ve gRPC yöntemleri-WCF geliştiricileri için gRPC
description: ServiceContract ve OperationContract öznitelikleriyle belirtilen WCF uç noktalarının karşılaştırılması ve Protoarabelleğe göre belirtilen gRPC yöntemleri
ms.date: 09/02/2019
ms.openlocfilehash: 763862a363afc6aab72335050cf4822754816c7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966920"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>WCF uç noktaları ve gRPC yöntemleri

WCF 'de, uygulama kodunuzu yazarken aşağıdaki yöntemlerden birini kullanın:

- Uygulama kodunu, OperationContract özniteliğiyle bir sınıfa ve [süsleme](xref:System.ServiceModel.OperationContractAttribute) yöntemlerine yazarsınız.
- Hizmet için bir arabirim bildirir ve arabirime [OperationContract](xref:System.ServiceModel.OperationContractAttribute) öznitelikleri eklersiniz.

Örneğin, `greet.proto` Greeter hizmetinin WCF eşdeğeri aşağıdaki gibi yazılabilir:

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Bölüm 3 ' te, prototip ileti tanımlarının veri sınıfları oluşturmak için kullanıldığını gösterdi. Hizmeti ve yöntem bildirimleri, hizmetini uygulamak için ' den devraldığı temel sınıfları oluşturmak için kullanılır. `.proto` dosyasında uygulanacak yöntemleri bildirmeniz yeterlidir ve derleyici, sanal yöntemlerle geçersiz kılmanız gereken bir temel sınıf oluşturur.

## <a name="operationcontract-properties"></a>OperationContract özellikleri

[OperationContract](xref:System.ServiceModel.OperationContractAttribute) özniteliği, nasıl çalıştığını denetlemek veya iyileştirmek için özelliklere sahiptir. gRPC metotları bu tür bir denetim sunmaz. Aşağıdaki tabloda, bu `OperationContract` özellikleri ve bu özelliklerin, gRPC 'de ' de (veya değil) nasıl ele aldığı gösterilmektedir:

| `OperationContract` özelliği | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | İşlemi tanımlayan URI. gRPC, `.proto` dosyasından `package`, `service` ve `rpc` adını kullanır. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Tüm gRPC hizmet yöntemleri `Task` nesneleri döndürür. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Aşağıdaki nota bakın. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Tek yönlü gRPC yöntemleri `Empty` sonuçları döndürür veya istemci akışını kullanır. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Aşağıdaki nota bakın. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | GRPC 'de anlamı olmayan SOAP ile ilgili. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | İleti şifrelemesi yok; ağ şifrelemesi aktarım katmanında işlendi (HTTP/2 üzerinden TLS). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | GRPC 'de anlamı olmayan SOAP ile ilgili. |

`IsInitiating` özelliği, bir [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) içindeki bir yöntemin bir oturumun parçası olarak çağrılan ilk yöntem olabileceğini belirtmenize olanak tanır. `IsTerminating` özelliği, bir işlem çağrıldıktan sonra sunucunun oturumu kapatmasına neden olur (veya bir geri çağırma istemcisinde kullanılıyorsa istemci). GRPC 'de akışlar tek yöntemlerle oluşturulur ve açıkça kapatılır. Bkz. [GRPC akışı](rpc-types.md#grpc-streaming).

GRPC güvenliği ve şifreleme hakkında daha fazla bilgi için bkz. [Bölüm 6](security.md).

>[!div class="step-by-step"]
>[Önceki](wcf-services-to-grpc-comparison.md)
>[İleri](wcf-bindings.md)
