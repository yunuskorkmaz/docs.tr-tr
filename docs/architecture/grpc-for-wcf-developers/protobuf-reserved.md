---
title: Prototip için ayrılmış alanlar-WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 34697371299bdc5d9a58c0696c1ce7d19816ca87
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846324"
---
# <a name="protobuf-reserved-fields"></a>Protobuf ayrılmış alanları

Prototipin geri uyumluluk garantisi, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır. Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır. Bu, `reserved` anahtar sözcüğü kullanılarak zorlanabilir. `displayName` ve `marketId` alanlar daha önce tanımlanan `Stock` iletiden kaldırılmışsa, alan numaralarının aşağıdaki örnekte olduğu gibi ayrılması gerekir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` anahtar sözcüğü, gelecekte eklenebilen alanlar için yer tutucu olarak da kullanılabilir. Ardışık alan numaraları `to` anahtar sözcüğünü kullanarak bir Aralık olarak ifade edilebilir.

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
