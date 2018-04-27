---
title: Veri Türlerinin Etkili Kullanımı (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4cac585cdc3072d595d2446e1937678f9ab03335
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="efficient-use-of-data-types-visual-basic"></a>Veri Türlerinin Etkili Kullanımı (Visual Basic)
Bildirilmemiş değişkenleri ve veri türü bildirilen değişkenlerin atanır `Object` veri türü. Bu, hızlı bir şekilde programları yazmak kolaylaştırır, ancak bunları daha yavaş çalışmasına neden olabilir.  
  
## <a name="strong-typing"></a>Yazarak tanımlayıcı  
 Veri türleri için tüm değişkenleri belirtme olarak bilinir *güçlü yazarak*. Güçlü yazarak kullanarak çeşitli avantajları vardır:  
  
-   Değişkenlerinizi IntelliSense desteği sağlar. Bu kodu yazarken özelliklerini ve diğer üyeleri görmenize olanak sağlar.  
  
-   Tür derleyici denetlemeyi avantajlarından yararlanır. Taşma gibi hatalar nedeniyle çalışma zamanında yük devredebilir deyimleri yakalar. Ayrıca bunları desteklemeyen nesnelerde yöntem çağrıları yakalar.  
  
-   Kodunuzu daha hızlı yürütülmesini sonuçlanır.  
  
## <a name="most-efficient-data-types"></a>En verimli veri türleri  
 Hiçbir zaman kesirler içeren değişkenler için tam sayı veri türleri nonintegral türleri daha büyük/küçük harf verimlidir. Visual Basic'te `Integer` ve `UInteger` en verimli sayısal türler.  
  
 Kesirli sayılar için `Double` en verimli veri türü geçerli platformlarda işlemci çift duyarlıklı kayan nokta işlemleri olmasıdır. Ancak, işlemleriyle `Double` gibi tam sayı türleri gibi ile kadar hızlı değildir `Integer`.  
  
## <a name="specifying-data-type"></a>Veri türünü belirtme  
 Kullanım [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) belirli bir türde bir değişken bildirmek için. Erişim düzeyi kullanarak aynı anda belirtebilirsiniz [ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) içinde as anahtar sözcüğü Aşağıdaki örnek.  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>Karakter dönüştürme  
 `AscW` Ve `ChrW` işlevleri Unicode olarak çalışır. Bunları preference için kullanması gereken `Asc` ve `Chr`, hangi gerekir Çevir içine ve dışına Unicode.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Sayısal Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [IntelliSense Kullanma](/visualstudio/ide/using-intellisense)
