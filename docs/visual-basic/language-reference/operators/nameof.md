---
title: NameOf işleci-Visual Basic
description: Visual Basic ' de NameOf işlecinin nasıl kullanılacağını öğrenin
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 8416bb1a1715c1c37b62cac6a9e0b427a9c72547
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041319"
---
# <a name="nameof-operator---visual-basic"></a><span data-ttu-id="b533f-103">NameOf işleci-Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b533f-103">NameOf operator - Visual Basic</span></span>

<span data-ttu-id="b533f-104">`NameOf` işleci, dize sabiti olarak bir değişkenin, türün veya üyenin adını edinir:</span><span class="sxs-lookup"><span data-stu-id="b533f-104">The `NameOf` operator obtains the name of a variable, type, or member as the string constant:</span></span>

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

<span data-ttu-id="b533f-105">Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span><span class="sxs-lookup"><span data-stu-id="b533f-105">As the preceding example shows, in the case of a type and a namespace, the produced name is usually not [fully qualified](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).</span></span>

<span data-ttu-id="b533f-106">`NameOf` işleci derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="b533f-106">The `NameOf` operator is evaluated at compile time, and has no effect at run time.</span></span>

<span data-ttu-id="b533f-107">Bağımsız değişken denetim kodunu daha sürdürülebilir hale getirmek için `NameOf` işlecini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b533f-107">You can use the `NameOf` operator to make the argument-checking code more maintainable:</span></span>

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

<span data-ttu-id="b533f-108">`NameOf` işleci Visual Basic 14 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b533f-108">The `NameOf` operator is available in Visual Basic 14 and later.</span></span>

## <a name="see-also"></a><span data-ttu-id="b533f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b533f-109">See also</span></span>

- [<span data-ttu-id="b533f-110">Visual Basic Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b533f-110">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="b533f-111">İşleçler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b533f-111">Operators (Visual Basic)</span></span>](index.md)
