---
title: while (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a><span data-ttu-id="94821-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="94821-102">while (C# Reference)</span></span>
<span data-ttu-id="94821-103">`while` Deyimi, bir deyim veya ifadeleri bir blok için belirtilen ifadeyi değerlendirir kadar yürütür `false`.</span><span class="sxs-lookup"><span data-stu-id="94821-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94821-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="94821-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="94821-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="94821-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="94821-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="94821-106">Example</span></span>  
 <span data-ttu-id="94821-107">Çünkü sınamasını `while` ifade başlamaz döngünün her yürütmeden önce bir `while` sıfır veya daha fazla kez döngü yürütür.</span><span class="sxs-lookup"><span data-stu-id="94821-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="94821-108">Bu farklıdır [yapmak](../../../csharp/language-reference/keywords/do.md) bir veya birden çok kez yürütür döngü.</span><span class="sxs-lookup"><span data-stu-id="94821-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="94821-109">A `while` döngü bitmelidir ne zaman bir [sonu](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimi dışında denetimi aktarır döngü.</span><span class="sxs-lookup"><span data-stu-id="94821-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="94821-110">Döngü çıkmadan sonraki yinelemeye denetim geçirmek için kullanmak [devam](../../../csharp/language-reference/keywords/continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="94821-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="94821-111">Where bağlı olarak üç önceki örnek çıktıda fark `int n` artırılır.</span><span class="sxs-lookup"><span data-stu-id="94821-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="94821-112">Çıktı aşağıdaki örnekte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="94821-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="94821-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="94821-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94821-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94821-114">See Also</span></span>  
 [<span data-ttu-id="94821-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="94821-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="94821-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="94821-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="94821-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="94821-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="94821-118">while deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="94821-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="94821-119">Yineleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="94821-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
