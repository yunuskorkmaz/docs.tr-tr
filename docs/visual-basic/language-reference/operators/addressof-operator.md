---
title: AddressOf İşleci
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: e88520bd7e731a35b98c1d40c5210dc5d1314911
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350276"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf İşleci (Visual Basic)
Belirli yordama başvuran bir temsilci örneği oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Bölümler  
 `procedurename`  
 Gerekli. Yeni oluşturulan temsilci tarafından başvurulacak prosedürü belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `AddressOf` işleci, `procedurename`tarafından belirtilen Sub veya Function öğesine işaret eden bir temsilci oluşturur. Belirtilen yordam bir örnek yöntemi olduğunda, temsilci hem örneğe hem de yöntemine başvurur. Ardından, temsilci çağrıldığında belirtilen örnek için belirtilen yöntem çağrılır.  
  
 `AddressOf` işleci, bir temsilci oluşturucusunun işleneni olarak kullanılabilir ya da temsilci türünün derleyici tarafından belirlenebileceği bir bağlamda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir düğmenin `Click` olayını işlemek üzere bir temsilci belirlemek için `AddressOf` işlecini kullanır.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir iş parçacığının başlangıç işlevini belirlemek için `AddressOf` işlecini kullanır.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
