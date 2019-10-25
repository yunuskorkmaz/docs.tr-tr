---
title: Liste ve diziler için yinelenen alanlar-WCF geliştiricileri için gRPC
description: Koleksiyonların prototip tarafından nasıl işlendiğini ve .NET koleksiyonlarıyla ilişkilerini anlayın.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846315"
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
