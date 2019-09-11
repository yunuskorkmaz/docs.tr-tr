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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd6de79965ba9d2639621aabc3be54ef5f87c935
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855465"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="23175-102">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="23175-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="23175-103">Görev paralel kitaplığı (TPL), giriş parametreleri olarak temsilci <xref:System.Func%601?displayProperty=nameWithType> veya <xref:System.Action?displayProperty=nameWithType> temsilcilerden birini alan birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="23175-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="23175-104">Bu temsilcileri, özel program mantığınızı paralel döngü, görev veya sorguya geçirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23175-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="23175-105">Bu temsilcilerin satır içi kod blokları gibi örneklerini oluşturmak için, TPL ve PLıNQ için kod örnekleri lambda ifadeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="23175-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="23175-106">Bu konu, Func ve Action 'a kısa bir giriş sağlar ve paralel kitaplığı ve PLıNQ görevinde lambda ifadelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23175-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="23175-107">Genel olarak Temsilciler hakkında daha fazla bilgi için bkz. [Temsilciler](../../csharp/programming-guide/delegates/index.md) ve [Temsilciler](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="23175-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="23175-108">Ve Visual Basic içindeki C# lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda Ifadeleri](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ve [lambda ifadeleri](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="23175-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="23175-109">Func temsilcisi</span><span class="sxs-lookup"><span data-stu-id="23175-109">Func Delegate</span></span>

<span data-ttu-id="23175-110">Bir `Func` temsilci, bir değer döndüren bir yöntemi kapsüller.</span><span class="sxs-lookup"><span data-stu-id="23175-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="23175-111">Bir Func imzasında, son veya en sağdaki tür parametresi her zaman dönüş türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="23175-111">In a Func signature, the last or rightmost type parameter always specifies the return type.</span></span> <span data-ttu-id="23175-112">Derleyici hatalarının yaygın nedenlerinden biri, ' a <xref:System.Func%602?displayProperty=nameWithType>iki giriş parametresi geçirmeye çalışmasıdır; aslında bu tür yalnızca bir giriş parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="23175-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="23175-113">Framework sınıf kitaplığı, ' nin 17 sürümlerini `Func`( <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Func%603?displayProperty=nameWithType> <xref:System.Func%6017?displayProperty=nameWithType>,, vb.) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23175-113">The Framework Class Library defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="23175-114">Eylem temsilcisi</span><span class="sxs-lookup"><span data-stu-id="23175-114">Action Delegate</span></span>

<span data-ttu-id="23175-115">Bir <xref:System.Action?displayProperty=nameWithType> temsilci, bir değeri döndürmeyen veya [void](../../csharp/language-reference/keywords/void.md)döndüren bir yöntemi (Visual Basic Sub) kapsüller.</span><span class="sxs-lookup"><span data-stu-id="23175-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value, or returns [void](../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="23175-116">Bir eylem türü imzasında, tür parametreleri yalnızca giriş parametrelerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23175-116">In an Action type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="23175-117">Func gibi, Framework sınıf kitaplığı, 16 türünde parametrelere sahip bir sürüm aracılığıyla hiçbir tür parametresi olmayan bir sürümden, eylemin 17 sürümlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23175-117">Like Func, the Framework Class Library defines 17 versions of Action, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="23175-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="23175-118">Example</span></span>

<span data-ttu-id="23175-119"><xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> Yöntemi için aşağıdaki örnek, lambda ifadeleri kullanılarak hem Func hem de eylem temsilcilerinin nasıl ifade alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23175-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="23175-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23175-120">See also</span></span>

- [<span data-ttu-id="23175-121">Paralel Programlama</span><span class="sxs-lookup"><span data-stu-id="23175-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
