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
ms.openlocfilehash: 7f446b264dcb5c05ed6ddfba34acbbf66be0e447
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084118"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Veri Türlerinin Etkili Kullanımı (Visual Basic)

Bildirilmemiş değişkenlere ve veri türü olmadan belirtilen değişkenlere veri türü atanmamıştır `Object` . Bu, programları hızlı bir şekilde yazmayı kolaylaştırır, ancak bunların daha yavaş yürütülmesine neden olabilir.

## <a name="strong-typing"></a>Güçlü yazma

 Tüm değişkenlerinizin veri türlerini belirtme, *güçlü yazma*olarak bilinir. Güçlü yazma kullanmanın çeşitli avantajları vardır:

- Değişkenleriniz için IntelliSense desteği sunar. Bu, kodu yazarken özelliklerini ve diğer üyelerini görmenizi sağlar.

- Derleyici türü denetlemesinin avantajlarından yararlanır. Bu catch deyimleri, taşma gibi hatalar nedeniyle çalışma zamanında başarısız olabilir. Ayrıca, bunları desteklemeyen nesneler üzerindeki yöntemlere yapılan çağrıları yakalar.

- Kodunuzun daha hızlı yürütülmesine neden olur.

## <a name="most-efficient-data-types"></a>En verimli veri türleri

 Kesirleri olmayan değişkenler için, integral veri türleri İntegral olmayan türlerden daha etkilidir. Visual Basic, `Integer` ve `UInteger` en verimli sayısal türlerdir.

 Büyük sayılar için `Double` en etkili veri türü, geçerli platformlardaki işlemciler çift duyarlıklı olarak kayan nokta işlemleri gerçekleştirtiğinden. Ancak, ile işlemler, gibi `Double` integral türleriyle kadar hızlı değildir `Integer` .

## <a name="specifying-data-type"></a>Veri türünü belirtme

 Belirli bir türün değişkenini bildirmek için [Dim ifadesini](../../../language-reference/statements/dim-statement.md) kullanın. Aşağıdaki örnekte olduğu gibi [ortak](../../../language-reference/modifiers/public.md), [korumalı](../../../language-reference/modifiers/protected.md), [arkadaş](../../../language-reference/modifiers/friend.md)veya [özel](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak erişim düzeyini eşzamanlı olarak belirtebilirsiniz.

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>Karakter dönüştürme

 `AscW`Ve `ChrW` işlevleri Unicode 'da çalışır. `Asc`Bu uygulamaları, ve ' ı tercih halinde kullanmanız gerekir ve `Chr` Bu, Unicode 'a ve dışına çevirmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Veri türleri](index.md)
- [Sayısal Veri Türleri](numeric-data-types.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
- [IntelliSense kullanma](/visualstudio/ide/using-intellisense)
