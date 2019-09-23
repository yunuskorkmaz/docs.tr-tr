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
# <a name="protobuf-nested-types"></a><span data-ttu-id="08b41-103">Prototipsiz iç içe türler</span><span class="sxs-lookup"><span data-stu-id="08b41-103">Protobuf nested types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="08b41-104">Benzer C# şekilde, diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protoarabellek ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="08b41-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="08b41-105">Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="08b41-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="08b41-106">Oluşturulan C# kodda, `Inner` tür `HelloRequest` sınıf içinde iç içe statik `Types` bir sınıfta bildirilecektir:</span><span class="sxs-lookup"><span data-stu-id="08b41-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="08b41-107">[Önceki](protobuf-data-types.md)
>[İleri](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="08b41-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
