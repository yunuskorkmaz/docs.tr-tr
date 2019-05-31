---
title: continue deyimi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: d5fd2f5edf85c3ac2c8f0367b85b37e76e2e856e
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422113"
---
# <a name="continue-c-reference"></a><span data-ttu-id="e792b-102">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e792b-102">continue (C# Reference)</span></span>

<span data-ttu-id="e792b-103">`continue` Deyimi, denetimi kapsayan'ın bir sonraki yinelemesine geçirir [sırada](../../../csharp/language-reference/keywords/while.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [için](../../../csharp/language-reference/keywords/for.md), veya [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi, göründüğü.</span><span class="sxs-lookup"><span data-stu-id="e792b-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="e792b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e792b-104">Example</span></span>

<span data-ttu-id="e792b-105">Bu örnekte, bir sayaç 1'den 10'a saymak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e792b-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="e792b-106">Kullanarak `continue` ifade ile birlikte deyiminde `(i < 9)`, deyimleri arasında `continue` ve sonuna `for` gövdesi atlanır.</span><span class="sxs-lookup"><span data-stu-id="e792b-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="e792b-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e792b-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e792b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e792b-108">See also</span></span>

- [<span data-ttu-id="e792b-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e792b-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="e792b-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e792b-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e792b-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e792b-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="e792b-112">break Deyimi</span><span class="sxs-lookup"><span data-stu-id="e792b-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
