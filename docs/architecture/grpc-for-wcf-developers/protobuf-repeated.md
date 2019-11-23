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
# <a name="repeated-fields-for-lists-and-arrays"></a>Listeler ve diziler için yinelenen alanlar

Listeler, `repeated` önek anahtar sözcüğü kullanılarak prototipte belirtilir. Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Oluşturulan kodda `repeated` alanları, yerleşik .NET koleksiyon türlerinden herhangi biri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel tür tarafından temsil edilir. `RepeatedField<T>` türü, listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir. <xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IEnumerable%601>gibi tüm standart .NET koleksiyonu arabirimlerini uygular, böylece LINQ sorgularını kullanabilir veya kolayca bir diziye veya listeye dönüştürebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-nested-types.md)
>[İleri](protobuf-reserved.md)
