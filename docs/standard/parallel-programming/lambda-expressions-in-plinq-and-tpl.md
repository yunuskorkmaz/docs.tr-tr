---
title: PLINQ ve TPL'deki Lambda İfadeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 4e5be295a52edc1a7f0a0a3aa98f55335ae3e31b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453006"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="9579b-102">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9579b-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="9579b-103">Görev Paralel Kitaplığı (TPL), giriş parametreleri <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Action?displayProperty=nameWithType> olarak temsilci veya aile deneyenlerden birini alan birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="9579b-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="9579b-104">Bu temsilciler, özel program mantığınızı paralel döngüye, göreve veya sorguya geçirmek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9579b-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="9579b-105">TPL ve PLINQ için kod örnekleri, bu temsilcilerin satır satırlı kod blokları olarak örneklerini oluşturmak için lambda ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9579b-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="9579b-106">Bu konu Func ve Action'a kısa bir giriş sağlar ve Görev Paralel Kitaplığı ve PLINQ'da lambda ifadelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9579b-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="9579b-107">Genel olarak temsilciler hakkında daha fazla bilgi [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md) [için, bkz.](../../csharp/programming-guide/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="9579b-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="9579b-108">C# ve Visual Basic'teki lambda ifadeleri hakkında daha fazla bilgi için [Lambda İfadeleri](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Lambda İfadeleri'ne](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9579b-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="9579b-109">Func Delegesi</span><span class="sxs-lookup"><span data-stu-id="9579b-109">Func Delegate</span></span>

<span data-ttu-id="9579b-110">Bir `Func` temsilci, bir değer döndüren bir yöntemi kapsüller.</span><span class="sxs-lookup"><span data-stu-id="9579b-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="9579b-111">Bir `Func` imzada, en son veya en sağdaki tür parametresi her zaman dönüş türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9579b-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="9579b-112">Derleyici hatalarının yaygın bir nedeni, iki giriş parametresini bir <xref:System.Func%602?displayProperty=nameWithType>; aslında bu tür yalnızca bir giriş parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="9579b-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="9579b-113">.NET 17 versiyonunu `Func`tanımlar <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType>: <xref:System.Func%603?displayProperty=nameWithType>, , ve <xref:System.Func%6017?displayProperty=nameWithType>benzeri kadar .</span><span class="sxs-lookup"><span data-stu-id="9579b-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="9579b-114">Eylem Delegesi</span><span class="sxs-lookup"><span data-stu-id="9579b-114">Action Delegate</span></span>

<span data-ttu-id="9579b-115">Bir <xref:System.Action?displayProperty=nameWithType> temsilci, bir değer döndürmeyen bir yöntemi (Visual Basic'te Alt) kapsüller.</span><span class="sxs-lookup"><span data-stu-id="9579b-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="9579b-116">Bir `Action` tür imzasında, tür parametreleri yalnızca giriş parametrelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9579b-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="9579b-117">Gibi `Func`, .NET 16 `Action`tür parametreleri olan bir sürüm aracılığıyla hiçbir tür parametreleri olan bir sürümden 17 sürümlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9579b-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="9579b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="9579b-118">Example</span></span>

<span data-ttu-id="9579b-119"><xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> Yöntem için aşağıdaki örnek, lambda ifadelerini kullanarak hem Func hem de Eylem temsilcilerinin nasıl ifade edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9579b-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="9579b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9579b-120">See also</span></span>

- [<span data-ttu-id="9579b-121">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="9579b-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
