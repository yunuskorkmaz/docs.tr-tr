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
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760382"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf İşleci (Visual Basic)
Özel yordam başvuran bir temsilci örneği oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Bölümler  
 `procedurename`  
 Gerekli. Yeni oluşturulan temsilci tarafından başvurulabilmesi için yordamı belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 `AddressOf` İşleci sub veya function tarafından belirtilen işaret eden bir temsilci oluşturur `procedurename`. Bir örnek yöntemi temsilci örneği hem yöntemi başvuruyor belirtilen yordam olduğunda. Ardından, temsilci çağrıldığında belirtilen örneğinin belirtilen yöntem çağrılır.  
  
 `AddressOf` İşleci, bir temsilci Oluşturucu işleneni kullanılabilir veya bir bağlamda, temsilci türü belirlenebilir derleyici tarafından kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `AddressOf` işlemek için bir temsilci atamak için işleç `Click` düğmesinin olay.  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `AddressOf` iş parçacığı başlangıç işlevi atamak için işleç.  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)
