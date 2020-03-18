---
title: C# foreach deyimi
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: dbe4f4e95c2b99f1be47885e39d51db81ba3a97d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173711"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="c62fc-102">foreach, in (C# referans)</span><span class="sxs-lookup"><span data-stu-id="c62fc-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="c62fc-103">Deyim, `foreach` her öğe için bir deyim <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> ifade bloğu uygular türü veya arabirimi uygulayan bir örnek teveks.</span><span class="sxs-lookup"><span data-stu-id="c62fc-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c62fc-104">Bildirim `foreach` bu türlerle sınırlı değildir ve aşağıdaki koşulları yerine getiren herhangi bir türe uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="c62fc-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="c62fc-105">dönüş türü sınıf, `GetEnumerator` yapı veya arayüz türü olan ortak parametresiz yönteme sahiptir,</span><span class="sxs-lookup"><span data-stu-id="c62fc-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="c62fc-106">yöntemin `GetEnumerator` dönüş türü kamu `Current` malı ve geri dönüş `MoveNext` türü olan <xref:System.Boolean>kamu parametresiz yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="c62fc-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="c62fc-107">C# 7.3 ile başlayarak, numaralandırıcının `Current` özelliği bir referans dönüş `T` [değeri](ref.md#reference-return-values) döndürürse (toplama`ref T` öğesinin türü nerede), yineleme değişkenini veya `ref` `ref readonly` değiştiriciile birlikte bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c62fc-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="c62fc-108">C# 8.0 ile `await` başlayarak, koleksiyon `foreach` türü arabirimi uyguladığında <xref:System.Collections.Generic.IAsyncEnumerable%601> işleç deyimine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c62fc-108">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="c62fc-109">Döngünün her yinelemesi, bir sonraki öğe eş senkronize olarak alınırken askıya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="c62fc-109">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="c62fc-110">Varsayılan olarak, akış öğeleri yakalanan bağlamında işlenir.</span><span class="sxs-lookup"><span data-stu-id="c62fc-110">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="c62fc-111">Bağlamın ele geçirilmesini devre dışı kılmış <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> olmak istiyorsanız, uzantı yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c62fc-111">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="c62fc-112">Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi [için, Görev tabanlı eşzamanlı deseni tüketme makalesine](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c62fc-112">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="c62fc-113">İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilir veya continue deyimini kullanarak döngüdeki bir sonraki yinelemeye adım atabilirsiniz. [continue](continue.md) `foreach`</span><span class="sxs-lookup"><span data-stu-id="c62fc-113">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c62fc-114">Ayrıca `foreach` [goto,](goto.md) [return](return.md)veya [atmak](throw.md) ifadeleri tarafından bir döngü çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c62fc-114">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="c62fc-115">İfadesi `foreach` `null`uygulanırsa, <xref:System.NullReferenceException> a atılır.</span><span class="sxs-lookup"><span data-stu-id="c62fc-115">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="c62fc-116">`foreach` İfadenin kaynak koleksiyonu boşsa, `foreach` döngügövdesi yürütülmez ve atlanır.</span><span class="sxs-lookup"><span data-stu-id="c62fc-116">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="c62fc-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c62fc-117">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c62fc-118">Aşağıdaki örnek, ifadenin `foreach` <xref:System.Collections.Generic.IEnumerable%601> arabirimi uygulayan <xref:System.Collections.Generic.List%601> türe ait bir örneği yle kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c62fc-118">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="c62fc-119">Sonraki örnek, `foreach` herhangi bir arabirim <xref:System.Span%601?displayProperty=nameWithType> uygulamaz türü, bir örnek ile deyimi kullanır:</span><span class="sxs-lookup"><span data-stu-id="c62fc-119">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="c62fc-120">Aşağıdaki örnek, `ref` stackalloc dizisindeher öğenin değerini ayarlamak için bir yineleme değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="c62fc-120">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="c62fc-121">Sürüm, `ref readonly` tüm değerleri yazdırmak için koleksiyonu yineler.</span><span class="sxs-lookup"><span data-stu-id="c62fc-121">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="c62fc-122">Bildirimde `readonly` örtülü yerel değişken bildirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c62fc-122">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="c62fc-123">Örtük değişken bildirimleri, `ref` açıkça `ref readonly` yazılan değişken bildirimleri gibi, ya da bildirimleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c62fc-123">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

<span data-ttu-id="c62fc-124">Aşağıdaki örnek, `await foreach` her öğeyi eşit olarak oluşturan bir koleksiyonu yinelemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="c62fc-124">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a><span data-ttu-id="c62fc-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c62fc-125">C# language specification</span></span>

<span data-ttu-id="c62fc-126">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [foreach deyimi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c62fc-126">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c62fc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c62fc-127">See also</span></span>

- [<span data-ttu-id="c62fc-128">C# Referans</span><span class="sxs-lookup"><span data-stu-id="c62fc-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c62fc-129">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c62fc-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c62fc-130">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="c62fc-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c62fc-131">Foreach'i dizilerle kullanma</span><span class="sxs-lookup"><span data-stu-id="c62fc-131">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="c62fc-132">ifade için</span><span class="sxs-lookup"><span data-stu-id="c62fc-132">for statement</span></span>](for.md)
