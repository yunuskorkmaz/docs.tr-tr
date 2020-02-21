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
# <a name="protobuf-nested-types"></a><span data-ttu-id="cdc3b-103">Protobuf iç içe türleri</span><span class="sxs-lookup"><span data-stu-id="cdc3b-103">Protobuf nested types</span></span>

<span data-ttu-id="cdc3b-104">Aynı şekilde C# , diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protokol arabelleği (protobuffer), ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc3b-104">Just as C# allows you to declare classes inside other classes, Protocol Buffer (Protobuf) allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="cdc3b-105">Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cdc3b-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="cdc3b-106">Oluşturulan C# kodda, `Inner` türü `HelloRequest` sınıfı içindeki iç içe statik `Types` sınıfında bildirilecektir:</span><span class="sxs-lookup"><span data-stu-id="cdc3b-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="cdc3b-107">[Önceki](protobuf-data-types.md)
>[İleri](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="cdc3b-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
