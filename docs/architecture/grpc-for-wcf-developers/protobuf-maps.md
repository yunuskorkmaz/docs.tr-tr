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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="c944b-103">Protobuf sözlük eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="c944b-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="c944b-104">İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c944b-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="c944b-105">.NET ' te genellikle Sözlük türleri kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="c944b-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="c944b-106">Prototip, .NET <xref:System.Collections.Generic.IDictionary%602> türünün eşdeğeridir `map<key_type, value_type>` türüdür.</span><span class="sxs-lookup"><span data-stu-id="c944b-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="c944b-107">Bu bölümde, prototipte bir `map` bildirme ve oluşturulan kodun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c944b-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="c944b-108">Oluşturulan kodda `map` alanları, <xref:System.Collections.Generic.IDictionary%602>dahil olmak üzere standart .NET koleksiyonu arabirimlerini uygulayan `Google.Protobuf.Collections.MapField<TKey, TValue>` sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c944b-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="c944b-109">Harita alanları bir ileti tanımında doğrudan yinelenemez, ancak bir harita içeren iç içe geçmiş bir ileti oluşturabilir ve aşağıdaki örnekte olduğu gibi ileti türünde `repeated` kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c944b-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="c944b-110">Koddaki MapField özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="c944b-110">Using MapField properties in code</span></span>

<span data-ttu-id="c944b-111">`map` alanlarından oluşturulan `MapField` özellikleri salt okunurdur ve hiçbir şekilde `null`olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c944b-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="c944b-112">Bir Map özelliği ayarlamak için, her türlü .NET sözlüğünden değerleri kopyalamak üzere boş `MapField` özelliğindeki `Add(IDictionary<TKey,TValue> values)` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c944b-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="c944b-113">Daha fazla okuma</span><span class="sxs-lookup"><span data-stu-id="c944b-113">Further reading</span></span>

<span data-ttu-id="c944b-114">Prototip hakkında daha fazla bilgi için bkz. resmi [prototip belgeleri](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="c944b-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c944b-115">[Önceki](protobuf-enums.md)
>[İleri](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="c944b-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
