---
title: WCF geliştiricileri için gRPC, sözlüklere yönelik prototip haritaları
description: Prototiplerinin göstermek için nasıl kullanılacağını anlayın. NET ' in Sözlük türleri.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6a71fb7940145571a94eaf5c8bae9dfc91a30db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184213"
---
# <a name="protobuf-maps-for-dictionaries"></a>Sözlükler için prototip haritaları

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir. .NET ' te genellikle Sözlük türleri kullanılarak işlenir. Prototip, .net <xref:System.Collections.Generic.IDictionary%602> türünün `map<key_type, value_type>` eşdeğeridir. Bu bölümde, prototip `map` içinde nasıl bildirildiği ve üretilen kodun nasıl kullanılacağı gösterilmektedir.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Oluşturulan kodda, `map` alanları da dahil olmak üzere `Google.Protobuf.Collections.MapField<TKey, TValue>` <xref:System.Collections.Generic.IDictionary%602>standart .NET koleksiyonu arabirimlerini uygulayan sınıfını kullanır.

Harita alanları bir ileti tanımında doğrudan yinelenemez, ancak bir harita içeren iç içe geçmiş bir ileti oluşturabilir ve aşağıdaki örnekte olduğu gibi `repeated` ileti türü üzerinde kullanabilirsiniz:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Koddaki MapField özelliklerini kullanma

Alanlardan oluşturulan özellikler salt okunurdur ve hiçbir şekilde olmayacaktır `null`. `MapField` `map` Bir Map özelliği ayarlamak için, her türlü `Add(IDictionary<TKey,TValue> values)` .net sözlüğünden değerleri `MapField` kopyalamak üzere Empty özelliğindeki yöntemi kullanın.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Daha fazla okuma

Prototip hakkında daha fazla bilgi için bkz. resmi [prototip belgeleri](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Önceki](protobuf-enums.md)
>[İleri](wcf-services-to-grpc-comparison.md)
