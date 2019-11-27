---
title: Veri Türlerinin Etkili Kullanımı
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 621dec7537e9c993024e271b96ab8706baf89885
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350103"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Veri Türlerinin Etkili Kullanımı (Visual Basic)
Bildirilmemiş değişkenlere ve veri türü olmadan belirtilen değişkenlere `Object` veri türü atanmamıştır. Bu, programları hızlı bir şekilde yazmayı kolaylaştırır, ancak bunların daha yavaş yürütülmesine neden olabilir.

## <a name="strong-typing"></a>Güçlü yazma
 Tüm değişkenlerinizin veri türlerini belirtme, *güçlü yazma*olarak bilinir. Güçlü yazma kullanmanın çeşitli avantajları vardır:

- Değişkenleriniz için IntelliSense desteği sunar. Bu, kodu yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.

- Derleyici türü denetlemesinin avantajlarından yararlanır. Bu catch deyimleri, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olabilir. Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.

- Kodunuzun daha hızlı yürütülmesine neden olur.

## <a name="most-efficient-data-types"></a>En verimli veri türleri
 Kesirleri olmayan değişkenler için, integral veri türleri İntegral olmayan türlerden daha etkilidir. Visual Basic, `Integer` ve `UInteger` en verimli sayısal türlerdir.

 Büyük sayılar için `Double` en etkili veri türüdür, çünkü geçerli platformlardaki işlemciler çift duyarlıklı olarak kayan nokta işlemleri gerçekleştirir. Ancak, `Double` olan işlemler, `Integer`gibi integral türleri kadar hızlı değildir.

## <a name="specifying-data-type"></a>Veri türünü belirtme
 Belirli bir türün değişkenini bildirmek için [Dim ifadesini](../../../../visual-basic/language-reference/statements/dim-statement.md) kullanın. Aşağıdaki örnekte olduğu gibi [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md)veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak erişim düzeyini eşzamanlı olarak belirtebilirsiniz.

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>Karakter dönüştürme
 `AscW` ve `ChrW` işlevleri Unicode 'da çalışır. Bunları `Asc` ve `Chr`için tercih ettiğiniz şekilde kullanmanız gerekir; bu, Unicode 'a ve dışına çevrilip çevrilmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Sayısal Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [IntelliSense Kullanma](/visualstudio/ide/using-intellisense)
