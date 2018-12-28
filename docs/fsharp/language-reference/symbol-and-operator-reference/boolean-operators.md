---
title: Boole İşleçleri
description: Kullanılabilen Boole işleçleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612744"
---
# <a name="boolean-operators"></a>Boole İşleçleri

Bu konuda Boole işleçleri için destek açıklanır F# dili.

## <a name="summary-of-boolean-operators"></a>Boole işleçleri özeti

Kullanılabilen Boole işleçleri aşağıdaki tabloda özetlenmiştir F# dili. Bu işleçler tarafından desteklenen tek türüdür `bool` türü.

|İşleç|Açıklama|
|--------|-----------|
|`not`|Mantıksal olumsuzlama|
|<code>&#124;&#124;</code>|Boole veya|
|`&&`|Boole ve|

Mantıksal AND ve OR işleçlerini gerçekleştirmek *kısa devre değerlendirmesi*, diğer bir deyişle, bunlar, yalnızca genel ifadenin sonucunu belirlemek gerekli olduğunda işlecinin sağ taraftaki ifadeyi değerlendirir. İkinci ifadede `&&` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `true`; ikinci ifadede `||` işleci, yalnızca ilk ifade değerlendirilirse değerlendirilir `false`.

## <a name="see-also"></a>Ayrıca bkz.

- [Bit Düzeyinde İşleçler](bitwise-operators.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Simge ve İşleç Başvurusu](index.md)