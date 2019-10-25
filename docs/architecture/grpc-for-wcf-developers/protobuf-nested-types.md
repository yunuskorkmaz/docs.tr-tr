---
title: Prototipsiz iç içe türler-WCF geliştiricileri için gRPC
description: Prototip ve gRPC 'de iç içe geçmiş ileti türleri hakkında bilgi edinin ve bunların içinde C#nasıl oluşturulduğunu öğrenin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ec9fc522619230c1201bfef1e8128f7356936212
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846312"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="65fd3-103">Protobuf iç içe türleri</span><span class="sxs-lookup"><span data-stu-id="65fd3-103">Protobuf nested types</span></span>

<span data-ttu-id="65fd3-104">Benzer C# şekilde, diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protoarabellek ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="65fd3-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="65fd3-105">Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="65fd3-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="65fd3-106">Oluşturulan C# kodda,`Inner`türü`HelloRequest`sınıfı içindeki iç içe statik`Types`sınıfında bildirilecektir:</span><span class="sxs-lookup"><span data-stu-id="65fd3-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="65fd3-107">[Önceki](protobuf-data-types.md)
>[İleri](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="65fd3-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
