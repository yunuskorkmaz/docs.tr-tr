---
title: "Değişken &#39;türü; &lt;variablename&gt;&#39; kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords: BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39968407f4de5436df324320c99dede4d72e2808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="0a567-102">Değişken &#39;türü; &lt;variablename&gt;&#39; kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil</span><span class="sxs-lookup"><span data-stu-id="0a567-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="0a567-103">Değişken türü '\<variablename >' kapsayan bir kapsama alanına bağlı olduğundan, çıkarılabilir olacaktır değil.</span><span class="sxs-lookup"><span data-stu-id="0a567-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="0a567-104">Adını değiştirmek '\<variablename >', veya tam adı (örneğin, 'Me.variablename' veya 'MyBase.variablename') kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a567-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="0a567-105">For döngüsü denetim değişkeni kodunuzda sınıfı ya da diğer çevreleyen kapsamdaki bir alan olarak aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="0a567-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="0a567-106">Denetim değişkeni olmadan kullanıldığından bir `As` yan tümcesi, çevreleyen kapsamdaki alanına bağlı ve derleyici yeni bir değişken için oluşturamadı veya türünü Infer.</span><span class="sxs-lookup"><span data-stu-id="0a567-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="0a567-107">Aşağıdaki örnekte, `Index`, Denetim değişkeninde `For` deyimi, bağlı `Index` alanındaki `Customer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0a567-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="0a567-108">Derleyici denetimi değişken için yeni bir değişken oluşturmaz `Index` veya türünü Infer.</span><span class="sxs-lookup"><span data-stu-id="0a567-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="0a567-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="0a567-109">By default, this message is a warning.</span></span> <span data-ttu-id="0a567-110">Uyarıları gizleme veya uyarıları hata ele hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0a567-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0a567-111">**Hata Kimliği:** BC42110</span><span class="sxs-lookup"><span data-stu-id="0a567-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="0a567-112">Bu uyarıyı gidermek için</span><span class="sxs-lookup"><span data-stu-id="0a567-112">To address this warning</span></span>  
  
-   <span data-ttu-id="0a567-113">For döngüsü denetim değişkeni sınıfının bir alanın adı olmayan bir tanımlayıcı adını değiştirerek yerel olun.</span><span class="sxs-lookup"><span data-stu-id="0a567-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="0a567-114">For döngüsü denetim değişkeni ekleyerek sınıfı alanına bağlar açıklamak `Me.` değişken adı.</span><span class="sxs-lookup"><span data-stu-id="0a567-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="0a567-115">Yerel türü çıkarımı güvenmek yerine, kullanın bir `As` tümcesi for döngüsü denetim değişkeni için bir tür belirtin.</span><span class="sxs-lookup"><span data-stu-id="0a567-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="0a567-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a567-116">Example</span></span>  
 <span data-ttu-id="0a567-117">Aşağıdaki kod, daha önceki örnekteki ilk düzeltme yerinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a567-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0a567-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a567-118">See Also</span></span>  
 [<span data-ttu-id="0a567-119">Option Infer deyimi</span><span class="sxs-lookup"><span data-stu-id="0a567-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="0a567-120">For Each... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="0a567-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="0a567-121">İçin... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="0a567-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="0a567-122">Nasıl yapılır: bir nesnenin geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="0a567-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="0a567-123">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="0a567-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="0a567-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="0a567-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
