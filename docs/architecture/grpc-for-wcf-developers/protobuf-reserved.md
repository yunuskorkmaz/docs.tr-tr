---
title: Prototip için ayrılmış alanlar-WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d4d40ca12d41ec37e0baebf10de9d0690e4297cc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184178"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="dbb82-103">Protoarabelleğe ayrılan alanlar</span><span class="sxs-lookup"><span data-stu-id="dbb82-103">Protobuf reserved fields</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="dbb82-104">Prototipin geri uyumluluk garantisi, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="dbb82-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="dbb82-105">Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbb82-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="dbb82-106">Bu, `reserved` anahtar sözcüğü kullanılarak zorlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dbb82-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="dbb82-107">`displayName` Ve`marketId`alanlarıdaha önce tanımlanan iletidenkaldırılmışsa,alannumaralarınınaşağıdakiörnekteolduğugibiayrılmasıgerekir.`Stock`</span><span class="sxs-lookup"><span data-stu-id="dbb82-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="dbb82-108">Anahtar `reserved` sözcüğü, gelecekte eklenebilen alanlar için bir yer tutucu olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dbb82-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="dbb82-109">Bitişik alan numaraları `to` anahtar sözcüğünü kullanarak bir Aralık olarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="dbb82-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="dbb82-110">[Önceki](protobuf-repeated.md)
>[İleri](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="dbb82-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
