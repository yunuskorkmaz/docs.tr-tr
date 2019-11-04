---
title: C#foreach ifadesi
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422806"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="be4cc-102">foreach, in (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="be4cc-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="be4cc-103">`foreach` deyimi, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimini uygulayan tür örneğindeki her öğe için bir deyimi veya bir deyim bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="be4cc-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="be4cc-104">`foreach` deyimleri bu türlerle sınırlı değildir ve aşağıdaki koşullara uyan herhangi bir türün örneğine uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="be4cc-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="be4cc-105">, dönüş türü Class, struct veya Interface türünde olan public parametresiz `GetEnumerator` yöntemine sahiptir</span><span class="sxs-lookup"><span data-stu-id="be4cc-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="be4cc-106">`GetEnumerator` yönteminin dönüş türü, ortak `Current` özelliğine ve dönüş türü <xref:System.Boolean>olan public parametresiz `MoveNext` metoduna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="be4cc-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="be4cc-107">7,3 ile C# başlayarak, numaralandırıcının `Current` özelliği bir [Başvuru dönüş değeri](ref.md#reference-return-values) döndürürse (`T` koleksiyon öğesinin türü olduğu`ref T`), yineleme değişkenini `ref` veya `ref readonly` değiştiricisiyle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be4cc-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="be4cc-108">`foreach` bildiri bloğunun içindeki herhangi bir noktada, [Break](break.md) ifadesini kullanarak döngünün dışına bölebilir veya [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adım aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be4cc-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="be4cc-109">Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `foreach` döngüsünden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be4cc-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="be4cc-110">`foreach` deyimin `null`uygulanmışsa bir <xref:System.NullReferenceException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="be4cc-110">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="be4cc-111">`foreach` deyimin kaynak koleksiyonu boşsa, `foreach` döngüsünün gövdesi yürütülmez ve atlanır.</span><span class="sxs-lookup"><span data-stu-id="be4cc-111">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop is not executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="be4cc-112">Örnekler</span><span class="sxs-lookup"><span data-stu-id="be4cc-112">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="be4cc-113">Aşağıdaki örnek, <xref:System.Collections.Generic.IEnumerable%601> arabirimini uygulayan <xref:System.Collections.Generic.List%601> türünün bir örneği ile `foreach` deyimin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="be4cc-113">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="be4cc-114">Sonraki örnek, hiçbir arabirim uygulamayan <xref:System.Span%601?displayProperty=nameWithType> türünün bir örneği ile `foreach` ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="be4cc-114">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="be4cc-115">Aşağıdaki örnek, bir stackalloc dizisindeki her bir öğenin değerini ayarlamak için bir `ref` yineleme değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="be4cc-115">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="be4cc-116">`ref readonly` sürümü, tüm değerleri yazdırmak için koleksiyonu yineler.</span><span class="sxs-lookup"><span data-stu-id="be4cc-116">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="be4cc-117">`readonly` bildirimi örtük bir yerel değişken bildirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="be4cc-117">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="be4cc-118">Örtük değişken bildirimleri `ref` veya `ref readonly` bildirimleriyle birlikte kullanılabilir, böylece açıkça değişken bildirimleri bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="be4cc-118">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="be4cc-119">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="be4cc-119">C# language specification</span></span>

<span data-ttu-id="be4cc-120">Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [foreach ifadesi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="be4cc-120">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="be4cc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be4cc-121">See also</span></span>

- [<span data-ttu-id="be4cc-122">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="be4cc-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be4cc-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="be4cc-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be4cc-124">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="be4cc-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be4cc-125">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="be4cc-125">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="be4cc-126">for deyimleri</span><span class="sxs-lookup"><span data-stu-id="be4cc-126">for statement</span></span>](for.md)
