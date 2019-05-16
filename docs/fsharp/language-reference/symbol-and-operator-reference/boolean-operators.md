---
title: Boole İşleçleri
description: Kullanılabilen Boole işleçleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: ad4bdd1121389f7e280647dbe0c4d0098ffb17df
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641884"
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
