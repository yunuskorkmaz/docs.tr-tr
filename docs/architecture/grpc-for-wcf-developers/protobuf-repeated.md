---
title: Liste ve diziler için yinelenen alanlar-WCF geliştiricileri için gRPC
description: Prototiparabelleği koleksiyonları ve .NET koleksiyonlarıyla ilişkilerini anlayın.
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867509"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="ec9ee-103">Listeler ve diziler için yinelenen alanlar</span><span class="sxs-lookup"><span data-stu-id="ec9ee-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="ec9ee-104">Önek anahtar sözcüğünü kullanarak protokol arabelleğinde (Protobuffer) listeler belirtirsiniz `repeated` .</span><span class="sxs-lookup"><span data-stu-id="ec9ee-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="ec9ee-105">Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ec9ee-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="ec9ee-106">Oluşturulan kodda, alanlar, `repeated` [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] yerleşik .net koleksiyon türlerinden herhangi biri yerine, türün salt yazılır özellikleri tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-106">In the generated code, `repeated` fields are represented by read-only properties of the [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="ec9ee-107">Bu tür, ve gibi tüm standart .NET koleksiyonu arabirimlerini uygular <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="ec9ee-107">This type implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="ec9ee-108">Bu nedenle, LINQ sorgularını kullanabilir veya bir diziye ya da listeye kolayca dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-108">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

<span data-ttu-id="ec9ee-109">`RepeatedField<T>`Tür, listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="ec9ee-109">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span>

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
><span data-ttu-id="ec9ee-110">[Önceki](protobuf-nested-types.md) 
> [Sonraki](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="ec9ee-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
