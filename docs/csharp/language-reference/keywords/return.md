---
title: iade deyimi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713137"
---
# <a name="return-c-reference"></a><span data-ttu-id="6cf5e-102">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6cf5e-102">return (C# Reference)</span></span>

<span data-ttu-id="6cf5e-103">İfade, `return` görüntülendiği yöntemin yürütülmesini sonlandırır ve denetimi arama yöntemine döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cf5e-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="6cf5e-104">İsteğe bağlı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="6cf5e-104">It can also return an optional value.</span></span> <span data-ttu-id="6cf5e-105">Yöntem bir `void` türse, `return` deyim atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6cf5e-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="6cf5e-106">İade deyimi bir `try` blok içindeyse, `finally` denetim arama yöntemine dönmeden önce blok, varsa yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6cf5e-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="6cf5e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6cf5e-107">Example</span></span>

 <span data-ttu-id="6cf5e-108">Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişkeni `area` `double` bir değer olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="6cf5e-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="6cf5e-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6cf5e-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6cf5e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cf5e-110">See also</span></span>

- [<span data-ttu-id="6cf5e-111">C# Referans</span><span class="sxs-lookup"><span data-stu-id="6cf5e-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6cf5e-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6cf5e-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6cf5e-113">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="6cf5e-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6cf5e-114">return Deyimi</span><span class="sxs-lookup"><span data-stu-id="6cf5e-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
