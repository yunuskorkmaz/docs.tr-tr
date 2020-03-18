---
title: Protobuf ayrılmış alanlar - WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: bde658c671e970b7ec841d71d5b4284eb91195f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147951"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="a5d83-103">Protobuf ayrılmış alanları</span><span class="sxs-lookup"><span data-stu-id="a5d83-103">Protobuf reserved fields</span></span>

<span data-ttu-id="a5d83-104">Protokol Arabelleği'ndeki (Protobuf) geriye dönük uyumluluk garantileri, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="a5d83-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="a5d83-105">Hizmetin yeni bir sürümündeki bir iletiden alan kaldırılırsa, bu alan numarası hiçbir zaman yeniden kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5d83-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="a5d83-106">Bunu anahtar kelimeyi `reserved` kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5d83-106">You can enfore this by using the `reserved` keyword.</span></span>

<span data-ttu-id="a5d83-107">Ve `displayName` `marketId` alanları daha önce `Stock` tanımlanan iletiden kaldırıldıysa, alan numaraları aşağıdaki örnekte olduğu gibi rezerve edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5d83-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="a5d83-108">`reserved` Gelecekte eklenebilecek alanlar için yer tutucu olarak da anahtar kelimekullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5d83-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="a5d83-109">Anahtar kelimeyi `to` kullanarak bitişik alan numaralarını aralık olarak ifade edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5d83-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="a5d83-110">[Önceki](protobuf-repeated.md)
>[Sonraki](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="a5d83-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
