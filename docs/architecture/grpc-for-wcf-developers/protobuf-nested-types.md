---
title: Prototipsiz iç içe türler-WCF geliştiricileri için gRPC
description: Prototip ve gRPC 'de iç içe geçmiş ileti türleri hakkında bilgi edinin ve bunların içinde C#nasıl oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967397"
---
# <a name="protobuf-nested-types"></a>Protobuf iç içe türleri

Benzer C# şekilde, diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protoarabellek ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar. Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

Oluşturulan C# kodda, `Inner` türü `HelloRequest` sınıfı içindeki iç içe statik `Types` sınıfında bildirilecektir:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Önceki](protobuf-data-types.md)
>[İleri](protobuf-repeated.md)
