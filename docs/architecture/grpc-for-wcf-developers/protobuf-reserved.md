---
title: Protobuf ayrılmış alanlar - WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: f89513c4659a02cbc94e1c659baecb9e750acbdc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111042"
---
# <a name="protobuf-reserved-fields"></a>Protobuf ayrılmış alanları

Protokol Arabelleği'ndeki (Protobuf) geriye dönük uyumluluk garantileri, her zaman aynı veri öğesini temsil eden alan numaralarına dayanır. Hizmetin yeni bir sürümündeki bir iletiden alan kaldırılırsa, bu alan numarası hiçbir zaman yeniden kullanılmamalıdır. Bunu anahtar kelimeyi `reserved` kullanarak uygulayabilirsiniz.

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
