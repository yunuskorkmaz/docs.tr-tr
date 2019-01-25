---
title: AddressOf İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 4f4f88551b6708ac3d0ee0f0f5bdcbdec1dfaaa9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721086"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf İşleci (Visual Basic)
Özel yordam başvuran bir yordam temsilci örneği oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Bölümler  
 `procedurename`  
 Gerekli. Yeni oluşturulan yordamı temsilci tarafından başvurulabilmesi için yordamı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `AddressOf` İşleci tarafından belirtilen işlevin işaret eden bir işlev temsilcisi oluşturur `procedurename`. Örnek hem yöntemi bir örnek yöntemi ardından işlev temsilcisi başvuruyor belirtilen yordam olduğunda. Ardından, işlev temsilcisi çağrıldığında belirtilen örneğinin belirtilen yöntem çağrılır.  
  
 `AddressOf` İşleci, bir temsilci Oluşturucu işleneni kullanılabilir veya bir bağlamda, temsilci türü belirlenebilir derleyici tarafından kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `AddressOf` işlemek için bir temsilci atamak için işleç `Click` düğmesinin olay.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `AddressOf` iş parçacığı başlangıç işlevi atamak için işleç.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
