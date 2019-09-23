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
# <a name="protobuf-reserved-fields"></a>Protoarabelleğe ayrılan alanlar

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Prototipin geri uyumluluk garantisi, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır. Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır. Bu, `reserved` anahtar sözcüğü kullanılarak zorlanabilir. `displayName` Ve`marketId`alanlarıdaha önce tanımlanan iletidenkaldırılmışsa,alannumaralarınınaşağıdakiörnekteolduğugibiayrılmasıgerekir.`Stock`

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Anahtar `reserved` sözcüğü, gelecekte eklenebilen alanlar için bir yer tutucu olarak da kullanılabilir. Bitişik alan numaraları `to` anahtar sözcüğünü kullanarak bir Aralık olarak ifade edilebilir.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Önceki](protobuf-repeated.md)
>[İleri](protobuf-any-oneof.md)
