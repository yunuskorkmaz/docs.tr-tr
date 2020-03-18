---
title: Listeler ve diziler için tekrarlanan alanlar - WCF geliştiricileri için gRPC
description: Protobuf'un koleksiyonları nasıl işleyeceğini ve .NET koleksiyonlarıyla nasıl ilişkili olduklarını anlayın.
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147977"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="56bbc-103">Listeler ve diziler için yinelenen alanlar</span><span class="sxs-lookup"><span data-stu-id="56bbc-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="56bbc-104">Önke anahtar sözcüğü `repeated` kullanarak Protokol Arabelleği'nde (Protobuf) listeleri belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56bbc-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="56bbc-105">Aşağıdaki örnekte, bir liste nasıl oluşturulacak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="56bbc-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="56bbc-106">Oluşturulan kodda, `repeated` alanlar yerleşik .NET koleksiyon türlerinden herhangi biri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel türle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="56bbc-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span>

<span data-ttu-id="56bbc-107">Tür, `RepeatedField<T>` listeyi ikili tel biçimine seri hale getirmek ve deserialize etmek için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="56bbc-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="56bbc-108">Gibi tüm standart .NET toplama arabirimlerini <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IEnumerable%601>uygular.</span><span class="sxs-lookup"><span data-stu-id="56bbc-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="56bbc-109">Böylece LINQ sorgularını kullanabilir veya kolayca bir diziye veya listeye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56bbc-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56bbc-110">[Önceki](protobuf-nested-types.md)
>[Sonraki](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="56bbc-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
