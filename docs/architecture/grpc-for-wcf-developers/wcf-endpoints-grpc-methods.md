---
title: WCF son noktaları ve gRPC yöntemleri-WCF geliştiricileri için gRPC
description: ServiceContract ve OperationContract öznitelikleriyle belirtilen WCF uç noktalarının karşılaştırılması ve Protoarabelleğe göre belirtilen gRPC yöntemleri
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184066"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>WCF uç noktaları ve gRPC yöntemleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

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

Bölüm 3 ' te, prototip ileti tanımlarının veri sınıfları oluşturmak için kullanıldığını gösterdi. Hizmeti ve yöntem bildirimleri, hizmetini uygulamak için ' den devraldığı temel sınıfları oluşturmak için kullanılır. Yalnızca `.proto` dosyada uygulanacak yöntemleri bildirmeniz ve derleyici, sanal yöntemlerle geçersiz kılmanız gereken bir temel sınıf oluşturur.

## <a name="operationcontract-properties"></a>OperationContract özellikleri

[OperationContract](xref:System.ServiceModel.OperationContractAttribute) özniteliği, nasıl çalıştığını denetlemek veya iyileştirmek için özelliklere sahiptir. gRPC metotları bu tür bir denetim sunmaz. Aşağıdaki tabloda, bu özellikler ve `OperationContract` bu özelliklerin, GRPC 'de ile nasıl ele aldığı (veya değil) olduğu işlevleri ayarlanır:

| `OperationContract`özelliði | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | İşlemi tanımlayan URI. `package`GRPC, `service` dosyanın`.proto` adını ve `rpc` dosyasından kullanır. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Tüm GRPC hizmet yöntemleri nesneleri `Task` döndürür. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Aşağıdaki nota bakın. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Tek yönlü GRPC yöntemleri sonuçları döndürür `Empty` veya istemci akışını kullanır. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Aşağıdaki nota bakın. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | GRPC 'de anlamı olmayan SOAP ile ilgili. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | İleti şifrelemesi yok; ağ şifrelemesi aktarım katmanında işlendi (HTTP/2 üzerinden TLS). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | GRPC 'de anlamı olmayan SOAP ile ilgili. |

Özelliği `IsInitiating` , bir [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) içindeki bir yöntemin bir oturumun parçası olarak çağrılan ilk yöntem olabileceğini belirtmenize olanak tanır. `IsTerminating` Özelliği, bir işlem çağrıldıktan sonra sunucunun oturumu kapatmasına neden olur (veya bir geri çağırma istemcisinde kullanılıyorsa istemci). GRPC 'de akışlar tek yöntemlerle oluşturulur ve açıkça kapatılır. Bkz. [GRPC akışı](rpc-types.md#grpc-streaming).

GRPC güvenliği ve şifreleme hakkında daha fazla bilgi için bkz. [Bölüm 6](security.md).

>[!div class="step-by-step"]
>[Önceki](wcf-services-to-grpc-comparison.md)
>[İleri](wcf-bindings.md)
