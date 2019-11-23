---
title: Liste ve diziler için yinelenen alanlar-WCF geliştiricileri için gRPC
description: Koleksiyonların prototip tarafından nasıl işlendiğini ve .NET koleksiyonlarıyla ilişkilerini anlayın.
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967359"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="42d3b-103">Listeler ve diziler için yinelenen alanlar</span><span class="sxs-lookup"><span data-stu-id="42d3b-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="42d3b-104">Listeler, `repeated` önek anahtar sözcüğü kullanılarak prototipte belirtilir.</span><span class="sxs-lookup"><span data-stu-id="42d3b-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="42d3b-105">Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="42d3b-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="42d3b-106">Oluşturulan kodda `repeated` alanları, yerleşik .NET koleksiyon türlerinden herhangi biri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel tür tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="42d3b-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="42d3b-107">`RepeatedField<T>` türü, listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="42d3b-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="42d3b-108"><xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IEnumerable%601>gibi tüm standart .NET koleksiyonu arabirimlerini uygular, böylece LINQ sorgularını kullanabilir veya kolayca bir diziye veya listeye dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42d3b-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="42d3b-109">[Önceki](protobuf-nested-types.md)
>[İleri](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="42d3b-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
