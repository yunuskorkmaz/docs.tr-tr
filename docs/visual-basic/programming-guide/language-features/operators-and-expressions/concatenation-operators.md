---
title: Visual Basic'de Birleştirme İşleçleri
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: ab268e513e6f019ed651c94deb5e423cfcca7587
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650624"
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
 [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Visual Basic'de dize düzenleme yöntemlerinin türleri](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
