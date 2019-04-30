---
title: C# foreach deyimi
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 417a8cefbc9bc7544ae1156992e6e6c549fb828f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661636"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="d60ca-102">foreach, (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d60ca-102">foreach, in (C# reference)</span></span>

<span data-ttu-id="d60ca-103">`foreach` Deyimi uygulayan türü örneğinde bir deyimi veya bir her öğe için bir deyimler bloğunu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d60ca-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d60ca-104">`foreach` Deyimi bu türleri için sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="d60ca-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="d60ca-105">Genel parametresiz `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü</span><span class="sxs-lookup"><span data-stu-id="d60ca-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="d60ca-106">dönüş türünü `GetEnumerator` yöntemi ortak sahip `Current` özelliği ve parametresiz public `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="d60ca-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="d60ca-107">C# 7.3, ile başlayarak Numaralandırıcı `Current` özelliği döndürür bir [başvuru dönüş değeri](ref.md#reference-return-values) (`ref T` burada `T` koleksiyon öğesi türü), yineleme değişkeni ile bildirebilirsiniz `ref` veya `ref readonly` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="d60ca-107">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](ref.md#reference-return-values) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span>

<span data-ttu-id="d60ca-108">Herhangi bir anda işaret içinde `foreach` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi veya bir sonraki yinelemesine kullanarak adım [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="d60ca-108">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="d60ca-109">Ayrıca çıkış bir `foreach` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="d60ca-109">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="d60ca-110">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d60ca-110">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="d60ca-111">Aşağıdaki örnek, kullanımını gösterir. `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan bir tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="d60ca-111">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="d60ca-112">Sonraki örnekte `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamayan türü:</span><span class="sxs-lookup"><span data-stu-id="d60ca-112">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="d60ca-113">Aşağıdaki örnekte bir `ref` bir stackalloc dizideki her öğenin değerini ayarlamak için yineleme değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d60ca-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="d60ca-114">`ref readonly` Sürüm tüm değerleri yazdırmak için koleksiyon yinelenir.</span><span class="sxs-lookup"><span data-stu-id="d60ca-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="d60ca-115">`readonly` Bildirimi örtük bir yerel değişken bildirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d60ca-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="d60ca-116">Örtük değişken bildirimleri ile birlikte kullanılabilir `ref` veya `ref readonly` açıkça mümkün olduğunca bildirimleri, yazdığınız değişken bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="d60ca-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="d60ca-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d60ca-117">C# language specification</span></span>

<span data-ttu-id="d60ca-118">Daha fazla bilgi için [foreach deyimi](~/_csharplang/spec/statements.md#the-foreach-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d60ca-118">For more information, see [The foreach statement](~/_csharplang/spec/statements.md#the-foreach-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d60ca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d60ca-119">See also</span></span>

- [<span data-ttu-id="d60ca-120">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d60ca-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d60ca-121">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d60ca-121">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d60ca-122">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d60ca-122">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d60ca-123">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="d60ca-123">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="d60ca-124">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="d60ca-124">Using foreach with arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="d60ca-125">For deyimi</span><span class="sxs-lookup"><span data-stu-id="d60ca-125">for statement</span></span>](for.md)
