---
title: GoTo deyimi (Visual Basic)
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
ms.openlocfilehash: 729ff2a9cbeacaefdf0452a6c5868c229a8d05b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582532"
---
# <a name="goto-statement"></a>GoTo Deyimi
Bir yordam içinde belirtilen bir satıra koşulsuz dallara.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
GoTo line  
```  
  
## <a name="part"></a>Bölümü  
 `line`  
 Gerekli. Herhangi bir satır etiketi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GoTo` Deyimi göründüğü yordamdaki satırlar için dal. Satır etiketi bir satırı olmalıdır `GoTo` başvurabilir. Daha fazla bilgi için [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
> [!NOTE]
>  `GoTo` deyimleri kod okunması ve düzenlenmesi zor hale getirebilir. Mümkün olduğunda, bir denetim yapısı kullanın. Daha fazla bilgi için [akış denetimi](../../../visual-basic/programming-guide/language-features/control-flow/index.md).  
  
 Kullanamazsınız bir `GoTo` daldan dışında deyimi bir `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, veya `Using`... `End Using` içinde bir etikete oluşturma.  
  
## <a name="branching-and-try-constructions"></a>Dallandırma ve yapılarını deneyin  
 İçinde bir `Try`... `Catch`... `Finally` oluşturma, aşağıdaki kurallar geçerli ile dallandırma `GoTo` deyimi.  
  
|Blok veya bölge|Dallanma, gelen dışında|Dallanma çıkış alanından içinde|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` Blok|Yalnızca bir `Catch` aynı yapı bloğunu <sup>1</sup>|Yalnızca tüm yapı dışında|  
|`Catch` Blok|Hiçbir zaman izin verilir|Yalnızca tüm yapı dışında veya çok `Try` aynı yapı bloğunu <sup>1</sup>|  
|`Finally` Blok|Hiçbir zaman izin verilir|Hiçbir zaman izin verilir|  
  
 <sup>1</sup> varsa `Try`... `Catch`... `Finally` yapımı iç içe başka içinde bir `Catch` blok dal içine `Try` blok kendi iç içe geçme düzeyindeki, ancak diğer `Try` blok. İç içe bir `Try`... `Catch`... `Finally` yapım tamamen içinde içerilmeli bir `Try` veya `Catch` içinde bunu iç içe Yapı bloğu.  
  
 Aşağıdaki çizim bir gösterir `Try` yapı içinde başka bir iç içe. Çeşitli dallar arasında iki yapılarını bloklarını, geçerli ya da geçersiz olarak belirtilir.  
  
 ![Deneme yapılarındaki dallanmanın grafik diyagramı](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")  
Try yapılarını geçerli ve geçersiz dalları  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `GoTo` satır etiketleri bir yordamda dala deyimi.  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case Deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With Deyimi](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
