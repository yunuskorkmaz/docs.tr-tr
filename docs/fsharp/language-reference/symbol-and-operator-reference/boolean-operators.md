---
title: "Boole İşleçleri (F#)"
description: "F # programlama dili kullanılabilen Boole işleçleri hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[Bit düzeyinde işleçler](bitwise-operators.md)

[Aritmetik işleçler](arithmetic-operators.md)

[Simge ve işleç başvurusu](index.md)
