---
description: foreach, in (C# Başvurusu)
title: C# foreach ifadesi
ms.date: 09/18/2020
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: ea8a6f86595348a32b707caf9782f84147fefc87
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828896"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="599b0-103">foreach, in (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="599b0-103">foreach, in (C# reference)</span></span>

<span data-ttu-id="599b0-104">`foreach`Deyimi, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, veya arabirimini uygulayan tür örneğindeki her öğe için bir deyimi veya bir deyim bloğunu yürütür:</span><span class="sxs-lookup"><span data-stu-id="599b0-104">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="1" interactive="try-dotnet-method" :::

<span data-ttu-id="599b0-105">`foreach`İfade bu türlerle sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="599b0-105">The `foreach` statement isn't limited to those types.</span></span> <span data-ttu-id="599b0-106">Bunu, aşağıdaki koşullara uyan herhangi bir türde bir örnekle kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="599b0-106">You can use it with an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="599b0-107">Bir tür, `GetEnumerator` dönüş türü Class, struct veya Interface türünde olan public parametresiz metoda sahiptir.</span><span class="sxs-lookup"><span data-stu-id="599b0-107">A type has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type.</span></span> <span data-ttu-id="599b0-108">C# 9,0 ' den başlayarak `GetEnumerator` Yöntem bir türün [genişletme yöntemi](../../programming-guide/classes-and-structs/extension-methods.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="599b0-108">Beginning with C# 9.0, the `GetEnumerator` method can be a type's [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>
- <span data-ttu-id="599b0-109">Metodun dönüş türü, `GetEnumerator` ortak `Current` özelliğine ve dönüş türü olan public parametresiz metoda sahiptir `MoveNext` <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="599b0-109">The return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="599b0-110">Aşağıdaki örnek, `foreach` <xref:System.Span%601?displayProperty=nameWithType> hiçbir arabirim uygulamayan tür örneği ile ifadesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="599b0-110">The following example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="2" :::

<span data-ttu-id="599b0-111">C# 7,3 ile başlayarak, Numaralandırıcı `Current` özelliği bir [Başvuru dönüş değeri](ref.md#reference-return-values) döndürürse ( `ref T` burada `T` bir koleksiyon öğesinin türüdür), `ref` `ref readonly` Aşağıdaki örnekte gösterildiği gibi, veya değiştiricisini içeren bir yineleme değişkeni bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="599b0-111">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of a collection element), you can declare an iteration variable with the `ref` or `ref readonly` modifier, as the following example shows:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="RefSpan" :::

<span data-ttu-id="599b0-112">C# 8,0 ' den başlayarak, `await foreach` zaman uyumsuz bir veri akışını (diğer bir deyişle, arabirimi uygulayan koleksiyon türü) kullanmak için ifadesini kullanabilirsiniz <xref:System.Collections.Generic.IAsyncEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="599b0-112">Beginning with C# 8.0, you can use the `await foreach` statement to consume an asynchronous stream of data, that is, the collection type that implements the <xref:System.Collections.Generic.IAsyncEnumerable%601> interface.</span></span> <span data-ttu-id="599b0-113">Next öğesi zaman uyumsuz olarak alındığında döngünün her yinelemesi askıya alınabilir.</span><span class="sxs-lookup"><span data-stu-id="599b0-113">Each iteration of the loop may be suspended while the next element is retrieved asynchronously.</span></span> <span data-ttu-id="599b0-114">Aşağıdaki örnek, ifadesinin nasıl kullanılacağını gösterir `await foreach` :</span><span class="sxs-lookup"><span data-stu-id="599b0-114">The following example shows how to use the `await foreach` statement:</span></span>

:::code language="csharp" source="snippets/IterationKeywordsExamples.cs" id="AwaitForeach" :::

<span data-ttu-id="599b0-115">Akış öğeleri varsayılan olarak yakalanan bağlamda işlenir.</span><span class="sxs-lookup"><span data-stu-id="599b0-115">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="599b0-116">Bağlam yakalamayı devre dışı bırakmak istiyorsanız, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> genişletme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="599b0-116">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="599b0-117">Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz model](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="599b0-117">For more information about synchronization contexts and capturing the current context, see [Consuming the Task-based asynchronous pattern](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span> <span data-ttu-id="599b0-118">Zaman uyumsuz akışlar hakkında daha fazla bilgi için [C# 8,0 'deki](../../whats-new/csharp-8.md) yenilikler makalesindeki [zaman uyumsuz akışlar](../../whats-new/csharp-8.md#asynchronous-streams) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="599b0-118">For more information about asynchronous streams, see the [Asynchronous streams](../../whats-new/csharp-8.md#asynchronous-streams) section of the [What's new in C# 8.0](../../whats-new/csharp-8.md) article.</span></span>

<span data-ttu-id="599b0-119">Deyimdeki herhangi bir noktada `foreach` , [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="599b0-119">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="599b0-120">Ayrıca `foreach` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="599b0-120">You can also exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

<span data-ttu-id="599b0-121">`foreach`İfade öğesine uygulanırsa `null` , bir oluşturulur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="599b0-121">If the `foreach` statement is applied to `null`, a <xref:System.NullReferenceException> is thrown.</span></span> <span data-ttu-id="599b0-122">Deyimin kaynak koleksiyonu `foreach` boşsa, `foreach` Döngünün gövdesi yürütülmez ve atlanır.</span><span class="sxs-lookup"><span data-stu-id="599b0-122">If the source collection of the `foreach` statement is empty, the body of the `foreach` loop isn't executed and skipped.</span></span>

## <a name="type-of-an-iteration-variable"></a><span data-ttu-id="599b0-123">Yineleme değişkeni türü</span><span class="sxs-lookup"><span data-stu-id="599b0-123">Type of an iteration variable</span></span>

<span data-ttu-id="599b0-124">`var` `foreach` Aşağıdaki kodda gösterildiği gibi, derleyicinin deyimdeki bir yineleme değişkeni türünü saymasına izin vermek için anahtar sözcüğünü kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="599b0-124">You can use the `var` keyword to let the compiler infer the type of an iteration variable in the `foreach` statement, as the following code shows:</span></span>

```csharp
foreach (var item in collection) { }
```

<span data-ttu-id="599b0-125">Aşağıdaki kodda gösterildiği gibi, bir yineleme değişkeni türünü de açıkça belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="599b0-125">You can also explicitly specify the type of an iteration variable, as the following code shows:</span></span>

```csharp
IEnumerable<T> collection = new T[5];
foreach (V item in collection) { }
```

<span data-ttu-id="599b0-126">Önceki biçimde, `T` bir koleksiyon öğesinin türü örtük olarak veya `V` bir yineleme değişkeni türüne açıkça dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="599b0-126">In the preceding form, type `T` of a collection element must be implicitly or explicitly convertible to type `V` of an iteration variable.</span></span> <span data-ttu-id="599b0-127">' Den açık bir dönüştürme `T` `V` çalışma zamanında başarısız olursa, `foreach` ifade bir oluşturur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="599b0-127">If an explicit conversion from `T` to `V` fails at run time, the `foreach` statement throws an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="599b0-128">Örneğin, `T` korumalı olmayan bir sınıf türü ise, `V` Uygulamasız olsa da herhangi bir arabirim türü olabilir `T` .</span><span class="sxs-lookup"><span data-stu-id="599b0-128">For example, if `T` is a non-sealed class type, `V` can be any interface type, even the one that `T` doesn't implement.</span></span> <span data-ttu-id="599b0-129">Çalışma zamanında, bir koleksiyon öğesinin türü, öğesinden türetilen `T` ve gerçekten uygulayan bir öğe olabilir `V` .</span><span class="sxs-lookup"><span data-stu-id="599b0-129">At run time, the type of a collection element may be the one that derives from `T` and actually implements `V`.</span></span> <span data-ttu-id="599b0-130">Böyle bir durum yoksa, bir oluşturulur <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="599b0-130">If that's not the case, an <xref:System.InvalidCastException> is thrown.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="599b0-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="599b0-131">C# language specification</span></span>

<span data-ttu-id="599b0-132">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [foreach ifadesi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="599b0-132">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="599b0-133">C# 8,0 ve üzeri sürümlerde eklenen özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:</span><span class="sxs-lookup"><span data-stu-id="599b0-133">For more information about features added in C# 8.0 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="599b0-134">Zaman uyumsuz akışlar (C# 8,0)</span><span class="sxs-lookup"><span data-stu-id="599b0-134">Async streams (C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/async-streams.md)
- [<span data-ttu-id="599b0-135">`GetEnumerator`Döngüler için uzantı desteği `foreach` (C# 9,0)</span><span class="sxs-lookup"><span data-stu-id="599b0-135">Extension `GetEnumerator` support for `foreach` loops (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/extension-getenumerator.md)

## <a name="see-also"></a><span data-ttu-id="599b0-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="599b0-136">See also</span></span>

- [<span data-ttu-id="599b0-137">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="599b0-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="599b0-138">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="599b0-138">C# keywords</span></span>](index.md)
- [<span data-ttu-id="599b0-139">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="599b0-139">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="599b0-140">for deyimi</span><span class="sxs-lookup"><span data-stu-id="599b0-140">for statement</span></span>](for.md)
