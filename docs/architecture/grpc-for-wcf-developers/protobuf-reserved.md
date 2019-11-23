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
