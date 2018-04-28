---
title: Boole İşleçleri (F#)
description: 'F # programlama dili kullanılabilen Boole işleçleri hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
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
