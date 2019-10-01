---
title: Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: ba14c0cd8781b8771ac8b746e3efec29a457294a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701183"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.
Anonim türün başka bir özelliğini başlatmak için anonim türün bir özelliği kullanıldığında derleyici bir ifade ağacına anonim dönüştürmeyi kabul etmez. Örneğin, aşağıdaki kodda, `Prop1`, başlatma listesinde bildirilmiştir ve sonra `Prop2` için ilk değer olarak kullanılır.  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **Hata kimliği:** BC36548  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- @No__t-0 için başlangıç değerini yerel bir değişkene atayın. Aşağıdaki kodda gösterildiği gibi, bu değişkeni hem `Prop1` hem de `Prop2` ' e atayın.  
  
    ```vb  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Anonim türler (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [İfade ağaçları (Visual Basic)](../../programming-guide/concepts/expression-trees/index.md)
- [Nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (Visual Basic)](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
