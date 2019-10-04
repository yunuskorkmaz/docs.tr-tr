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
ms.openlocfilehash: 9c25653809c51662ea5b606ab97be6a9b50d5986
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956941"
---
# <a name="exit-statement-visual-basic"></a>Exit Deyimi (Visual Basic)

Bir yordam veya bloğundan çıkar ve denetimi yordam çağrısının veya blok tanımının ardından gelen deyime hemen aktarır.

## <a name="syntax"></a>Sözdizimi

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Deyimler

 `Exit Do`  
 Görüntülenen `Do` döngüsünden hemen çıkar. Yürütme `Loop` ifadesiyle sonraki deyimle devam eder. `Exit Do`, yalnızca bir `Do` döngüsü içinde kullanılabilir. İç içe `Do` döngüleri içinde kullanıldığında, `Exit Do` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.

 `Exit For`  
 Görüntülenen `For` döngüsünden hemen çıkar. Yürütme `Next` ifadesiyle sonraki deyimle devam eder. `Exit For`, yalnızca bir `For`... `Next` veya `For Each`... `Next` döngüsü içinde kullanılabilir. İç içe `For` döngüleri içinde kullanıldığında, `Exit For` en içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.

 `Exit Function`  
 ' In göründüğü `Function` yordamından hemen çıkar. Yürütme, `Function` yordamını çağıran deyimden sonraki deyimle devam eder. `Exit Function`, yalnızca bir `Function` yordamı içinde kullanılabilir.

 Bir dönüş değeri belirtmek için, `Exit Function` ifadesinden önceki bir satırdaki işlev adına değeri atayabilirsiniz. Dönüş değerini atamak ve tek bir ifadede işlevinden çıkmak için, bunun yerine [return ifadesini](return-statement.md)kullanabilirsiniz.

 `Exit Property`  
 ' In göründüğü `Property` yordamından hemen çıkar. Yürütme, `Property` yordamını çağıran deyimle devam eder, diğer bir deyişle, özellik değerini talep eden veya ayarla. `Exit Property`, yalnızca bir özelliğin `Get` veya `Set` yordamı içinde kullanılabilir.

 Bir `Get` yordamında bir dönüş değeri belirtmek için, değeri `Exit Property` ifadesinden önceki bir satırdaki işlev adına atayabilirsiniz. Dönüş değerini atamak ve tek bir ifadede `Get` yordamından çıkmak için, bunun yerine `Return` ifadesini kullanabilirsiniz.

 @No__t-0 yordamında `Exit Property` deyimleri `Return` ifadesiyle eşdeğerdir.

 `Exit Select`  
 Görüntülenen `Select Case` bloğundan hemen çıkar. Yürütme `End Select` ifadesiyle sonraki deyimle devam eder. `Exit Select`, yalnızca bir `Select Case` ifadesinde kullanılabilir.

 `Exit Sub`  
 ' In göründüğü `Sub` yordamından hemen çıkar. Yürütme, `Sub` yordamını çağıran deyimden sonraki deyimle devam eder. `Exit Sub`, yalnızca bir `Sub` yordamı içinde kullanılabilir.

 @No__t-0 yordamında `Exit Sub` deyimleri `Return` ifadesiyle eşdeğerdir.

 `Exit Try`  
 @No__t-0 veya `Catch` bloğundan hemen çıkar. Yürütme, varsa `Finally` bloğu ile devam eder veya `End Try` deyiminden sonraki deyimle devam eder. `Exit Try`, yalnızca bir `Try` veya `Catch` bloğunda kullanılabilir ve `Finally` bloğu içinde kullanılamaz.

 `Exit While`  
 Görüntülenen `While` döngüsünden hemen çıkar. Yürütme `End While` ifadesiyle sonraki deyimle devam eder. `Exit While`, yalnızca bir `While` döngüsü içinde kullanılabilir. İç içe `While` döngüleri içinde kullanıldığında, `Exit While` denetimi, döngünün üzerinde `Exit While` gerçekleştiği bir iç içe bir düzey olan döngüye aktarır.

## <a name="remarks"></a>Açıklamalar

@No__t-0 deyimlerini `End` deyimleriyle karıştırmayın. `Exit` bir deyimin sonunu tanımlamaz.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `index` değişkeni 100 ' den büyükse döngü koşulu döngüyü sonlandırır. Ancak, döngüdeki `If` ifadesinde, dizin değişkeni 10 ' dan büyük olduğunda `Exit Do` ifadesinin döngüyü durdurmasına neden olur.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, `myFunction` işlev adına dönüş değeri atar ve sonra işlevden dönmek için `Exit Function` kullanır:

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, dönüş değerini atamak ve işlevden çıkmak için [return ifadesini](return-statement.md) kullanır:

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>Ayrıca bkz.

- [Continue Deyimi](continue-statement.md)
- [Do...Loop Deyimi](do-loop-statement.md)
- [End Deyimi](end-statement.md)
- [For Each...Next Deyimi](for-each-next-statement.md)
- [For...Next Deyimi](for-next-statement.md)
- [Function Deyimi](function-statement.md)
- [Return Deyimi](return-statement.md)
- [Stop Deyimi](stop-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
