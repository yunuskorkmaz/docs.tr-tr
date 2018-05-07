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
ms.openlocfilehash: 7c229c32a3b295b4dbfe50ca2abc60d4ad5f2145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="addressof-operator-visual-basic"></a>AddressOf İşleci (Visual Basic)
Özel yordam başvuruda bulunan bir yordam temsilci örneği oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Bölümler  
 `procedurename`  
 Gerekli. Yeni oluşturulan yordamı temsilci tarafından başvurulan yordamı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `AddressOf` İşleci tarafından belirtilen işlevin işaret eden bir işlev temsilcisi oluşturur `procedurename`. Örnek ve yöntemi için örnek yöntemi sonra işlev temsilcisi başvuruyor belirtilen yordam olduğunda. Ardından, işlev temsilcisi çağrıldığında belirtilen örneğinin belirtilen yöntem çağrılır.  
  
 `AddressOf` İşleci temsilci Oluşturucu işleneni olarak kullanılabilir veya hangi temsilci türü belirlenebilir derleyici tarafından bağlamda kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `AddressOf` işlemek için temsilci atamak işleci `Click` düğmesinin olay.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `AddressOf` başlangıç işlevi için bir iş parçacığı atamak işleci.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
