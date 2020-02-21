---
title: Liste ve diziler için yinelenen alanlar-WCF geliştiricileri için gRPC
description: Prototiparabelleği koleksiyonları ve .NET koleksiyonlarıyla ilişkilerini anlayın.
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542965"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="1d106-103">Listeler ve diziler için yinelenen alanlar</span><span class="sxs-lookup"><span data-stu-id="1d106-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="1d106-104">`repeated` önek anahtar sözcüğünü kullanarak protokol arabelleğinde (Protobuffer) listeler belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d106-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="1d106-105">Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1d106-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="1d106-106">Oluşturulan kodda `repeated` alanları, yerleşik .NET koleksiyon türlerinden herhangi biri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel tür tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="1d106-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> 

<span data-ttu-id="1d106-107">`RepeatedField<T>` türü, listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="1d106-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="1d106-108"><xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IEnumerable%601>gibi tüm standart .NET koleksiyonu arabirimlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="1d106-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="1d106-109">Bu nedenle, LINQ sorgularını kullanabilir veya bir diziye ya da listeye kolayca dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d106-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1d106-110">[Önceki](protobuf-nested-types.md)
>[İleri](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="1d106-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
