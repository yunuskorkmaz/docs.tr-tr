---
title: Prototipsiz iç içe türler-WCF geliştiricileri için gRPC
description: Prototip ve gRPC 'de iç içe geçmiş ileti türleri hakkında bilgi edinin ve bunların içinde C#nasıl oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542852"
---
# <a name="protobuf-nested-types"></a>Protobuf iç içe türleri

Aynı şekilde C# , diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protokol arabelleği (protobuffer), ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar. Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:

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
