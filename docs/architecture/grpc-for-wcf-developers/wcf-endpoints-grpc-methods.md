---
title: WCF son noktaları ve gRPC yöntemleri-WCF geliştiricileri için gRPC
description: ServiceContract ve OperationContract öznitelikleriyle belirtilen WCF uç noktalarının karşılaştırılması ve Protoarabelleğe göre belirtilen gRPC yöntemleri
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503426"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>WCF uç noktaları ve gRPC yöntemleri

Windows Communication Foundation (WCF) ' de, uygulama kodunuzu yazarken aşağıdaki yöntemlerden birini kullanın:

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

Bölüm 3 ' te, prototip ileti tanımlarının veri sınıfları oluşturmak için kullanıldığını gösterdi. Hizmeti ve yöntem bildirimleri, hizmetini uygulamak için ' den devraldığı temel sınıfları oluşturmak için kullanılır. `.proto` dosyasında uygulanacak yöntemleri bildirmeniz yeterlidir ve derleyici, geçersiz kılmanız gereken sanal yöntemlerle bir temel sınıf oluşturur.

## <a name="operationcontract-properties"></a>OperationContract özellikleri

[OperationContract](xref:System.ServiceModel.OperationContractAttribute) özniteliği, nasıl çalıştığını denetlemek veya iyileştirmek için özelliklere sahiptir. gRPC metotları bu tür bir denetim sunmaz. Aşağıdaki tabloda bu `OperationContract` özellikleri listelenmekte ve bu işlevlerin gRPC 'de nasıl ele aldığı (veya olmadığı) açıklanmaktadır:

| `OperationContract` özelliği | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Bir URI, işlemi tanımlar. gRPC, `.proto` dosyasından `package`, `service`ve `rpc` adını kullanır. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Tüm gRPC hizmet yöntemleri `Task` nesneleri döndürür. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Bu tablodan sonraki paragrafa bakın. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Tek yönlü gRPC yöntemleri `Empty` sonuçları döndürür veya istemci akışını kullanır. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Bu tablodan sonraki paragrafa bakın. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Bu özellik SOAP ile ilgilidir ve gRPC 'de bir anlamı yoktur. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | İleti şifrelemesi yok. Ağ şifreleme, aktarım katmanında (HTTP/2 üzerinden TLS) işlenir. |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Bu özellik SOAP ile ilgilidir ve gRPC 'de bir anlamı yoktur. |

`IsInitiating` özelliği, [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) içindeki bir yöntemin bir oturumun parçası olarak çağrılan ilk yöntem olabileceğini belirtmenize olanak tanır. `IsTerminating` özelliği, bir işlem çağrıldıktan sonra sunucunun oturumu kapatmasına neden olur (veya özellik bir geri çağırma istemcisinde kullanılıyorsa istemci). GRPC 'de akışlar tek yöntemlerle oluşturulur ve açıkça kapatılır. Bkz. [GRPC akışı](rpc-types.md#grpc-streaming).

GRPC güvenliği ve şifreleme hakkında daha fazla bilgi için bkz. [Bölüm 6](security.md).

>[!div class="step-by-step"]
>[Önceki](wcf-services-to-grpc-comparison.md)
>[İleri](wcf-bindings.md)
