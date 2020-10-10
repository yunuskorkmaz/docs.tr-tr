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
ms.openlocfilehash: 6c70934c3b861e1a1433e5c0b95bb32e9d717c53
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877658"
---
# <a name="continue-c-reference"></a><span data-ttu-id="18100-103">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="18100-103">continue (C# Reference)</span></span>

<span data-ttu-id="18100-104">`continue`İfadesi, denetimi içinde göründüğü [while](./while.md), [Do](./do.md), [for](./for.md)veya [foreach](./foreach-in.md) deyimlerinin bir sonraki yinelemesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="18100-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="18100-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="18100-105">Example</span></span>

<span data-ttu-id="18100-106">Bu örnekte, bir sayaç 1 ile 10 arasında bir sayı olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="18100-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="18100-107">`continue`Deyimi ifadesiyle birlikte kullanarak `(i < 9)` , gövde sonu arasındaki deyimler, `continue` 9 ' `for` dan küçük olan yinelemelerde atlanır `i` .</span><span class="sxs-lookup"><span data-stu-id="18100-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped in the iterations where `i` is less than 9.</span></span> <span data-ttu-id="18100-108">Döngünün son iki tekrarda `for` (i = = 9 ve i = = 10), `continue` ifade yürütülmez ve değeri `i` konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="18100-108">In the last two iterations of the `for` loop (where i == 9 and i == 10), the `continue` statement is not executed and the value of `i` is printed to the console.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="18100-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="18100-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="18100-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18100-110">See also</span></span>

- [<span data-ttu-id="18100-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="18100-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="18100-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="18100-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="18100-113">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="18100-113">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="18100-114">Break ekstresi</span><span class="sxs-lookup"><span data-stu-id="18100-114">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
