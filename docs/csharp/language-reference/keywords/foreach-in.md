---
title: C# foreach ifadesi
ms.date: 06/03/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 1645a246c9feee2a92c0d4e4bbeda47f0afde7d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401894"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="6617b-102">foreach, in (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6617b-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="6617b-103">`foreach`Deyimi, veya arabirimini uygulayan tür örneğindeki her öğe için bir deyimi veya bir deyim bloğunu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6617b-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="6617b-104">`foreach`Deyimleri bu türlerle sınırlı değildir ve aşağıdaki koşullara uyan herhangi bir türün örneğine uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="6617b-104">The `foreach` statement isn't limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="6617b-105">, `GetEnumerator` dönüş türü Class, struct veya Interface türünde olan public parametresiz metoda sahiptir</span><span class="sxs-lookup"><span data-stu-id="6617b-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="6617b-106">metodun dönüş türü, `GetEnumerator` ortak `Current` özelliğine ve dönüş türü olan public parametresiz metoda sahiptir `MoveNext` <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="6617b-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="6617b-107">Çoğu kullanımda, `foreach` `IEnumerable<T>` her öğe türünde olan bir ifadeyi yineler `T` .</span><span class="sxs-lookup"><span data-stu-id="6617b-107">In most uses, `foreach` iterates an `IEnumerable<T>` expression where each element is of type `T`.</span></span> <span data-ttu-id="6617b-108">Ancak öğeler, özelliğin türünden örtük veya açık dönüştürmeye sahip herhangi bir tür olabilir `Current` .</span><span class="sxs-lookup"><span data-stu-id="6617b-108">However, the elements may be any type that has an implicit or explicit conversion from the type of the `Current` property.</span></span> <span data-ttu-id="6617b-109">`Current`Özelliği döndürürse `SomeType` , öğelerin türü şu olabilir:</span><span class="sxs-lookup"><span data-stu-id="6617b-109">If the `Current` property returns `SomeType`, the type of the elements may be:</span></span>

- <span data-ttu-id="6617b-110">Temel sınıflarından herhangi biri `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="6617b-110">Any of the base classes of `SomeType`.</span></span>
- <span data-ttu-id="6617b-111">Tarafından uygulanan arabirimlerden herhangi biri `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="6617b-111">Any of the interfaces implemented by `SomeType`.</span></span>

<span data-ttu-id="6617b-112">Ayrıca, `SomeType` bir veya ise, `class` `interface` `sealed` öğelerin türü şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="6617b-112">Furthermore, if `SomeType` is a `class` or an `interface` and not `sealed`, the type of elements may include:</span></span>

- <span data-ttu-id="6617b-113">Öğesinden türetilmiş herhangi bir tür `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="6617b-113">Any type derived from `SomeType`.</span></span>
- <span data-ttu-id="6617b-114">Herhangi bir rastgele arabirim.</span><span class="sxs-lookup"><span data-stu-id="6617b-114">Any arbitrary interface.</span></span> <span data-ttu-id="6617b-115">Herhangi bir arabirim, veya uygulamadan türetilmiş bir sınıf tarafından uygulanabileceğinden, herhangi bir arabirime izin verilir `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="6617b-115">Any interface is allowed because any interface may be implemented by a class derived from or implementing `SomeType`.</span></span>

<span data-ttu-id="6617b-116">Önceki kurallarla eşleşen herhangi bir türü kullanarak yineleme değişkenini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6617b-116">You may declare the iteration variable using any type that matches the preceding rules.</span></span> <span data-ttu-id="6617b-117">`SomeType`Yineleme değişkeninin türüne dönüştürme, açık bir dönüştürme gerektiriyorsa, bu işlem <xref:System.InvalidCastException> dönüştürme başarısız olduğunda bir oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="6617b-117">If the conversion from `SomeType` to the type of the iteration variable requires an explicit cast, that operation may throw an <xref:System.InvalidCastException> when the conversion fails.</span></span>

<span data-ttu-id="6617b-118">C# 7,3 ile başlayarak, Numaralandırıcı `Current` özelliği bir [Başvuru dönüş değeri](ref.md#reference-return-values) döndürürse ( `ref T` burada `T` koleksiyon öğesinin türüdür), yineleme değişkenini `ref` veya `ref readonly` değiştiriciyle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6617b-118">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="6617b-119">C# 8,0 ' den başlayarak, `await` `foreach` koleksiyon türü arabirimini uygularsa işleç ifadeye uygulanabilir <xref:System.Collections.Generic.IAsyncEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="6617b-119">Beginning with C# 8.0, the `await` operator may be applied to the `foreach` statement when the collection type implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="6617b-120">Next öğesi zaman uyumsuz olarak alındığında döngünün her yinelemesi askıya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="6617b-120">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="6617b-121">Akış öğeleri varsayılan olarak yakalanan bağlamda işlenir.</span><span class="sxs-lookup"><span data-stu-id="6617b-121">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="6617b-122">Bağlam yakalamayı devre dışı bırakmak istiyorsanız, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6617b-122">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="6617b-123">Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz model](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="6617b-123">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

<span data-ttu-id="6617b-124">Deyimdeki herhangi bir noktada `foreach` , [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6617b-124">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="6617b-125">Ayrıca `foreach` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6617b-125">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="6617b-126">`foreach`İfade öğesine uygulanırsa `null` , bir oluşturulur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="6617b-126">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="6617b-127">Deyimin kaynak koleksiyonu `foreach` boşsa, `foreach` Döngünün gövdesi yürütülmez ve atlanır.</span><span class="sxs-lookup"><span data-stu-id="6617b-127">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="examples"></a><span data-ttu-id="6617b-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6617b-128">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="6617b-129">Aşağıdaki örnek, `foreach` arabirimini uygulayan türünün bir örneği ile deyimin kullanımını gösterir <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="6617b-129">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="6617b-130">Sonraki örnek, `foreach` <xref:System.Span%601?displayProperty=nameWithType> hiçbir arabirim uygulamayan türü bir örneği ile ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="6617b-130">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="6617b-131">Aşağıdaki örnek, bir `ref` stackalloc dizisindeki her bir öğenin değerini ayarlamak için bir yineleme değişkeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="6617b-131">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="6617b-132">`ref readonly`Sürüm, tüm değerleri yazdırmak için koleksiyonu yineler.</span><span class="sxs-lookup"><span data-stu-id="6617b-132">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="6617b-133">`readonly`Bildirim örtük bir yerel değişken bildirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6617b-133">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="6617b-134">Örtük değişken bildirimleri, ya da `ref` `ref readonly` bildirimleriyle birlikte kullanılabilir ve açıkça değişken bildirimleri olarak türlenebilir.</span><span class="sxs-lookup"><span data-stu-id="6617b-134">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="6617b-135">Aşağıdaki örnek, `await foreach` her öğeyi zaman uyumsuz olarak üreten bir koleksiyonu yinelemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="6617b-135">The following example uses `await foreach` to iterate a collection that generates each element asynchronously:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach"  :::

## <a name="c-language-specification"></a><span data-ttu-id="6617b-136">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6617b-136">C# language specification</span></span>

<span data-ttu-id="6617b-137">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [foreach ifadesi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6617b-137">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="6617b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6617b-138">See also</span></span>

- [<span data-ttu-id="6617b-139">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6617b-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6617b-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6617b-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6617b-141">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6617b-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6617b-142">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="6617b-142">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="6617b-143">for deyimi</span><span class="sxs-lookup"><span data-stu-id="6617b-143">for statement</span></span>](for.md)
