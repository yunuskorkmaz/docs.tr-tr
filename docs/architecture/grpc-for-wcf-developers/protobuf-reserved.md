---
title: Prototip için ayrılmış alanlar-WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938526"
---
# <a name="protobuf-reserved-fields"></a>Protobuf ayrılmış alanları

Protokol arabelleğindeki geri uyumluluk garantisi (Protobuffer), her zaman aynı veri öğesini temsil eden alan numaralarına dayanır. Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır. Anahtar sözcüğünü kullanarak bu davranışı uygulayabilirsiniz `reserved` .

`displayName`Ve `marketId` alanları `Stock` daha önce tanımlanan iletiden kaldırılmışsa, alan numaralarının aşağıdaki örnekte olduğu gibi ayrılması gerekir.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved`Bu anahtar sözcüğünü, gelecekte eklenebilen alanlar için bir yer tutucu olarak da kullanabilirsiniz. Anahtar sözcüğünü kullanarak bitişik alan numaralarını bir Aralık olarak ifade edebilirsiniz `to` .

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Önceki](protobuf-repeated.md) 
> [Sonraki](protobuf-any-oneof.md)
