---
title: "continue (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords: continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1ace2c90d03593b51b9ea461a47e122c5da1ab81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="continue-c-reference"></a><span data-ttu-id="3b4a8-102">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3b4a8-102">continue (C# Reference)</span></span>
<span data-ttu-id="3b4a8-103">`continue` Deyimi kapsayan, sonraki yinelemeye denetim geçirir [sırada](../../../csharp/language-reference/keywords/while.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [için](../../../csharp/language-reference/keywords/for.md), veya [foreach](../../../csharp/language-reference/keywords/foreach-in.md) göründüğü deyimi.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b4a8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b4a8-104">Example</span></span>  
 <span data-ttu-id="3b4a8-105">Bu örnekte, bir sayaç 1'den 10'a saymak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="3b4a8-106">Kullanarak `continue` ifade ile birlikte deyiminde `(i < 9)`, arasında deyimleri `continue` ve sonuna `for` gövde atlanır.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3b4a8-107">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3b4a8-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b4a8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b4a8-108">See Also</span></span>  
 [<span data-ttu-id="3b4a8-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3b4a8-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3b4a8-110">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b4a8-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3b4a8-111">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3b4a8-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3b4a8-112">break deyimi</span><span class="sxs-lookup"><span data-stu-id="3b4a8-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
 [<span data-ttu-id="3b4a8-113">Atlama deyimleri</span><span class="sxs-lookup"><span data-stu-id="3b4a8-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
