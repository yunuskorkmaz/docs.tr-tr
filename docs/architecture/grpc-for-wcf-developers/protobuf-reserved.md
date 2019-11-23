---
title: Prototip için ayrılmış alanlar-WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: e589cd38a712ce014fa2c4d847fbde359d538dd0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967307"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="de33b-103">Protobuf ayrılmış alanları</span><span class="sxs-lookup"><span data-stu-id="de33b-103">Protobuf reserved fields</span></span>

<span data-ttu-id="de33b-104">Prototipin geri uyumluluk garantisi, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="de33b-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="de33b-105">Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="de33b-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="de33b-106">Bu, `reserved` anahtar sözcüğü kullanılarak zorlanabilir.</span><span class="sxs-lookup"><span data-stu-id="de33b-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="de33b-107">`displayName` ve `marketId` alanlar daha önce tanımlanan `Stock` iletiden kaldırılmışsa, alan numaralarının aşağıdaki örnekte olduğu gibi ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="de33b-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="de33b-108">`reserved` anahtar sözcüğü, gelecekte eklenebilen alanlar için yer tutucu olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de33b-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="de33b-109">Ardışık alan numaraları `to` anahtar sözcüğünü kullanarak bir Aralık olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="de33b-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="de33b-110">[Önceki](protobuf-repeated.md)
>[İleri](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="de33b-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
