---
description: "Şu konuda daha fazla bilgi edinin: BC42110: ' ' değişkeninin türü, <variablename> kapsayan bir kapsamdaki alana bağlandığından çıkarsanmayacak"
title: "'<variablename>' değişkeninin türü sarmalayan bir kapsamda bir alana bağlı olduğundan çıkarılmayacak"
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: db31f1a6e87a2fd133f095e2fbdde7bc6bded97e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641245"
---
# <a name="bc42110-the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="bf479-103">BC42110: ' ' değişkeninin türü, \<variablename> kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak</span><span class="sxs-lookup"><span data-stu-id="bf479-103">BC42110: The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="bf479-104">' ' Değişkeninin türü, \<variablename> kapsayan kapsamdaki bir alana bağlandığı için çıkarsmayacak.</span><span class="sxs-lookup"><span data-stu-id="bf479-104">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="bf479-105">' ' Adını değiştirin ya da \<variablename> tam adı kullanın (örneğin, ' me. variablename ' veya ' MyBase. variablename ').</span><span class="sxs-lookup"><span data-stu-id="bf479-105">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="bf479-106">Kodunuzda bir döngü denetim değişkeni, sınıfın veya diğer kapsayan kapsamdaki bir alanla aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bf479-106">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="bf479-107">Denetim değişkeni bir yan tümce olmadan kullanıldığı için `As` , kapsayan kapsamdaki alana bağlanır ve derleyici bunun için yeni bir değişken oluşturmaz veya türünü çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="bf479-107">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="bf479-108">Aşağıdaki örnekte, `Index` deyimindeki denetim değişkeni, `For` `Index` sınıfındaki alana bağlanır `Customer` .</span><span class="sxs-lookup"><span data-stu-id="bf479-108">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="bf479-109">Derleyici, denetim değişkeni için yeni bir değişken oluşturmaz `Index` veya türünü çıkarmaz.</span><span class="sxs-lookup"><span data-stu-id="bf479-109">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

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

<span data-ttu-id="bf479-110">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="bf479-110">By default, this message is a warning.</span></span> <span data-ttu-id="bf479-111">Uyarıların nasıl gizleneceği veya uyarıların hata olarak nasıl değerlendirildiğinin hakkında bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bf479-111">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="bf479-112">**Hata kimliği:** BC42110</span><span class="sxs-lookup"><span data-stu-id="bf479-112">**Error ID:** BC42110</span></span>

## <a name="to-address-this-warning"></a><span data-ttu-id="bf479-113">Bu uyarıyı çözmek için</span><span class="sxs-lookup"><span data-stu-id="bf479-113">To address this warning</span></span>

- <span data-ttu-id="bf479-114">Adını, aynı zamanda sınıfının bir alanının adı olmayan bir tanımlayıcı olarak değiştirerek döngü denetim değişkenini yerel yapın.</span><span class="sxs-lookup"><span data-stu-id="bf479-114">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="bf479-115">Döngü denetimi değişkeninin, değişken adına önek olarak sınıf alanına bağlamadığını açıklığa kavuşturun `Me.` .</span><span class="sxs-lookup"><span data-stu-id="bf479-115">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="bf479-116">Yerel tür çıkarımı güvenmek yerine, `As` döngü denetim değişkeni için bir tür belirtmek için bir yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf479-116">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="bf479-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf479-117">Example</span></span>

 <span data-ttu-id="bf479-118">Aşağıdaki kod, önceki örnekte yer aldığı ilk düzeltmeyi göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bf479-118">The following code shows the earlier example with the first correction in place.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bf479-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf479-119">See also</span></span>

- [<span data-ttu-id="bf479-120">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf479-120">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="bf479-121">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf479-121">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="bf479-122">For...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="bf479-122">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="bf479-123">Nasıl yapılır: Bir Nesnenin Geçerli Örneğine Başvurma</span><span class="sxs-lookup"><span data-stu-id="bf479-123">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="bf479-124">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf479-124">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="bf479-125">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="bf479-125">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
