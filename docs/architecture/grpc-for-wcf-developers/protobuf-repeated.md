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
# <a name="repeated-fields-for-lists-and-arrays"></a>Listeler ve diziler için yinelenen alanlar

`repeated` önek anahtar sözcüğünü kullanarak protokol arabelleğinde (Protobuffer) listeler belirtirsiniz. Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Oluşturulan kodda `repeated` alanları, yerleşik .NET koleksiyon türlerinden herhangi biri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel tür tarafından temsil edilir. 

`RepeatedField<T>` türü, listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir. <xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IEnumerable%601>gibi tüm standart .NET koleksiyonu arabirimlerini uygular. Bu nedenle, LINQ sorgularını kullanabilir veya bir diziye ya da listeye kolayca dönüştürebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-nested-types.md)
>[İleri](protobuf-reserved.md)
