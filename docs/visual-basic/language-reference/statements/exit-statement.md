---
description: 'Daha fazla bilgi edinin: Exit deyiminiz (Visual Basic)'
title: Exit Deyimi
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
ms.openlocfilehash: 54af7fbf908dbad829cf6f08bf442dfe85e35610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769136"
---
# <a name="exit-statement-visual-basic"></a>Exit Deyimi (Visual Basic)

Bir yordam veya bloğundan çıkar ve denetimi yordam çağrısının veya blok tanımının ardından gelen deyime hemen aktarır.

## <a name="syntax"></a>Syntax

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a>Deyimler

 `Exit Do`  
 `Do`Üzerinde Göründüğü döngüden hemen çıkar. Yürütme, deyimden sonraki deyimle devam eder `Loop` . `Exit Do` yalnızca bir döngü içinde kullanılabilir `Do` . İç içe döngüler içinde kullanıldığında `Do` , en `Exit Do` içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.

 `Exit For`  
 `For`Üzerinde Göründüğü döngüden hemen çıkar. Yürütme, deyimden sonraki deyimle devam eder `Next` . `Exit For` yalnızca bir `For` ... `Next` veya `For Each` ... döngüsü içinde kullanılabilir `Next` . İç içe döngüler içinde kullanıldığında `For` , en `Exit For` içteki döngüden çıkar ve denetimi sonraki daha yüksek iç içe geçme düzeyine aktarır.

 `Exit Function`  
 `Function`Görüntülenen yordamdan hemen çıkar. Yürütme yordamı çağıran deyimden sonraki deyimle devam eder `Function` . `Exit Function` yalnızca bir yordam içinde kullanılabilir `Function` .

 Bir dönüş değeri belirtmek için, değeri deyimden önceki bir satırdaki işlev adına atayabilirsiniz `Exit Function` . Dönüş değerini atamak ve tek bir ifadede işlevinden çıkmak için, bunun yerine [return ifadesini](return-statement.md)kullanabilirsiniz.

 `Exit Property`  
 `Property`Görüntülenen yordamdan hemen çıkar. Yürütme, yordamı çağıran deyimle devam eder `Property` , diğer bir deyişle, özelliğin değerini talep eden veya ayarla. `Exit Property` yalnızca bir özelliğin `Get` ya da yordamın içinde kullanılabilir `Set` .

 Bir yordamda dönüş değeri belirtmek için `Get` , değeri deyimden önceki bir satırdaki işlev adına atayabilirsiniz `Exit Property` . Dönüş değerini atamak ve `Get` yordamın tek bir ifadede çıkış yapmak için, bunun yerine `Return` ifadesini kullanabilirsiniz.

 Bir `Set` yordamda, `Exit Property` deyimleri `Return` ifadesiyle eşdeğerdir.

 `Exit Select`  
 `Select Case`Görüntülenen bloğundan hemen çıkar. Yürütme, deyimden sonraki deyimle devam eder `End Select` . `Exit Select` yalnızca bir deyimin içinde kullanılabilir `Select Case` .

 `Exit Sub`  
 `Sub`Görüntülenen yordamdan hemen çıkar. Yürütme yordamı çağıran deyimden sonraki deyimle devam eder `Sub` . `Exit Sub` yalnızca bir yordam içinde kullanılabilir `Sub` .

 Bir `Sub` yordamda, `Exit Sub` deyimleri `Return` ifadesiyle eşdeğerdir.

 `Exit Try`  
 `Try`Görüntülenen veya bloğundan hemen çıkar `Catch` . Yürütme, varsa bloğa devam eder `Finally` veya deyimden sonraki deyimle devam eder `End Try` . `Exit Try` yalnızca bir veya bloğu içinde kullanılabilir `Try` `Catch` ve bir blok içinde kullanılamaz `Finally` .

 `Exit While`  
 `While`Üzerinde Göründüğü döngüden hemen çıkar. Yürütme, deyimden sonraki deyimle devam eder `End While` . `Exit While` yalnızca bir döngü içinde kullanılabilir `While` . İç içe döngüler içinde kullanıldığında `While` , `Exit While` denetimi döngünün üzerinde bir iç içe geçmiş düzeyi olan döngüye aktarır `Exit While` .

## <a name="remarks"></a>Açıklamalar

Deyimlerini `Exit` `End` deyimlerle karıştırmayın. `Exit` bir deyimin sonunu tanımlamaz.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, değişken 100 ' den büyükse döngü koşulu döngüyü sonlandırır `index` . `If`Ancak, döngüdeki ifade, `Exit Do` Dizin değişkeni 10 ' dan büyük olduğunda deyimin döngüyü durdurmasına neden olur.

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, dönüş değerini işlev adına atar `myFunction` ve sonra `Exit Function` işlevden dönmek için kullanır:

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, dönüş değerini atamak ve işlevden çıkmak için [return ifadesini](return-statement.md) kullanır:

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a>Ayrıca bkz.

- [Continue Deyimi](continue-statement.md)
- [Do...Loop Deyimi](do-loop-statement.md)
- [End ekstresi](end-statement.md)
- [For Each...Next Deyimi](for-each-next-statement.md)
- [For...Next Deyimi](for-next-statement.md)
- [Function Deyimi](function-statement.md)
- [Return Deyimi](return-statement.md)
- [Stop Deyimi](stop-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
