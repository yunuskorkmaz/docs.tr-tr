---
title: "'<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak"
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512720"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="3dd9b-102">'\<VariableName > ' değişkeninin türü, kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak</span><span class="sxs-lookup"><span data-stu-id="3dd9b-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="3dd9b-103">'\<VariableName > ' değişkeninin türü, kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="3dd9b-104">'\<VariableName > ' adını değiştirin ya da tam adı kullanın (örneğin, ' me. variablename ' veya ' MyBase. variablename ').</span><span class="sxs-lookup"><span data-stu-id="3dd9b-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="3dd9b-105">Kodunuzda bir döngü denetim değişkeni, sınıfın veya diğer kapsayan kapsamdaki bir alanla aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="3dd9b-106">Denetim değişkeni bir `As` yan tümce olmadan kullanıldığı için, kapsayan kapsamdaki alana bağlanır ve derleyici bunun için yeni bir değişken oluşturmaz veya türünü çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="3dd9b-107">Aşağıdaki örnekte `Index`, `For` deyimindeki denetim değişkeni, `Customer` sınıfındaki `Index` alana bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="3dd9b-108">Derleyici, denetim değişkeni `Index` için yeni bir değişken oluşturmaz veya türünü çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
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

<span data-ttu-id="3dd9b-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-109">By default, this message is a warning.</span></span> <span data-ttu-id="3dd9b-110">Uyarıların nasıl gizleneceği veya uyarıların hata olarak nasıl değerlendirildiğinin hakkında bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3dd9b-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="3dd9b-111">**Hata KIMLIĞI:** BC42110</span><span class="sxs-lookup"><span data-stu-id="3dd9b-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="3dd9b-112">Bu uyarıyı çözmek için</span><span class="sxs-lookup"><span data-stu-id="3dd9b-112">To address this warning</span></span>

- <span data-ttu-id="3dd9b-113">Adını, aynı zamanda sınıfının bir alanının adı olmayan bir tanımlayıcı olarak değiştirerek döngü denetim değişkenini yerel yapın.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="3dd9b-114">Döngü denetimi değişkeninin, değişken adına önek `Me.` olarak sınıf alanına bağlamadığını açıklığa kavuşturun.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="3dd9b-115">Yerel tür çıkarımı güvenmek yerine, döngü denetim değişkeni `As` için bir tür belirtmek için bir yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="3dd9b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3dd9b-116">Example</span></span>
 <span data-ttu-id="3dd9b-117">Aşağıdaki kod, önceki örnekte yer aldığı ilk düzeltmeyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="3dd9b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dd9b-118">See also</span></span>

- [<span data-ttu-id="3dd9b-119">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="3dd9b-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3dd9b-120">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="3dd9b-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="3dd9b-121">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="3dd9b-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3dd9b-122">Nasıl yapılır: Nesnenin geçerli örneğine başvurma</span><span class="sxs-lookup"><span data-stu-id="3dd9b-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="3dd9b-123">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="3dd9b-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="3dd9b-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="3dd9b-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
