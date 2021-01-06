---
title: WCF geliştiricileri için gRPC, sözlüklere yönelik prototip haritaları
description: .NET 'teki sözlük türlerini temsil etmek için prototiplerin nasıl kullanılacağını anlayın.
ms.date: 12/15/2020
ms.openlocfilehash: d38270d4bc320cf1f758080c18843ed1d716b350
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938552"
---
# <a name="protobuf-maps-for-dictionaries"></a>Protobuf sözlük eşlemeleri

İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir. .NET sürümünde bu etkinlik genellikle Sözlük türleri aracılığıyla işlenir. <xref:System.Collections.Generic.IDictionary%602>Protokol arabelleğindeki .NET türünün eşdeğeri (Protobuffer) `map<key_type, value_type>` türüdür. Bu bölümde `map` , prototipte bir türün nasıl bildirilecektir ve oluşturulan kodun nasıl kullanılacağı gösterilmektedir.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Oluşturulan kodda `map` alanlar, türün salt okuma özellikleriyle temsil edilir [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] . Bu tür, dahil olmak üzere standart .NET koleksiyonu arabirimlerini uygular <xref:System.Collections.Generic.IDictionary%602> .

Harita alanları bir ileti tanımında doğrudan yinelenemez. Ancak `repeated` , aşağıdaki örnekte olduğu gibi, eşleme içeren ve ileti türünde kullanılan iç içe geçmiş bir ileti oluşturabilirsiniz:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Koddaki MapField özelliklerini kullanma

`MapField`Alanlardan oluşturulan Özellikler `map` salt okunurdur ve hiçbir şekilde olmayacaktır `null` . Bir Map özelliği ayarlamak için, `Add(IDictionary<TKey,TValue> values)` `MapField` her türlü .net sözlüğünden değerleri kopyalamak üzere Empty özelliğindeki yöntemi kullanın.

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

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
>[Önceki](protobuf-enums.md) 
> [Sonraki](wcf-services-to-grpc-comparison.md)
