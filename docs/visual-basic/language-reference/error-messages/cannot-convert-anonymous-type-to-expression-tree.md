---
title: Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: a6ddbaa358709fe306f1529112d1f2bd0a715a91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649965"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="2ef6e-102">Anonim türün bir alanı başka bir alanı başlatmak için kullanıldığından; anonim tür, ifade ağacına dönüştürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="2ef6e-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="2ef6e-103">Anonim türün başka bir özelliğini başlatmak için anonim türün bir özellik kullanıldığında, derleyici dönüştürülmesi anonim bir ifade ağacı kabul etmiyor.</span><span class="sxs-lookup"><span data-stu-id="2ef6e-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="2ef6e-104">Örneğin, aşağıdaki kodda, `Prop1` başlatma listesinde bildirilen ve ardından ilk değeri olarak kullanılan `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="2ef6e-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
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
  
 <span data-ttu-id="2ef6e-105">**Hata Kimliği:** BC36548</span><span class="sxs-lookup"><span data-stu-id="2ef6e-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ef6e-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2ef6e-106">To correct this error</span></span>  
  
- <span data-ttu-id="2ef6e-107">İlk değeri atamak `Prop1` yerel bir değişkene.</span><span class="sxs-lookup"><span data-stu-id="2ef6e-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="2ef6e-108">Bu değişken hem de Ata `Prop1` ve `Prop2`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2ef6e-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2ef6e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ef6e-109">See also</span></span>

- [<span data-ttu-id="2ef6e-110">Anonim türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ef6e-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="2ef6e-111">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ef6e-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="2ef6e-112">Nasıl yapılır: (Visual Basic) dinamik sorgular derlemek için ifade ağaçları kullanma</span><span class="sxs-lookup"><span data-stu-id="2ef6e-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
