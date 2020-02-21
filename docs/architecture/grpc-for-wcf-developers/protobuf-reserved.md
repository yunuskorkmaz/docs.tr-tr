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
# <a name="protobuf-reserved-fields"></a>Protobuf ayrılmış alanları

Protokol arabelleğindeki geri uyumluluk garantisi (Protobuffer), her zaman aynı veri öğesini temsil eden alan numaralarına dayanır. Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır. Bunu, `reserved` anahtar sözcüğünü kullanarak gerçekleştirebilirsiniz. 

`displayName` ve `marketId` alanlar daha önce tanımlanan `Stock` iletiden kaldırılmışsa, alan numaralarının aşağıdaki örnekte olduğu gibi ayrılması gerekir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` anahtar sözcüğünü gelecekte eklenebilen alanlar için yer tutucu olarak da kullanabilirsiniz. `to` anahtar sözcüğünü kullanarak bitişik alan numaralarını bir Aralık olarak ifade edebilirsiniz.

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
