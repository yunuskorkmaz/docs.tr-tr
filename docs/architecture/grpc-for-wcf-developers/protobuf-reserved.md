---
title: Prototip için ayrılmış alanlar-WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: 50082a1aab2e7707a1839b9d56455124a9e4a6a1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542982"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="124af-103">Protobuf ayrılmış alanları</span><span class="sxs-lookup"><span data-stu-id="124af-103">Protobuf reserved fields</span></span>

<span data-ttu-id="124af-104">Protokol arabelleğindeki geri uyumluluk garantisi (Protobuffer), her zaman aynı veri öğesini temsil eden alan numaralarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="124af-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="124af-105">Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="124af-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="124af-106">Bunu, `reserved` anahtar sözcüğünü kullanarak gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="124af-106">You can enfore this by using the `reserved` keyword.</span></span> 

<span data-ttu-id="124af-107">`displayName` ve `marketId` alanlar daha önce tanımlanan `Stock` iletiden kaldırılmışsa, alan numaralarının aşağıdaki örnekte olduğu gibi ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="124af-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="124af-108">`reserved` anahtar sözcüğünü gelecekte eklenebilen alanlar için yer tutucu olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="124af-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="124af-109">`to` anahtar sözcüğünü kullanarak bitişik alan numaralarını bir Aralık olarak ifade edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="124af-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="124af-110">[Önceki](protobuf-repeated.md)
>[İleri](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="124af-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
