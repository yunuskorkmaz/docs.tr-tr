---
title: "Visual Basic'de Birleştirme İşleçleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a444cca76fbc41807b0c8b69bcbaedbd75c36eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic'de Birleştirme İşleçleri
Birleştirme işleçleri, tek bir dize halinde birden çok dizenin katılın. İki birleştirme işleçleri vardır `+` ve `&`. Her ikisi de, aşağıdaki örnekte gösterildiği gibi temel birleştirme işlemi gerçekleştiremeyen.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Bu işleçlere de birleştirme `String` aşağıdaki örnekte gösterildiği gibi değişkenleri.  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>İki birleştirme işleçleri arasındaki farklar  
 [+ İşleci](../../../../visual-basic/language-reference/operators/addition-operator.md) iki sayı ekleme birincil amacı vardır. Ancak, bu da dize işlenenleri sayısal işlenen bir arada kullanabilirsiniz. `+` Sahip eklemek, birleştirme, bir derleyici hatası sinyal ya da bir çalışma zamanı throw belirleyen kuralları karmaşık bir dizi <xref:System.InvalidCastException> özel durum.  
  
 [& İşleci](../../../../visual-basic/language-reference/operators/concatenation-operator.md) yalnızca için tanımlanan `String` işlenenler ve her zaman için işlenenleri widens `String`ne olursa olsun, ayarını `Option Strict`. `&` İşleci, dize birleştirme için önerilir, çünkü özel olarak dizeleri için tanımlanır ve istenmeyen bir dönüştürme oluşturma, olasılığını azaltır.  
  
## <a name="performance-string-and-stringbuilder"></a>Performans: Dize ve StringBuilder  
 Çok sayıda birleştirmeler, silme ve değişiklik, gibi bir dizesini işlemeleri yaparsanız performansınızı gelen kar <xref:System.Text.StringBuilder> sınıfını <xref:System.Text> ad alanı. Oluşturma ve başlatma için fazladan bir yönerge sürdüğünü bir <xref:System.Text.StringBuilder> nesnesi ve son değerine dönüştürmek için başka bir yönerge bir `String`, ancak bu kez kurtarmak <xref:System.Text.StringBuilder> daha hızlı gerçekleştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Visual Basic'de dize düzenleme yöntemlerinin türleri](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
