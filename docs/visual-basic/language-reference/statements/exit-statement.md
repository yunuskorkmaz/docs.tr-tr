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
ms.openlocfilehash: 1f386694bd7425ee530b9305ab684b730f9b73c8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832638"
---
# <a name="exit-statement-visual-basic"></a>Exit Deyimi (Visual Basic)
Bir yordam ya da bloktan çıkıp ve denetim yordam çağrısı ya da blok tanımının takiben deyime hemen aktarır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Deyimler  
 `Exit Do`  
 Hemen çıkar `Do` döngü, bunu görünür. Yürütme devam eder, deyimi aşağıdaki `Loop` deyimi. `Exit Do` yalnızca içinde kullanılan bir `Do` döngü. Kullanıldığında içinde iç içe geçmiş `Do` döngüleri `Exit Do` en içteki döngüden çıkılıp ve yüksek düzeye iç içe aktarır.  
  
 `Exit For`  
 Hemen çıkar `For` döngü, bunu görünür. Yürütme devam eder, deyimi aşağıdaki `Next` deyimi. `Exit For` yalnızca içinde kullanılan bir `For`... `Next` veya `For Each`... `Next` döngü. Kullanıldığında içinde iç içe geçmiş `For` döngüleri `Exit For` en içteki döngüden çıkılıp ve yüksek düzeye iç içe aktarır.  
  
 `Exit Function`  
 Hemen çıkar `Function` göründüğü yordamı. Yürütme devam eder, adlı deyiminin sonrasındaki deyime ile `Function` yordamı. `Exit Function` yalnızca içinde kullanılan bir `Function` yordamı.  
  
 Dönüş değeri belirtmek için değer önce bir satırda işlevi adı atayabilirsiniz `Exit Function` deyimi. Dönüş değeri atamak ve bir deyim işlev çıkmak için bunun yerine kullanabileceğiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Hemen çıkar `Property` göründüğü yordamı. Yürütme devam eder, çağrılan deyimiyle `Property` yordamı, diğer bir deyişle, isteme veya özelliğin değerini ayarlamak deyimi. `Exit Property` yalnızca bir özelliğin içinde kullanılabilir `Get` veya `Set` yordamı.  
  
 Bir dönüş değeri belirtmek için bir `Get` yordamı, önce bir satırda işlevi adı değeri atayabilir `Exit Property` deyimi. Çıkış ve dönüş değeri atamak `Get` bir deyim yordamda, bunun yerine kullanabileceğiniz `Return` deyimi.  
  
 İçinde bir `Set` yordamı `Exit Property` deyimi, `Return` deyimi.  
  
 `Exit Select`  
 Hemen çıkar `Select Case` hangi görünmesini engelleyin. Yürütme devam eder, deyimi aşağıdaki `End Select` deyimi. `Exit Select` yalnızca içinde kullanılan bir `Select Case` deyimi.  
  
 `Exit Sub`  
 Hemen çıkar `Sub` göründüğü yordamı. Yürütme devam eder, adlı deyiminin sonrasındaki deyime ile `Sub` yordamı. `Exit Sub` yalnızca içinde kullanılan bir `Sub` yordamı.  
  
 İçinde bir `Sub` yordamı `Exit Sub` deyimi, `Return` deyimi.  
  
 `Exit Try`  
 Hemen çıkar `Try` veya `Catch` hangi görünmesini engelleyin. Yürütme devam eder ile `Finally` varsa veya deyimi aşağıdaki `End Try` deyimi Aksi takdirde. `Exit Try` yalnızca içinde kullanılan bir `Try` veya `Catch` bloğu ve değil iç bir `Finally` blok.  
  
 `Exit While`  
 Hemen çıkar `While` döngü, bunu görünür. Yürütme devam eder, deyimi aşağıdaki `End While` deyimi. `Exit While` yalnızca içinde kullanılan bir `While` döngü. Kullanıldığında içinde iç içe geçmiş `While` döngüleri `Exit While` döngü yukarıda bir iç içe düzeyi döngü denetim aktarır burada `Exit While` gerçekleşir.  
  
## <a name="remarks"></a>Açıklamalar  
 Karıştırmayın `Exit` ifadelerle `End` deyimleri. `Exit` bir deyim sonu tanımlamıyor.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, döngü koşuluna döngü durdurur, `index` değişkendir 100'den büyük. `If` Döngü deyimi ancak neden `Exit Do` döngüyü dizin değişkeni 10'dan büyük olduğunda durdurmak için deyimi.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction`ve ardından `Exit Function` işlevden döndürülecek.  
  
 [!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) dönüş değerini atayın ve işlev çıkın.  
  
 [!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Continue Deyimi](../../../visual-basic/language-reference/statements/continue-statement.md)
- [Do...Loop Deyimi](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [End Deyimi](../../../visual-basic/language-reference/statements/end-statement.md)
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Return Deyimi](../../../visual-basic/language-reference/statements/return-statement.md)
- [Stop Deyimi](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
