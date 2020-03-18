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
# <a name="protobuf-reserved-fields"></a>Protobuf ayrılmış alanları

Protokol Arabelleği'ndeki (Protobuf) geriye dönük uyumluluk garantileri, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır. Hizmetin yeni bir sürümündeki bir iletiden alan kaldırılırsa, bu alan numarası hiçbir zaman yeniden kullanılmamalıdır. Bunu anahtar kelimeyi `reserved` kullanarak yapabilirsiniz.

Ve `displayName` `marketId` alanları daha önce `Stock` tanımlanan iletiden kaldırıldıysa, alan numaraları aşağıdaki örnekte olduğu gibi rezerve edilmelidir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` Gelecekte eklenebilecek alanlar için yer tutucu olarak da anahtar kelimekullanabilirsiniz. Anahtar kelimeyi `to` kullanarak bitişik alan numaralarını aralık olarak ifade edebilirsiniz.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Önceki](protobuf-repeated.md)
>[Sonraki](protobuf-any-oneof.md)
