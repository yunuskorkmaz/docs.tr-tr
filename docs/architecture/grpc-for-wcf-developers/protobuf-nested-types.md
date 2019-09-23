---
title: Prototipsiz iç içe türler-WCF geliştiricileri için gRPC
description: Prototip ve gRPC 'de iç içe geçmiş ileti türleri hakkında bilgi edinin ve bunların içinde C#nasıl oluşturulduğunu öğrenin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 39bc52b37cc9e57cfe0ed5a5118c348de5f014d8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184192"
---
# <a name="protobuf-nested-types"></a>Prototipsiz iç içe türler

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Benzer C# şekilde, diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protoarabellek ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar. Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

Oluşturulan C# kodda, `Inner` tür `HelloRequest` sınıf içinde iç içe statik `Types` bir sınıfta bildirilecektir:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Önceki](protobuf-data-types.md)
>[İleri](protobuf-repeated.md)
