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
ms.locfileid: "33585482"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="78b0b-102">Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="78b0b-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="78b0b-103">Anonim türün bir özellik anonim türünde başka bir özellik başlatmak için kullanıldığında, derleyici dönüştürülmesi bir anonim bir ifade ağacına kabul etmiyor.</span><span class="sxs-lookup"><span data-stu-id="78b0b-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="78b0b-104">Örneğin, aşağıdaki kodda, `Prop1` başlatma listesinde bildirilen ve ilk değeri olarak kullanılan `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="78b0b-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
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
  
 <span data-ttu-id="78b0b-105">**Hata Kimliği:** BC36548</span><span class="sxs-lookup"><span data-stu-id="78b0b-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78b0b-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="78b0b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="78b0b-107">İlk değeri atamak `Prop1` yerel değişkene.</span><span class="sxs-lookup"><span data-stu-id="78b0b-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="78b0b-108">Bu değişken hem de Ata `Prop1` ve `Prop2`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="78b0b-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="78b0b-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78b0b-109">See Also</span></span>  
 [<span data-ttu-id="78b0b-110">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="78b0b-110">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="78b0b-111">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="78b0b-111">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [<span data-ttu-id="78b0b-112">Nasıl yapılır: Dinamik Sorgular Derlemek için İfade Ağaçları Kullanma</span><span class="sxs-lookup"><span data-stu-id="78b0b-112">How to: Use Expression Trees to Build Dynamic Queries</span></span>](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
