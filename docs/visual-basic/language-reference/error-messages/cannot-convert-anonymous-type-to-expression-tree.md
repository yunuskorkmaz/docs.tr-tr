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
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="f404d-102">Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="f404d-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="f404d-103">Anonim türün başka bir özelliğini başlatmak için anonim türün bir özelliği kullanıldığında derleyici bir ifade ağacına anonim dönüştürmeyi kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="f404d-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="f404d-104">Örneğin, aşağıdaki kodda, `Prop1`, başlatma listesinde bildirilmiştir ve sonra `Prop2` için ilk değer olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f404d-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
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
  
 <span data-ttu-id="f404d-105">**Hata kimliği:** BC36548</span><span class="sxs-lookup"><span data-stu-id="f404d-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f404d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f404d-106">To correct this error</span></span>  
  
- <span data-ttu-id="f404d-107">@No__t-0 için başlangıç değerini yerel bir değişkene atayın.</span><span class="sxs-lookup"><span data-stu-id="f404d-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="f404d-108">Aşağıdaki kodda gösterildiği gibi, bu değişkeni hem `Prop1` hem de `Prop2` ' e atayın.</span><span class="sxs-lookup"><span data-stu-id="f404d-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```vb  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f404d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f404d-109">See also</span></span>

- [<span data-ttu-id="f404d-110">Anonim türler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f404d-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f404d-111">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f404d-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="f404d-112">Nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f404d-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
