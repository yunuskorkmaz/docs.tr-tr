---
description: 'Daha fazla bilgi edinin: AddressOf Işleci (Visual Basic)'
title: AddressOf İşleci
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 2aba8c26aa9581fe1070574b8c408e09bf063d1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774388"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf İşleci (Visual Basic)

Belirli yordama başvuran bir temsilci örneği oluşturur.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Bölümler  

 `procedurename`  
 Gereklidir. Yeni oluşturulan temsilci tarafından başvurulacak prosedürü belirtir.  
  
## <a name="remarks"></a>Açıklamalar  

 `AddressOf`İşleci, tarafından belirtilen Sub veya Function öğesine işaret eden bir temsilci oluşturur `procedurename` . Belirtilen yordam bir örnek yöntemi olduğunda, temsilci hem örneğe hem de yöntemine başvurur. Ardından, temsilci çağrıldığında belirtilen örnek için belirtilen yöntem çağrılır.  
  
 `AddressOf`İşleci, bir temsilci oluşturucusunun işleneni olarak kullanılabilir ya da temsilci türünün derleyici tarafından belirlenebileceği bir bağlamda kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `AddressOf` bir düğmenin olayını işlemek üzere bir temsilci belirlemek için işlecini kullanır `Click` .  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `AddressOf` bir iş parçacığının başlangıç işlevini belirlemek için işlecini kullanır.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Declare Deyimi](../statements/declare-statement.md)
- [Function Deyimi](../statements/function-statement.md)
- [Sub Deyimi](../statements/sub-statement.md)
- [Temsilciler](../../programming-guide/language-features/delegates/index.md)
