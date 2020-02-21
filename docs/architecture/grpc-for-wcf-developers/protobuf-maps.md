---
title: WCF geliştiricileri için gRPC, sözlüklere yönelik prototip haritaları
description: .NET 'teki sözlük türlerini temsil etmek için prototiplerin nasıl kullanılacağını anlayın.
ms.date: 09/09/2019
ms.openlocfilehash: bf848bbc7e3618f6d78e280fcd85d5eb88d5cfae
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543137"
---
# <a name="protobuf-maps-for-dictionaries"></a>Protobuf sözlük eşlemeleri

İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir. .NET sürümünde bu genellikle Sözlük türleri aracılığıyla işlenir. Protokol arabelleğindeki .NET <xref:System.Collections.Generic.IDictionary%602> türünün (Protobuffer) eşdeğeri `map<key_type, value_type>` türüdür. Bu bölümde, prototipte bir `map` türünün nasıl bildirildiği ve oluşturulan kodun nasıl kullanılacağı gösterilmektedir.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Oluşturulan kodda `map` alanları `Google.Protobuf.Collections.MapField<TKey, TValue>` sınıfını kullanır. Bu sınıf, <xref:System.Collections.Generic.IDictionary%602>dahil olmak üzere standart .NET koleksiyonu arabirimlerini uygular.

Harita alanları bir ileti tanımında doğrudan yinelenemez. Ancak, aşağıdaki örnekte olduğu gibi, bir harita içeren iç içe geçmiş bir ileti oluşturabilir ve ileti türünde `repeated` kullanabilirsiniz:

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

## <a name="further-reading"></a>Daha fazla bilgi

Prototip hakkında daha fazla bilgi için bkz. resmi [prototip belgeleri](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Önceki](protobuf-enums.md)
>[İleri](wcf-services-to-grpc-comparison.md)
