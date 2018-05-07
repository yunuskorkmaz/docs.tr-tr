---
title: Exit Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 05a65dd84a00478f52c8cd7d8b46341644512718
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exit-statement-visual-basic"></a>Exit Deyimi (Visual Basic)
Bir yordam veya blok çıkar ve denetim hemen yordam çağrısı veya bloğu tanımı aşağıdaki deyim aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Deyimler  
 `Exit Do`  
 Hemen çıkar `Do` döngü onu görünen içinde. Yürütülmeye deyimi aşağıdaki `Loop` deyimi. `Exit Do` yalnızca içinde kullanılan bir `Do` döngü. Kullanıldığında içinde iç içe geçmiş `Do` döngüler, `Exit Do` en içteki döngüden çıkılıp ve iç içe geçme sonraki yüksek düzeyde denetim aktarır.  
  
 `Exit For`  
 Hemen çıkar `For` döngü onu görünen içinde. Yürütülmeye deyimi aşağıdaki `Next` deyimi. `Exit For` yalnızca içinde kullanılan bir `For`... `Next` veya `For Each`... `Next` döngü. Kullanıldığında içinde iç içe geçmiş `For` döngüler, `Exit For` en içteki döngüden çıkılıp ve iç içe geçme sonraki yüksek düzeyde denetim aktarır.  
  
 `Exit Function`  
 Hemen çıkar `Function` göründüğü yordamı. Yürütülmeye adlı deyiminden deyimiyle `Function` yordamı. `Exit Function` yalnızca içinde kullanılan bir `Function` yordamı.  
  
 Dönüş değeri belirtmek için değeri önce bir satırda işlev adı atayabilirsiniz `Exit Function` deyimi. Dönüş değeri atamak ve bir deyim işlevinde'ndan çıkmak için bunun yerine kullanabileceğiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Hemen çıkar `Property` göründüğü yordamı. Yürütülmeye adlı deyimiyle `Property` yordamı, diğer bir deyişle, isteme veya özelliğin değerini ayarlama ifadesiyle. `Exit Property` yalnızca bir özelliğin içinde kullanılabilir `Get` veya `Set` yordamı.  
  
 Bir dönüş değeri belirtmek için bir `Get` yordamı, önce bir satırda işlev adı için değer atayabilirsiniz `Exit Property` deyimi. Dönüş değeri ve çıkış atamak için `Get` bir deyim yordamda, bunun yerine kullanabileceğiniz `Return` deyimi.  
  
 İçinde bir `Set` yordamı, `Exit Property` deyimi eşdeğerdir `Return` deyimi.  
  
 `Exit Select`  
 Hemen çıkar `Select Case` onu görünen içinde engelleyin. Yürütülmeye deyimi aşağıdaki `End Select` deyimi. `Exit Select` yalnızca içinde kullanılan bir `Select Case` deyimi.  
  
 `Exit Sub`  
 Hemen çıkar `Sub` göründüğü yordamı. Yürütülmeye adlı deyiminden deyimiyle `Sub` yordamı. `Exit Sub` yalnızca içinde kullanılan bir `Sub` yordamı.  
  
 İçinde bir `Sub` yordamı, `Exit Sub` deyimi eşdeğerdir `Return` deyimi.  
  
 `Exit Try`  
 Hemen çıkar `Try` veya `Catch` onu görünen içinde engelleyin. Yürütülmeye ile `Finally` blok varsa veya deyimi aşağıdaki `End Try` deyimi Aksi takdirde. `Exit Try` yalnızca içinde kullanılan bir `Try` veya `Catch` bloğu ve değil iç bir `Finally` bloğu.  
  
 `Exit While`  
 Hemen çıkar `While` döngü onu görünen içinde. Yürütülmeye deyimi aşağıdaki `End While` deyimi. `Exit While` yalnızca içinde kullanılan bir `While` döngü. Kullanıldığında içinde iç içe geçmiş `While` döngüler, `Exit While` denetimi bir iç içe düzeyi döngü yukarıda döngü aktarır nerede `Exit While` oluşur.  
  
## <a name="remarks"></a>Açıklamalar  
 Aynı şey `Exit` deyimleri `End` deyimleri. `Exit` bir deyim sonu tanımlamıyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü koşulunu döngü durur zaman `index` değişkenidir 100'den büyük. `If` Döngüdeki deyimi ancak neden `Exit Do` deyimi dizin değişken 10'dan büyük olduğunda döngü durdurmak için.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction`ve ardından `Exit Function` işlevinden dönün.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) dönüş değeri atamak ve işlev çıkın.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Continue Deyimi](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)  
 [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return Deyimi](../../../visual-basic/language-reference/statements/return-statement.md)  
 [Stop Deyimi](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
