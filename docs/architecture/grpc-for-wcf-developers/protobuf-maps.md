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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="7a611-103">Protobuf sözlük eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="7a611-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="7a611-104">İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7a611-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="7a611-105">.NET sürümünde bu etkinlik genellikle Sözlük türleri aracılığıyla işlenir.</span><span class="sxs-lookup"><span data-stu-id="7a611-105">In .NET, this activity is commonly handled through dictionary types.</span></span> <span data-ttu-id="7a611-106"><xref:System.Collections.Generic.IDictionary%602>Protokol arabelleğindeki .NET türünün eşdeğeri (Protobuffer) `map<key_type, value_type>` türüdür.</span><span class="sxs-lookup"><span data-stu-id="7a611-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="7a611-107">Bu bölümde `map` , prototipte bir türün nasıl bildirilecektir ve oluşturulan kodun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a611-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="7a611-108">Oluşturulan kodda `map` alanlar, türün salt okuma özellikleriyle temsil edilir [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] .</span><span class="sxs-lookup"><span data-stu-id="7a611-108">In the generated code, `map` fields are represented by read-only properties of the [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span></span> <span data-ttu-id="7a611-109">Bu tür, dahil olmak üzere standart .NET koleksiyonu arabirimlerini uygular <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="7a611-109">This type implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="7a611-110">Harita alanları bir ileti tanımında doğrudan yinelenemez.</span><span class="sxs-lookup"><span data-stu-id="7a611-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="7a611-111">Ancak `repeated` , aşağıdaki örnekte olduğu gibi, eşleme içeren ve ileti türünde kullanılan iç içe geçmiş bir ileti oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7a611-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="7a611-112">Koddaki MapField özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="7a611-112">Using MapField properties in code</span></span>

<span data-ttu-id="7a611-113">`MapField`Alanlardan oluşturulan Özellikler `map` salt okunurdur ve hiçbir şekilde olmayacaktır `null` .</span><span class="sxs-lookup"><span data-stu-id="7a611-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="7a611-114">Bir Map özelliği ayarlamak için, `Add(IDictionary<TKey,TValue> values)` `MapField` her türlü .net sözlüğünden değerleri kopyalamak üzere Empty özelliğindeki yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="7a611-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="7a611-115">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="7a611-115">Further reading</span></span>

<span data-ttu-id="7a611-116">Prototip hakkında daha fazla bilgi için bkz. resmi [prototip belgeleri](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="7a611-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
><span data-ttu-id="7a611-117">[Önceki](protobuf-enums.md) 
> [Sonraki](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="7a611-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
