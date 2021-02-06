---
description: 'Hakkında daha fazla bilgi edinin: BC42324: bir lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir'
title: Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: a21e33c9a8737642d4d0764e92b1fbb2213f9602
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640881"
---
# <a name="bc42324-using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="27321-103">BC42324: bir lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir</span><span class="sxs-lookup"><span data-stu-id="27321-103">BC42324: Using the iteration variable in a lambda expression may have unexpected results</span></span>

<span data-ttu-id="27321-104">Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="27321-104">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="27321-105">Bunun yerine, döngü içinde bir yerel değişken oluşturun ve bunu yineleme değişkeninin değerine atayın.</span><span class="sxs-lookup"><span data-stu-id="27321-105">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>

 <span data-ttu-id="27321-106">Bu uyarı, döngü içinde belirtilen bir lambda ifadesinde bir döngü yineleme değişkeni kullandığınızda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="27321-106">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="27321-107">Örneğin, aşağıdaki örnek uyarının görünmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="27321-107">For example, the following example causes the warning to appear.</span></span>

```vb
For i As Integer = 1 To 10
    ' The warning is given for the use of i.
    Dim exampleFunc As Func(Of Integer) = Function() i
Next
```

 <span data-ttu-id="27321-108">Aşağıdaki örnek, gerçekleşebilecek beklenmeyen sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="27321-108">The following example shows the unexpected results that might occur.</span></span>

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            array1(i) = Function() i
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

 <span data-ttu-id="27321-109">`For`Döngü, her biri döngü yineleme değişkeninin değerini döndüren bir lambda ifadeleri dizisi oluşturur `i` .</span><span class="sxs-lookup"><span data-stu-id="27321-109">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="27321-110">Lambda ifadeleri `For Each` döngüde değerlendirildiğinde, döngüde art arda gelen değerleri 0, 1, 2, 3 ve 4 ' ü görmeyi bekleyebilir `i` `For` .</span><span class="sxs-lookup"><span data-stu-id="27321-110">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="27321-111">Bunun yerine, en son `i` beş kez görüntülenmiş değeri görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="27321-111">Instead, you see the final value of `i` displayed five times:</span></span>

 `5`

 `5`

 `5`

 `5`

 `5`

 <span data-ttu-id="27321-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="27321-112">By default, this message is a warning.</span></span> <span data-ttu-id="27321-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="27321-113">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="27321-114">**Hata kimliği:** BC42324</span><span class="sxs-lookup"><span data-stu-id="27321-114">**Error ID:** BC42324</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="27321-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="27321-115">To correct this error</span></span>

- <span data-ttu-id="27321-116">Yineleme değişkeninin değerini yerel bir değişkene atayın ve yerel değişkeni lambda ifadesinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="27321-116">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            Dim j = i
            array1(i) = Function() j
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="27321-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27321-117">See also</span></span>

- [<span data-ttu-id="27321-118">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="27321-118">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
