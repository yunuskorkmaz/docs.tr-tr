---
title: Continue Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 9ee5fb19db6eafeb7e4bed12935d0b950d6368d6
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005110"
---
# <a name="continue-statement-visual-basic"></a>Continue Deyimi (Visual Basic)
Denetimi bir döngünün sonraki yinelemesine hemen aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0, `For` veya `While` döngüsünün içinden bu döngünün bir sonraki yinelemesine aktarabilirsiniz. Denetim, `For` veya `While` ifadesine veya `Until` veya `While` yan tümcesini içeren @no__t 2 veya `Loop` bildirimine aktarılmaya eşdeğer olan döngü koşulu testine anında geçirilir.  
  
 @No__t-0 ' yı döngüdeki aktarımlara izin veren herhangi bir konumda kullanabilirsiniz. Denetimin aktarılmasına izin veren kurallar [goto ifadesiyle](../../../visual-basic/language-reference/statements/goto-statement.md)aynıdır.  
  
 Örneğin, bir döngü tamamen bir `Try` bloğu, `Catch` bloğu veya `Finally` bloğu içinde yer alıyorsa, döngünün dışına aktarmak için `Continue` ' ü kullanabilirsiniz. Diğer taraftan, `Try`... `End Try` yapısı döngü içinde yer alıyorsa, `Finally` bloğundan denetimi aktarmak için `Continue` ' yi kullanamazsınız ve bunu yalnızca tamamen dışarı aktarırsanız, `Try` veya `Catch` bloğunun dışına aktarmak için kullanabilirsiniz. _T-6... `End Try` yapısı.  
  
 Aynı türde iç içe geçmiş döngülerine sahipseniz, örneğin başka bir `Do` döngüsünde `Do` döngüsü varsa, `Continue Do` bir ifade kendisini içeren en içteki `Do` döngüsünün bir sonraki yinelemesine atlar. Aynı türdeki bir kapsayan döngünün sonraki yinelemesine atlamak için `Continue` kullanamazsınız.  
  
 Farklı türlerde iç içe geçmiş döngülerine sahipseniz (örneğin, bir `For` döngüsünde `Do` döngüsü), `Continue Do` veya `Continue For` ' ü kullanarak iki döngünün bir sonraki yinelemesine atlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir bölen sıfırsa bir dizinin sonraki sütununa atlamak için `Continue While` ifadesini kullanır. @No__t-0 bir `For` döngüsü içinde. @No__t-2 döngüsünü içeren en içteki `While` döngüsünün bir sonraki yinelemesi olan `While col < lastcol` ifadesine aktarır.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
