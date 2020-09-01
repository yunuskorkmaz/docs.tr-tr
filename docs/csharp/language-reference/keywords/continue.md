---
description: Continue bildirisi-C# başvurusu
title: Continue bildirisi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128445"
---
# <a name="continue-c-reference"></a><span data-ttu-id="83fc8-103">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="83fc8-103">continue (C# Reference)</span></span>

<span data-ttu-id="83fc8-104">`continue`İfadesi, denetimi içinde göründüğü [while](./while.md), [Do](./do.md), [for](./for.md)veya [foreach](./foreach-in.md) deyimlerinin bir sonraki yinelemesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="83fc8-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="83fc8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="83fc8-105">Example</span></span>

<span data-ttu-id="83fc8-106">Bu örnekte, bir sayaç 1 ile 10 arasında bir sayı olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="83fc8-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="83fc8-107">`continue`Deyimini ifadesiyle birlikte kullanarak `(i < 9)` , `continue` gövdenin sonu arasındaki deyimler `for` atlanır.</span><span class="sxs-lookup"><span data-stu-id="83fc8-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="83fc8-108">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="83fc8-108">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="83fc8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83fc8-109">See also</span></span>

- [<span data-ttu-id="83fc8-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="83fc8-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83fc8-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="83fc8-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83fc8-112">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="83fc8-112">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="83fc8-113">Break ekstresi</span><span class="sxs-lookup"><span data-stu-id="83fc8-113">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
