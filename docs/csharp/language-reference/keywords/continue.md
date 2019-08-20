---
title: Continue bildirisi- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 74d166dbcf03b868baf464864e4c246f789df9cc
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605877"
---
# <a name="continue-c-reference"></a><span data-ttu-id="9f9f0-102">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9f9f0-102">continue (C# Reference)</span></span>

<span data-ttu-id="9f9f0-103">[](./foreach-in.md) [](./do.md) [](./for.md) [](./while.md)İfadesi, denetimi içinde göründüğü while, do, for veya ForEach deyimlerinin bir sonraki yinelemesine geçirir. `continue`</span><span class="sxs-lookup"><span data-stu-id="9f9f0-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="9f9f0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f9f0-104">Example</span></span>

<span data-ttu-id="9f9f0-105">Bu örnekte, bir sayaç 1 ile 10 arasında bir sayı olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="9f9f0-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="9f9f0-106">`continue` Deyimini ifadesiyle `(i < 9)`birlikte kullanarak, `for` gövdenin sonu arasındaki `continue` deyimler atlanır.</span><span class="sxs-lookup"><span data-stu-id="9f9f0-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="9f9f0-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9f9f0-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9f9f0-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f9f0-108">See also</span></span>

- [<span data-ttu-id="9f9f0-109">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9f9f0-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9f9f0-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9f9f0-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9f9f0-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9f9f0-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9f9f0-112">break Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f9f0-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
