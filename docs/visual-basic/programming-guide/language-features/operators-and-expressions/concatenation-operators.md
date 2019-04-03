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
ms.openlocfilehash: 124f0ca0cd01d7fd218fd89dfb78e70fe8aad9e4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835732"
---
# <a name="concatenation-operators-in-visual-basic"></a>Visual Basic'de Birleştirme İşleçleri
Birleştirme işleçleri, tek bir dize olarak birden çok dizeyi katılın. İki birleştirme işleçleri vardır `+` ve `&`. Her ikisi de, aşağıdaki örnekte gösterildiği gibi temel birleştirme işleminin yürütülmesi.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Bu işleçler de bitiştirebilirsiniz `String` değişkenler, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>İki birleştirme işleçleri arasındaki farklar  
 [+ İşleci](../../../../visual-basic/language-reference/operators/addition-operator.md) iki sayının ekleme birincil amacı vardır. Ancak, sayısal dize işlenenleri işlenenle aynı zamanda bitiştirebilirsiniz. `+` İşleci olan ekleyin, birleştirme, derleyici bir hata sinyali vermek ya da bir çalışma zamanı durum belirleyen kuralları karmaşık bir dizi <xref:System.InvalidCastException> özel durum.  
  
 [& İşleci](../../../../visual-basic/language-reference/operators/concatenation-operator.md) yalnızca tanımlanan `String` işlenen ve her zaman işlenenleri için widens `String`ayarına bakılmaksızın `Option Strict`. `&` İşleci, dize birleştirme için önerilir, çünkü özel olarak dizeleri için tanımlanır ve istenmeyen bir dönüştürme oluşturma olasılığınızı azaltır.  
  
## <a name="performance-string-and-stringbuilder"></a>Performans: Dize ve StringBuilder  
 Çok sayıda değişiklik, birleştirmeler ve silme gibi bir dizesini işlemeleri yaparsanız performansınızı gelen kar <xref:System.Text.StringBuilder> sınıfını <xref:System.Text> ad alanı. Oluşturma ve başlatma için fazladan bir yönerge alır bir <xref:System.Text.StringBuilder> nesnesi ve son değerine dönüştürmek için başka bir yönerge bir `String`, ancak bu kez kurtarma <xref:System.Text.StringBuilder> daha hızlı bir şekilde gerçekleştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visual Basic'de dize düzenleme yöntemlerinin türleri](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
