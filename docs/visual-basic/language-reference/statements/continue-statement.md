---
title: Continue Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 20140cafb68c7e5518bf3d5fa80e56ca1c1de2c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354119"
---
# <a name="continue-statement-visual-basic"></a>Continue Deyimi (Visual Basic)
Denetimi bir döngünün sonraki yinelemesine hemen aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `Do`, `For`veya `While` döngüsünün içinden bu döngünün bir sonraki yinelemesine aktarabilirsiniz. Denetim, `For` ya da `While` bildirimine aktarmaya veya `Until` ya da `While` yan tümcesini içeren `Do` ya da `Loop` ifadesine doğrudan döngü koşulu testine geçirilir.  
  
 `Continue`, döngüdeki aktarımlara izin veren herhangi bir konumda kullanabilirsiniz. Denetimin aktarılmasına izin veren kurallar [goto ifadesiyle](../../../visual-basic/language-reference/statements/goto-statement.md)aynıdır.  
  
 Örneğin, bir döngü tamamen bir `Try` bloğunda, bir `Catch` bloğunda veya `Finally` bloğunda yer alıyorsa, döngünün dışına aktarmak için `Continue` kullanabilirsiniz. Diğer taraftan, `Try`...`End Try` yapısı döngünün içindeyse, denetimi `Finally` bloğunun dışına aktarmak için `Continue` kullanamazsınız ve bunu yalnızca `Try`... `Catch` yapısından dışarı aktarırsanız `Try`veya`End Try` bloğundan dışarı aktarmak için kullanabilirsiniz.  
  
 Aynı türde iç içe geçmiş döngülerine sahipseniz (örneğin, başka bir `Do` döngüsünde `Do` döngüsünde, bir `Continue Do` bildiri kendisini içeren en içteki `Do` döngüsünün bir sonraki yinelemesine atlar. Aynı türdeki bir kapsayan döngünün sonraki yinelemesine atlamak için `Continue` kullanamazsınız.  
  
 Farklı türlerde iç içe geçmiş döngülerine sahipseniz (örneğin, `For` döngüsünde `Do` döngüsü), `Continue Do` veya `Continue For`kullanarak iki döngünün bir sonraki yinelemesine atlayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir bölen sıfırsa bir dizinin sonraki sütununa atlamak için `Continue While` ifadesini kullanır. `Continue While` bir `For` döngüsü içinde. `For` döngüsünü içeren en içteki `While` döngüsünün bir sonraki yinelemesi olan `While col < lastcol` bildirimine aktarır.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While Deyimi](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
