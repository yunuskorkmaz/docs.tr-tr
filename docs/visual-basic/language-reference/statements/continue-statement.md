---
title: Continue Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382100"
---
# <a name="continue-statement-visual-basic"></a>Continue Deyimi (Visual Basic)
Denetimi bir döngünün sonraki yinelemesine hemen aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `Do` , `For` veya `While` döngüsünün içinden bu döngünün bir sonraki yinelemesine aktarabilirsiniz. Denetim, or ifadesine ya da `For` `While` `Do` `Loop` `Until` OR yan tümcesini içeren or ifadesine `While` ya da içine aktarılmaya denk olan döngü koşulu testine doğrudan geçirilir.  
  
 `Continue`Döngüde, aktarımlara izin veren herhangi bir konumda kullanabilirsiniz. Denetimin aktarılmasına izin veren kurallar [goto ifadesiyle](goto-statement.md)aynıdır.  
  
 Örneğin, bir döngü bir `Try` blok, blok veya blok içinde tamamen içerilmediği takdirde `Catch` `Finally` `Continue` döngüyü dışarı aktarmak için kullanabilirsiniz. Diğer taraftan, `Try` ... `End Try` yapısı döngü içinde yer alıyorsa, `Continue` denetimi bloğunun dışına aktarmak için kullanamazsınız `Finally` ve `Try` `Catch` yalnızca... yapısından tamamen dışarı aktarırsanız bir veya bloğunun dışına aktarmak için kullanabilirsiniz `Try` `End Try` .  
  
 Aynı türde iç içe geçmiş döngülerine sahipseniz (örneğin, başka bir `Do` döngü içindeki bir döngü) `Do` , bir `Continue Do` ifade kendisini içeren en içteki döngünün bir sonraki yinelemesine atlar `Do` . `Continue`Aynı türdeki bir kapsayan döngünün sonraki yinelemesine atlamak için öğesini kullanamazsınız.  
  
 Farklı türlerde iç içe geçmiş döngülerine sahipseniz (örneğin, `Do` döngü içindeki bir döngü), ya da `For` kullanarak iki döngünün bir sonraki yinelemesine atlayabilirsiniz `Continue Do` `Continue For` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `Continue While` bir bölen sıfırsa bir dizinin sonraki sütununa atlamak için ifadesini kullanır. `Continue While`Bir `For` döngü içinde. Bu, `While col < lastcol` döngüsünü içeren en içteki döngünün bir sonraki yinelemesi olan ifadesine aktarır `While` `For` .  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Do...Loop Deyimi](do-loop-statement.md)
- [For...Next Deyimi](for-next-statement.md)
- [While...End While Deyimi](while-end-while-statement.md)
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
