---
title: "'<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak"
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013653"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="6f79a-102">Değişkeninin türü '\<variablename >' sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak</span><span class="sxs-lookup"><span data-stu-id="6f79a-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="6f79a-103">Değişkeninin türü '\<variablename >' sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak.</span><span class="sxs-lookup"><span data-stu-id="6f79a-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="6f79a-104">Adını değiştirmek ya da '\<variablename >', veya tam adı (örneğin, 'Me.variablename' veya 'MyBase.variablename') kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f79a-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="6f79a-105">Bir for döngüsü denetim değişkeni kodunuzda, sınıf ya da diğer kapsayan kapsam alan olarak aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="6f79a-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="6f79a-106">Denetim değişkeni olmadan kullanıldığından bir `As` yan tümcesi, kapsayan kapsamda alana bağlı ve derleyici için yeni bir değişken oluşturamadı veya kendi türü çıkarımı.</span><span class="sxs-lookup"><span data-stu-id="6f79a-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="6f79a-107">Aşağıdaki örnekte, `Index`, Denetim değişkeninde `For` deyimi, bağlı `Index` alanındaki `Customer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6f79a-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="6f79a-108">Derleyici, denetim değişkeni için yeni bir değişken oluşturmaz `Index` veya türü çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="6f79a-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="6f79a-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="6f79a-109">By default, this message is a warning.</span></span> <span data-ttu-id="6f79a-110">Uyarıları Gizle veya uyarıları hata olarak değerlendir hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6f79a-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6f79a-111">**Hata Kimliği:** BC42110</span><span class="sxs-lookup"><span data-stu-id="6f79a-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="6f79a-112">Bu uyarıyı gidermek için</span><span class="sxs-lookup"><span data-stu-id="6f79a-112">To address this warning</span></span>  
  
- <span data-ttu-id="6f79a-113">Ayrıca sınıfın bir alanın adı olmayan bir tanımlayıcı adını değiştirerek döngü denetim değişkeni yerel olun.</span><span class="sxs-lookup"><span data-stu-id="6f79a-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
- <span data-ttu-id="6f79a-114">Döngü denetim değişkeni ekleyerek sınıfı alanına bağlar açıklamak `Me.` değişken adı.</span><span class="sxs-lookup"><span data-stu-id="6f79a-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- <span data-ttu-id="6f79a-115">Yerel tür çıkarımı üzerinde bağlı olan yerine bir `As` yan tümcesi for döngüsü denetim değişkeni için bir tür belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="6f79a-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="6f79a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f79a-116">Example</span></span>  
 <span data-ttu-id="6f79a-117">Aşağıdaki kod, önceki örnekte ilk düzeltme yerinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f79a-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f79a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f79a-118">See also</span></span>

- [<span data-ttu-id="6f79a-119">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f79a-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="6f79a-120">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f79a-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="6f79a-121">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f79a-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="6f79a-122">Nasıl yapılır: Bir nesnenin geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="6f79a-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="6f79a-123">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="6f79a-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="6f79a-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="6f79a-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
