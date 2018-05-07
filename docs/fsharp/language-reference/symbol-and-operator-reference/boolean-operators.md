---
title: Boole İşleçleri (F#)
description: 'F # programlama dili kullanılabilen Boole işleçleri hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="boolean-operators"></a>Boole İşleçleri

Bu konu, F # dilinde Boole işleçleri desteğini açıklar.


## <a name="summary-of-boolean-operators"></a>Boole işleçleri özeti
F # dilinde kullanılabilir Boole işleçleri aşağıdaki tabloda özetlenmiştir. Bu işleçleri tarafından desteklenen tek tür `bool` türü.

|İşleç|Açıklama|
|--------|-----------|
|`not`|Mantıksal olumsuzlaştırma|
|<code>&#124;&#124;</code>|Mantıksal OR|
|`&&`|Boolean ve|

Mantıksal AND ve OR işleçleri gerçekleştirmek *değerlendirmesi*, diğer bir deyişle, bunlar değerlendirmek işlecinin sağ tarafındaki ifade yalnızca ifadenin genel sonucu belirlemek gerekli olduğunda. İkinci bir ifade `&&` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `true`; ikinci bir ifade `||` işleci yalnızca ilk ifade değerlendirilirse değerlendirildiği `false`.

## <a name="see-also"></a>Ayrıca Bkz.
[Bit Düzeyinde İşleçler](bitwise-operators.md)

[Aritmetik İşleçler](arithmetic-operators.md)

[Simge ve İşleç Başvurusu](index.md)
