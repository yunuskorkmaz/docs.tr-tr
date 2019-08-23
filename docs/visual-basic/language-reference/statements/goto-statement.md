---
title: GoTo ekstresi (Visual Basic)
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
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912458"
---
# <a name="goto-statement"></a>GoTo Deyimi
Bir yordamda belirtilen satıra koşulsuz olarak dallandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Bölümüyle  
 `line`  
 Gerekli. Herhangi bir satır etiketi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GoTo` İfadesi yalnızca, göründüğü yordamdaki satırlara dallandırır. Çizginin, `GoTo` başvurabilen bir çizgi etiketi olmalıdır. Daha fazla bilgi için [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
> `GoTo`deyimler kodun okunmasını ve bakımını kolaylaştırabilir. Mümkün olduğunda, bunun yerine bir denetim yapısı kullanın. Daha fazla bilgi için bkz. [Denetim akışı](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 `For`... Dışında `GoTo` dallandırmak için bir ifade kullanamazsınız `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya`Using`... `End Using` içindeki bir etikete oluşturma.  
  
## <a name="branching-and-try-constructions"></a>Dallandırma ve TRY kurulumlarını  
 Bir `Try`... içinde `Catch`... oluşturma, aşağıdaki kurallar `GoTo` ifadesiyle dallandırma için geçerlidir. `Finally`  
  
|Blok veya bölge|Dışarıdan içinde dallanma|İçinden dallanma|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`engelleyin|Yalnızca aynı yapım <sup>1 bloğundan</sup> `Catch`|Yalnızca tüm oluşturma dışında|  
|`Catch`engelleyin|Hiçbir izin verilmiyor|Yalnızca tüm oluşturma veya `Try` aynı yapı <sup>1</sup> bloğunun dışında|  
|`Finally`engelleyin|Hiçbir izin verilmiyor|Hiçbir izin verilmiyor|  
  
 <sup>1</sup> varsa `Try`... `Catch`... oluşturma diğeri içinde iç içe yerleştirilmiş bir `Catch` `Try` blok, bloğa kendi iç içe geçme düzeyinde dallandırır, ancak başka `Try` bir blok içinde yer alamaz. `Finally` İç içe `Try`geçmiş... `Catch`... oluşturma, içinde iç içe olan bir `Try` veya `Catch` bir blok içinde tamamen bulunmalıdır. `Finally`  
  
 Aşağıdaki çizimde, bir `Try` oluşturma diğeri içinde iç içe gösterilmiştir. İki kurulumlarını blokları arasındaki çeşitli dallar geçerli veya geçersiz olarak belirtilir.  
  
 ![TRY kurulumlarını içinde dallanma grafik Diyagramı](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yordamdaki `GoTo` çizgi etiketlerine dallandırmak için ifadesini kullanır.  
  
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
