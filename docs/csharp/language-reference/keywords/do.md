---
title: do (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a><span data-ttu-id="e12f9-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e12f9-102">do (C# Reference)</span></span>
<span data-ttu-id="e12f9-103">`do` Deyimini yürütür bir deyim veya deyimleri bloğu art arda için belirtilen ifadeyi değerlendirir kadar `false`.</span><span class="sxs-lookup"><span data-stu-id="e12f9-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="e12f9-104">Döngünün gövdesi kaşlı ayraç içinde alınmalıdır `{}`sürece tek bir deyimde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e12f9-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="e12f9-105">Bu durumda, küme ayraçları isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e12f9-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e12f9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e12f9-106">Example</span></span>  
 <span data-ttu-id="e12f9-107">Aşağıdaki örnekte, `do-while` döngü deyimlerini yürütmek değişkeni sürece `x` değerinden 5'tir.</span><span class="sxs-lookup"><span data-stu-id="e12f9-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="e12f9-108">Farklı [sırada](../../../csharp/language-reference/keywords/while.md) deyimi, bir `do-while` döngü koşullu ifade değerlendirilir önce bir kez gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e12f9-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="e12f9-109">Bir oranda noktası `do-while` bloğu, döngü kullanarak dışında bölün [sonu](../../../csharp/language-reference/keywords/break.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="e12f9-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="e12f9-110">Doğrudan adım `while` ifade değerlendirme deyimi kullanarak [devam](../../../csharp/language-reference/keywords/continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="e12f9-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="e12f9-111">Varsa `while` ifade true olarak değerlendirilir, yürütme Döngüdeki ilk ifade adresindeki devam eder.</span><span class="sxs-lookup"><span data-stu-id="e12f9-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="e12f9-112">Yanlış olarak değerlendirilir, ilk ifadeden sonra yürütülmeye `do-while` döngü.</span><span class="sxs-lookup"><span data-stu-id="e12f9-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="e12f9-113">A `do-while` döngü ayrıca çıkıldı tarafından [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="e12f9-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e12f9-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e12f9-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e12f9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e12f9-115">See Also</span></span>  
 [<span data-ttu-id="e12f9-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e12f9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e12f9-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e12f9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e12f9-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e12f9-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e12f9-119">yapın-while deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="e12f9-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="e12f9-120">Yineleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="e12f9-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
