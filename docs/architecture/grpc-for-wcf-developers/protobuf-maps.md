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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="1ebda-103">Sözlükler için prototip haritaları</span><span class="sxs-lookup"><span data-stu-id="1ebda-103">Protobuf maps for dictionaries</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1ebda-104">İletilerde adlandırılmış değerlerin rastgele koleksiyonlarını temsil etmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1ebda-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="1ebda-105">.NET ' te genellikle Sözlük türleri kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="1ebda-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="1ebda-106">Prototip, .net <xref:System.Collections.Generic.IDictionary%602> türünün `map<key_type, value_type>` eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="1ebda-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="1ebda-107">Bu bölümde, prototip `map` içinde nasıl bildirildiği ve üretilen kodun nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ebda-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="1ebda-108">Oluşturulan kodda, `map` alanları da dahil olmak üzere `Google.Protobuf.Collections.MapField<TKey, TValue>` <xref:System.Collections.Generic.IDictionary%602>standart .NET koleksiyonu arabirimlerini uygulayan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ebda-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="1ebda-109">Harita alanları bir ileti tanımında doğrudan yinelenemez, ancak bir harita içeren iç içe geçmiş bir ileti oluşturabilir ve aşağıdaki örnekte olduğu gibi `repeated` ileti türü üzerinde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1ebda-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="1ebda-110">Koddaki MapField özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="1ebda-110">Using MapField properties in code</span></span>

<span data-ttu-id="1ebda-111">Alanlardan oluşturulan özellikler salt okunurdur ve hiçbir şekilde olmayacaktır `null`. `MapField` `map`</span><span class="sxs-lookup"><span data-stu-id="1ebda-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="1ebda-112">Bir Map özelliği ayarlamak için, her türlü `Add(IDictionary<TKey,TValue> values)` .net sözlüğünden değerleri `MapField` kopyalamak üzere Empty özelliğindeki yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ebda-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="1ebda-113">Daha fazla okuma</span><span class="sxs-lookup"><span data-stu-id="1ebda-113">Further reading</span></span>

<span data-ttu-id="1ebda-114">Prototip hakkında daha fazla bilgi için bkz. resmi [prototip belgeleri](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="1ebda-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ebda-115">[Önceki](protobuf-enums.md)
>[İleri](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="1ebda-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
