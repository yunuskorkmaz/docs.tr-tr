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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="7d0ab-103">Protobuf sözlük eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="7d0ab-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="7d0ab-104">İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="7d0ab-105">.NET sürümünde bu genellikle Sözlük türleri aracılığıyla işlenir.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="7d0ab-106">Protokol arabelleğindeki .NET <xref:System.Collections.Generic.IDictionary%602> türünün (Protobuffer) eşdeğeri `map<key_type, value_type>` türüdür.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="7d0ab-107">Bu bölümde, prototipte bir `map` türünün nasıl bildirildiği ve oluşturulan kodun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="7d0ab-108">Oluşturulan kodda `map` alanları `Google.Protobuf.Collections.MapField<TKey, TValue>` sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class.</span></span> <span data-ttu-id="7d0ab-109">Bu sınıf, <xref:System.Collections.Generic.IDictionary%602>dahil olmak üzere standart .NET koleksiyonu arabirimlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-109">This class implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="7d0ab-110">Harita alanları bir ileti tanımında doğrudan yinelenemez.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="7d0ab-111">Ancak, aşağıdaki örnekte olduğu gibi, bir harita içeren iç içe geçmiş bir ileti oluşturabilir ve ileti türünde `repeated` kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d0ab-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="7d0ab-112">Koddaki MapField özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="7d0ab-112">Using MapField properties in code</span></span>

<span data-ttu-id="7d0ab-113">`map` alanlarından oluşturulan `MapField` özellikleri salt okunurdur ve hiçbir şekilde `null`olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="7d0ab-114">Bir Map özelliği ayarlamak için, her türlü .NET sözlüğünden değerleri kopyalamak üzere boş `MapField` özelliğindeki `Add(IDictionary<TKey,TValue> values)` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7d0ab-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="7d0ab-115">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="7d0ab-115">Further reading</span></span>

<span data-ttu-id="7d0ab-116">Prototip hakkında daha fazla bilgi için bkz. resmi [prototip belgeleri](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="7d0ab-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7d0ab-117">[Önceki](protobuf-enums.md)
>[İleri](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="7d0ab-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
