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
# <a name="repeated-fields-for-lists-and-arrays"></a>Listeler ve diziler için yinelenen alanlar

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Listeler, `repeated` ön ek anahtar sözcüğü kullanılarak prototipte belirtilir. Aşağıdaki örnek, bir listenin nasıl oluşturulacağını gösterir:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Oluşturulan kodda, `repeated` alanlar yerleşik .net koleksiyon türleri yerine `Google.Protobuf.Collections.RepeatedField<T>` genel tür tarafından temsil edilir. Tür `RepeatedField<T>` , listeyi seri hale getirmek ve ikili tel formatında seri durumdan çıkarmak için gereken kodu içerir. <xref:System.Collections.Generic.IList%601> Ve<xref:System.Collections.Generic.IEnumerable%601>gibi tüm standart .NET koleksiyonu arabirimlerini uygular, böylece LINQ sorgularını kullanabilir veya kolayca bir diziye veya listeye dönüştürebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-nested-types.md)
>[İleri](protobuf-reserved.md)
