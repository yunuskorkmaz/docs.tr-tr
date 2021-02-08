---
description: "Daha fazla bilgi edinin: PLıNQ ve TPL 'deki lambda Ifadeleri"
title: PLINQ ve TPL'deki Lambda İfadeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 86ecfca0e9866a08b4f4bb40d15b74257ec4540e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798036"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="fb371-103">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="fb371-103">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="fb371-104">Görev paralel kitaplığı (TPL), <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Action?displayProperty=nameWithType> giriş parametreleri olarak temsilci veya temsilcilerden birini alan birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="fb371-104">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="fb371-105">Bu temsilcileri, özel program mantığınızı paralel döngü, görev veya sorguya geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb371-105">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="fb371-106">Bu temsilcilerin satır içi kod blokları gibi örneklerini oluşturmak için, TPL ve PLıNQ için kod örnekleri lambda ifadeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb371-106">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="fb371-107">Bu konu, Func ve Action 'a kısa bir giriş sağlar ve paralel kitaplığı ve PLıNQ görevinde lambda ifadelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb371-107">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="fb371-108">Genel olarak Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../csharp/programming-guide/delegates/index.md) ve [Temsilciler](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb371-108">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="fb371-109">C# ve Visual Basic lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../csharp/language-reference/operators/lambda-expressions.md) ve [lambda ifadeleri](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fb371-109">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/language-reference/operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="fb371-110">Func temsilcisi</span><span class="sxs-lookup"><span data-stu-id="fb371-110">Func Delegate</span></span>

<span data-ttu-id="fb371-111">Bir `Func` temsilci, bir değer döndüren bir yöntemi kapsüller.</span><span class="sxs-lookup"><span data-stu-id="fb371-111">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="fb371-112">Bir `Func` İmzada, son veya en sağdaki tür parametresi her zaman dönüş türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb371-112">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="fb371-113">Derleyici hatalarının yaygın nedenlerinden biri, ' a iki giriş parametresi geçirmeye çalışmasıdır <xref:System.Func%602?displayProperty=nameWithType> ; aslında bu tür yalnızca bir giriş parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="fb371-113">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="fb371-114">.Net, ' ın 17 sürümlerini (,, vb.) tanımlar `Func` <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Func%603?displayProperty=nameWithType> <xref:System.Func%6017?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fb371-114">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="fb371-115">Eylem temsilcisi</span><span class="sxs-lookup"><span data-stu-id="fb371-115">Action Delegate</span></span>

<span data-ttu-id="fb371-116">Bir <xref:System.Action?displayProperty=nameWithType> temsilci, bir değeri döndürmeyen bir yöntemi (Visual Basic Sub) kapsüller.</span><span class="sxs-lookup"><span data-stu-id="fb371-116">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="fb371-117">`Action`Tür imzasında, tür parametreleri yalnızca giriş parametrelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb371-117">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="fb371-118">Benzer şekilde `Func` , .net, `Action` 16 tür parametrelere sahip bir sürüm aracılığıyla hiçbir tür parametresi olmayan bir sürümden, ' nin 17 sürümlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fb371-118">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="fb371-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb371-119">Example</span></span>

<span data-ttu-id="fb371-120">Yöntemi için aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> lambda ifadeleri kullanılarak hem Func hem de eylem temsilcilerinin nasıl ifade alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb371-120">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="fb371-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb371-121">See also</span></span>

- [<span data-ttu-id="fb371-122">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="fb371-122">Parallel Programming</span></span>](index.md)
