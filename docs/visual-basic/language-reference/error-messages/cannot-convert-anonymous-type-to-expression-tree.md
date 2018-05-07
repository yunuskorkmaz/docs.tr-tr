---
title: Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: d43f6ef19591af326d06a4ce21194d8f9fa58c2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.
Anonim türün bir özellik anonim türünde başka bir özellik başlatmak için kullanıldığında, derleyici dönüştürülmesi bir anonim bir ifade ağacına kabul etmiyor. Örneğin, aşağıdaki kodda, `Prop1` başlatma listesinde bildirilen ve ilk değeri olarak kullanılan `Prop2`.  
  
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
  
 **Hata Kimliği:** BC36548  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İlk değeri atamak `Prop1` yerel değişkene. Bu değişken hem de Ata `Prop1` ve `Prop2`aşağıdaki kodda gösterildiği gibi.  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [İfade Ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [Nasıl yapılır: Dinamik Sorgular Derlemek için İfade Ağaçları Kullanma](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
