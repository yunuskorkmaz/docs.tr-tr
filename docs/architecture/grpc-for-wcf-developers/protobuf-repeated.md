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
# <a name="repeated-fields-for-lists-and-arrays"></a>Listeler ve diziler için yinelenen alanlar

Önek anahtar sözcüğünü kullanarak protokol arabelleğinde (Protobuffer) listeler belirtirsiniz `repeated` . Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Oluşturulan kodda, alanlar, `repeated` [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] yerleşik .net koleksiyon türlerinden herhangi biri yerine, türün salt yazılır özellikleri tarafından temsil edilir. Bu tür, ve gibi tüm standart .NET koleksiyonu arabirimlerini uygular <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IEnumerable%601> . Bu nedenle, LINQ sorgularını kullanabilir veya bir diziye ya da listeye kolayca dönüştürebilirsiniz.

`RepeatedField<T>`Tür, listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir.

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
>[Önceki](protobuf-nested-types.md) 
> [Sonraki](protobuf-reserved.md)
