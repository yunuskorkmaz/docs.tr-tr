---
title: GoTo Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: d5cdcd214c9679e245645505fe11cb5d521ce085
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351081"
---
# <a name="goto-statement"></a>GoTo Deyimi
Bir yordamda belirtilen satıra koşulsuz olarak dallandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>Bölümüyle  
 `line`  
 Gerekli. Herhangi bir satır etiketi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GoTo` ifadesi yalnızca göründüğü yordamdaki satırlara dallandırır. Çizgi, `GoTo` başvurabileceği bir çizgi etiketine sahip olmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo` deyimleri kodun okunmasını ve bakımını kolaylaştırabilir. Mümkün olduğunda, bunun yerine bir denetim yapısı kullanın. Daha fazla bilgi için bkz. [Denetim akışı](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`veya `Using`...`End Using` yapımı içindeki bir etikete `GoTo` bir ifade kullanamazsınız.  
  
## <a name="branching-and-try-constructions"></a>Dallandırma ve TRY kurulumlarını  
 `Try`...`Catch`...`Finally` oluşturma içinde, aşağıdaki kurallar `GoTo` ifadesiyle dallandırma için geçerlidir.  
  
|Blok veya bölge|Dışarıdan içinde dallanma|İçinden dallanma|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` bloğu|Yalnızca aynı yapı <sup>1</sup> ' in `Catch` bloğundan|Yalnızca tüm oluşturma dışında|  
|`Catch` bloğu|Hiçbir izin verilmiyor|Yalnızca tüm oluşturma veya aynı yapı <sup>1</sup> ' in `Try` bloğunun dışında|  
|`Finally` bloğu|Hiçbir izin verilmiyor|Hiçbir izin verilmiyor|  
  
 <sup>1</sup> bir `Try`...`Catch`...`Finally` oluşturma bir diğeri içinde iç içe geçmişse, bir `Catch` bloğu kendi iç içe düzeyindeki `Try` bloğuna dallandırır, ancak başka bir `Try` bloğunda yer alamaz. İç içe geçmiş bir `Try`...`Catch`...`Finally` oluşturma, iç içe aldığı yapıın `Try` veya `Catch` bloğunda tamamen bulunmalıdır.  
  
 Aşağıdaki çizimde, başka bir `Try` oluşturma bir diğeri içinde gösterilmektedir. İki kurulumlarını blokları arasındaki çeşitli dallar geçerli veya geçersiz olarak belirtilir.  
  
 ![TRY kurulumlarını içinde dallanma grafik Diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yordamdaki çizgi etiketlerine dallandırmak için `GoTo` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case Deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
