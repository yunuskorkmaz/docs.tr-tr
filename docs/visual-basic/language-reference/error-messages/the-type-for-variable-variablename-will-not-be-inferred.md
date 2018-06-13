---
title: Değişken için tür &#39; &lt;variablename&gt; &#39; kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594289"
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="7ff81-102">Değişken için tür &#39; &lt;variablename&gt; &#39; kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil</span><span class="sxs-lookup"><span data-stu-id="7ff81-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="7ff81-103">Değişken türü '\<variablename >' kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil.</span><span class="sxs-lookup"><span data-stu-id="7ff81-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="7ff81-104">Adını değiştirmek '\<variablename >', veya tam adı (örneğin, 'Me.variablename' veya 'MyBase.variablename') kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ff81-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="7ff81-105">For döngüsü denetim değişkeni kodunuzda sınıfı ya da diğer çevreleyen kapsamdaki bir alan olarak aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="7ff81-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="7ff81-106">Denetim değişkeni olmadan kullanıldığından bir `As` yan tümcesi, çevreleyen kapsamdaki alanına bağlı ve derleyici yeni bir değişken için oluşturamadı veya türünü Infer.</span><span class="sxs-lookup"><span data-stu-id="7ff81-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="7ff81-107">Aşağıdaki örnekte, `Index`, Denetim değişkeninde `For` deyimi, bağlı `Index` alanındaki `Customer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ff81-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="7ff81-108">Derleyici denetimi değişken için yeni bir değişken oluşturmaz `Index` veya türünü Infer.</span><span class="sxs-lookup"><span data-stu-id="7ff81-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="7ff81-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="7ff81-109">By default, this message is a warning.</span></span> <span data-ttu-id="7ff81-110">Uyarıları gizleme veya uyarıları hata ele hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7ff81-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7ff81-111">**Hata Kimliği:** BC42110</span><span class="sxs-lookup"><span data-stu-id="7ff81-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="7ff81-112">Bu uyarıyı gidermek için</span><span class="sxs-lookup"><span data-stu-id="7ff81-112">To address this warning</span></span>  
  
-   <span data-ttu-id="7ff81-113">For döngüsü denetim değişkeni sınıfının bir alanın adı olmayan bir tanımlayıcı adını değiştirerek yerel olun.</span><span class="sxs-lookup"><span data-stu-id="7ff81-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="7ff81-114">For döngüsü denetim değişkeni ekleyerek sınıfı alanına bağlar açıklamak `Me.` değişken adı.</span><span class="sxs-lookup"><span data-stu-id="7ff81-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="7ff81-115">Yerel türü çıkarımı güvenmek yerine, kullanın bir `As` tümcesi for döngüsü denetim değişkeni için bir tür belirtin.</span><span class="sxs-lookup"><span data-stu-id="7ff81-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="7ff81-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ff81-116">Example</span></span>  
 <span data-ttu-id="7ff81-117">Aşağıdaki kod, daha önceki örnekteki ilk düzeltme yerinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff81-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ff81-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff81-118">See Also</span></span>  
 [<span data-ttu-id="7ff81-119">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="7ff81-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="7ff81-120">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="7ff81-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="7ff81-121">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="7ff81-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="7ff81-122">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma</span><span class="sxs-lookup"><span data-stu-id="7ff81-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="7ff81-123">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="7ff81-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="7ff81-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="7ff81-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
