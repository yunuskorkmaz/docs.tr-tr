---
title: Continue Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: eb8596c43bf6232eec4bcb844e6202c5de373404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="continue-statement-visual-basic"></a>Continue Deyimi (Visual Basic)
Aktarımları denetimi hemen sonraki yineleme döngüsü.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Alan aktarabilirsiniz içinde bir `Do`, `For`, veya `While` Bu döngü sonraki yinelemeye döngü. Denetim aktarma için eşdeğer olan hemen döngü koşulunu test, geçişleri `For` veya `While` deyimi veya `Do` veya `Loop` içeren ifade `Until` veya `While` yan tümcesi.  
  
 Kullanabileceğiniz `Continue` aktarımları sağlar döngüsünde herhangi bir konumdaki. Denetim aktarımını izin verme kuralları ile aynıdır [GoTo deyimi](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Örneğin, bir döngü içinde tamamen kapsanan ise bir `Try` blok, bir `Catch` bloğu veya bir `Finally` bloğu kullanabilirsiniz `Continue` döngü dışına aktarmak için. Eğer, diğer yandan `Try`... `End Try` yapısı döngü içinde bulunan, kullanamazsınız `Continue` kontrolünü dışarı aktarmak için `Finally` bloğu ve kullanabilirsiniz, dışarı aktarmak için bir `Try` veya `Catch` yalnızca, tamamen dışında aktarırsanız engelle `Try`... `End Try` yapısı.  
  
 Aynı türde iç içe geçmiş döngüler örneğin varsa bir `Do` döngü başka içinde `Do` döngü, bir `Continue Do` deyimi atlar ise en içteki sonraki yinelemeye `Do` içerdiği döngü. Kullanamazsınız `Continue` aynı türde içeren bir döngü sonraki yinelemeye atlanacak.  
  
 Farklı türlerdeki iç içe geçmiş döngüler örneğin varsa bir `Do` içinde döngü bir `For` döngüsü kullanarak ya da döngü sonraki yinelemeye atlayabilirsiniz `Continue Do` veya `Continue For`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Continue While` bölen sıfır ise, bir dizi sonraki sütuna atlamak için deyimi. `Continue While` İçinde bir `For` döngü. İçin aktarır `While col < lastcol` ise en içteki sonraki yinelemesi olduğunu deyimi `While` içeren döngü `For` döngü.  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
