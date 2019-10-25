---
title: WCF geliştiricileri için gRPC, sözlüklere yönelik prototip haritaları
description: Prototiplerinin göstermek için nasıl kullanılacağını anlayın. NET ' in Sözlük türleri.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: aef6b0f378e7a63f362ec42642cae15b32d49a08
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846331"
---
# <a name="protobuf-maps-for-dictionaries"></a>Protobuf sözlük eşlemeleri

İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir. .NET ' te genellikle Sözlük türleri kullanılarak işlenir. Prototip, .NET <xref:System.Collections.Generic.IDictionary%602> türünün eşdeğeridir `map<key_type, value_type>` türüdür. Bu bölümde, prototipte bir `map` bildirme ve oluşturulan kodun nasıl kullanılacağı gösterilmektedir.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Oluşturulan kodda `map` alanları, <xref:System.Collections.Generic.IDictionary%602>dahil olmak üzere standart .NET koleksiyonu arabirimlerini uygulayan `Google.Protobuf.Collections.MapField<TKey, TValue>` sınıfını kullanır.

Harita alanları bir ileti tanımında doğrudan yinelenemez, ancak bir harita içeren iç içe geçmiş bir ileti oluşturabilir ve aşağıdaki örnekte olduğu gibi ileti türünde `repeated` kullanabilirsiniz:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Koddaki MapField özelliklerini kullanma

`map` alanlarından oluşturulan `MapField` özellikleri salt okunurdur ve hiçbir şekilde `null`olmayacaktır. Bir Map özelliği ayarlamak için, her türlü .NET sözlüğünden değerleri kopyalamak üzere boş `MapField` özelliğindeki `Add(IDictionary<TKey,TValue> values)` yöntemini kullanın.

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
