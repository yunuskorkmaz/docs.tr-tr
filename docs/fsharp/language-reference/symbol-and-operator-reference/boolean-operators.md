---
title: Boole İşleçleri (F#)
description: 'F # programlama dilinde kullanılabilen Boole işleçleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272325"
---
# <a name="boolean-operators"></a>Boole İşleçleri

Bu konu, F # dilinde Boole işleçleri desteğini açıklar.

## <a name="summary-of-boolean-operators"></a>Boole işleçleri özeti

F # dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir. Bu işleçler tarafından desteklenen tek türüdür `bool` türü.

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
