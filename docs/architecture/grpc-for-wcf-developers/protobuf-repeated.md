---
title: Liste ve diziler için yinelenen alanlar-WCF geliştiricileri için gRPC
description: Koleksiyonların prototip tarafından nasıl işlendiğini ve .NET koleksiyonlarıyla ilişkilerini anlayın.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184185"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="d417d-103">Listeler ve diziler için yinelenen alanlar</span><span class="sxs-lookup"><span data-stu-id="d417d-103">Repeated fields for lists and arrays</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d417d-104">Listeler, `repeated` ön ek anahtar sözcüğü kullanılarak prototipte belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d417d-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="d417d-105">Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d417d-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="d417d-106">Oluşturulan kodda, `repeated` alanlar yerleşik .net koleksiyon türleri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel tür tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="d417d-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="d417d-107">Tür `RepeatedField<T>` , listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="d417d-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="d417d-108"><xref:System.Collections.Generic.IList%601> Ve<xref:System.Collections.Generic.IEnumerable%601>gibi tüm standart .NET koleksiyonu arabirimlerini uygular, böylece LINQ sorgularını kullanabilir veya kolayca bir diziye veya listeye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d417d-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d417d-109">[Önceki](protobuf-nested-types.md)
>[İleri](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="d417d-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
