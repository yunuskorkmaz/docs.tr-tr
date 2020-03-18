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
# <a name="repeated-fields-for-lists-and-arrays"></a>Listeler ve diziler için yinelenen alanlar

Önke anahtar sözcüğü `repeated` kullanarak Protokol Arabelleği'nde (Protobuf) listeleri belirtirsiniz. Aşağıdaki örnekte, bir liste nasıl oluşturulacak gösterilmektedir:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Oluşturulan kodda, `repeated` alanlar yerleşik .NET koleksiyon türlerinden herhangi biri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel türle temsil edilir.

Tür, `RepeatedField<T>` listeyi ikili tel biçimine seri hale getirmek ve deserialize etmek için gereken kodu içerir. Gibi tüm standart .NET toplama arabirimlerini <xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IEnumerable%601>uygular. Böylece LINQ sorgularını kullanabilir veya kolayca bir diziye veya listeye dönüştürebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-nested-types.md)
>[Sonraki](protobuf-reserved.md)
