---
title: continue (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: b3a9a17bb16ded19330cbc880b2e5e7271f269c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215676"
---
# <a name="continue-c-reference"></a><span data-ttu-id="81243-102">continue (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="81243-102">continue (C# Reference)</span></span>
<span data-ttu-id="81243-103">`continue` Deyimi kapsayan, sonraki yinelemeye denetim geçirir [sırada](../../../csharp/language-reference/keywords/while.md), [yapmak](../../../csharp/language-reference/keywords/do.md), [için](../../../csharp/language-reference/keywords/for.md), veya [foreach](../../../csharp/language-reference/keywords/foreach-in.md) göründüğü deyimi.</span><span class="sxs-lookup"><span data-stu-id="81243-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81243-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="81243-104">Example</span></span>  
 <span data-ttu-id="81243-105">Bu örnekte, bir sayaç 1'den 10'a saymak için başlatılır.</span><span class="sxs-lookup"><span data-stu-id="81243-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="81243-106">Kullanarak `continue` ifade ile birlikte deyiminde `(i < 9)`, arasında deyimleri `continue` ve sonuna `for` gövde atlanır.</span><span class="sxs-lookup"><span data-stu-id="81243-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="81243-107">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="81243-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81243-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81243-108">See Also</span></span>  
 [<span data-ttu-id="81243-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="81243-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="81243-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="81243-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="81243-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="81243-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="81243-112">break Deyimi</span><span class="sxs-lookup"><span data-stu-id="81243-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
 [<span data-ttu-id="81243-113">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="81243-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
