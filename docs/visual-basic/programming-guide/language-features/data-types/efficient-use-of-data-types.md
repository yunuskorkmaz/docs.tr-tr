---
title: Veri Türlerinin Etkili Kullanımı (Visual Basic)
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
ms.openlocfilehash: 0b517bca3a9e296eb891e30df91c1d32eb357432
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907224"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Veri Türlerinin Etkili Kullanımı (Visual Basic)
Bildirilmemiş değişkenler ve bir veri türü bildirilen değişkenler atanmış `Object` veri türü. Bu hızlı yazma kolaylaştırır, ancak bunları daha yavaş çalışmasına neden olabilir.  
  
## <a name="strong-typing"></a>Yazarak güçlü  
 Tüm değişkenlerin veri türlerini belirtme olarak bilinir *güçlü yazım, yazım*. Güçlü yazım, yazım kullanarak çeşitli avantajları vardır:  
  
- Bu değişkenleri için IntelliSense desteği sağlar. Bu kod yazarken özelliklerini ve diğer üyeleri görmenizi sağlar.  
  
- Bu derleyici tür denetimi yararlanır. Bu, çalışma zamanında taşma gibi hatalar nedeniyle başarısız olabilir deyimleri yakalar. Ayrıca bunları desteği olmayan nesneler üzerinde yöntemlere yapılan çağrılar yakalar.  
  
- Bu, kodunuzun daha hızlı bir şekilde yürütülmesini sonuçlanır.  
  
## <a name="most-efficient-data-types"></a>En verimli veri türleri  
 Kesir hiçbir zaman içeren değişkenlerini tam sayı veri türleri nonintegral türleri daha büyük/küçük harf etkilidir. Visual Basic'te `Integer` ve `UInteger` en verimli sayısal türleri.  
  
 Kesirli sayılar için `Double` en verimli veri türü, geçerli platformda işlemci çift duyarlıklı kayan nokta işlemleri olmasıdır. Ancak, işlemleriyle `Double` gibi tam sayı türleri gibi ile kısa sürede olmayan `Integer`.  
  
## <a name="specifying-data-type"></a>Veri türünü belirtme  
 Kullanım [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) belirli bir türdeki bir değişken bildirmek için. Kullanarak aynı anda erişim düzeyini belirtebilirsiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) görüldüğü anahtar sözcüğü Aşağıdaki örnek.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Karakter dönüştürme  
 `AscW` Ve `ChrW` işlevler Unicode olarak çalışır. Bunları preference için kullanması gereken `Asc` ve `Chr`, hangi gerekir Çevir içine ve dışına Unicode.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Sayısal Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [IntelliSense Kullanma](/visualstudio/ide/using-intellisense)
