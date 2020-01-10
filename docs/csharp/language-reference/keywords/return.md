---
title: Return bildirisi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713137"
---
# <a name="return-c-reference"></a><span data-ttu-id="d8291-102">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d8291-102">return (C# Reference)</span></span>

<span data-ttu-id="d8291-103">`return` ifadesi, göründüğü yöntemin yürütmesini sonlandırır ve çağırma yöntemine denetimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8291-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="d8291-104">Ayrıca, isteğe bağlı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d8291-104">It can also return an optional value.</span></span> <span data-ttu-id="d8291-105">Yöntem bir `void` türüdür, `return` deyimleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8291-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="d8291-106">Return ifadesinin bir `try` bloğu içindeyse, varsa `finally` bloğu, Denetim çağıran yönteme döndürmeden önce yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d8291-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="d8291-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8291-107">Example</span></span>

 <span data-ttu-id="d8291-108">Aşağıdaki örnekte, yöntemi `CalculateArea()` `area` yerel değişkeni `double` değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8291-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="d8291-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d8291-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d8291-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8291-110">See also</span></span>

- [<span data-ttu-id="d8291-111">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="d8291-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d8291-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d8291-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d8291-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d8291-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d8291-114">return Deyimi</span><span class="sxs-lookup"><span data-stu-id="d8291-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
