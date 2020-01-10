---
title: Continue bildirisi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713669"
---
# <a name="continue-c-reference"></a><span data-ttu-id="23db3-102">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="23db3-102">continue (C# Reference)</span></span>

<span data-ttu-id="23db3-103">`continue` ifadesi, denetimin göründüğü [while](./while.md), [Do](./do.md), [for](./for.md)veya [foreach](./foreach-in.md) ifadesinin bir sonraki yinelemesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="23db3-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="23db3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="23db3-104">Example</span></span>

<span data-ttu-id="23db3-105">Bu örnekte, bir sayaç 1 ile 10 arasında bir sayı olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="23db3-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="23db3-106">`continue` deyimini ifade `(i < 9)`ile birlikte kullanarak, `for` gövdesinin `continue` ve sonundaki deyimler atlanır.</span><span class="sxs-lookup"><span data-stu-id="23db3-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="23db3-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="23db3-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="23db3-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23db3-108">See also</span></span>

- [<span data-ttu-id="23db3-109">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="23db3-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="23db3-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="23db3-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="23db3-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="23db3-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="23db3-112">break Deyimi</span><span class="sxs-lookup"><span data-stu-id="23db3-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
