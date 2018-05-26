---
title: foreach, in (C# Başvurusu)
ms.date: 05/24/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: b6b7dc0a4d3970ddfbbb6635ccebbbd5b75671e4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="c2e99-102">foreach, in (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c2e99-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="c2e99-103">`foreach` Deyimini uygulayan türünün bir örneği bir deyim veya her öğe için deyimleri bloğu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c2e99-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="c2e99-104">`foreach` Deyimi bu türlerde sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="c2e99-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="c2e99-105">Parametresiz ortak olan `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü</span><span class="sxs-lookup"><span data-stu-id="c2e99-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="c2e99-106">dönüş türü `GetEnumerator` yöntemi ortak olan `Current` özelliği ve parametresiz ortak `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="c2e99-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="c2e99-107">Bir oranda noktası içinde `foreach` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) anahtar sözcüğü ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c2e99-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span> <span data-ttu-id="c2e99-108">Ayrıca çıkabilirsiniz bir `foreach` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="c2e99-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="c2e99-109">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c2e99-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c2e99-110">Aşağıdaki örnek kullanımını gösterir `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="c2e99-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="c2e99-111">Sonraki örnek kullanır `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamaz türü:</span><span class="sxs-lookup"><span data-stu-id="c2e99-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="c2e99-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c2e99-112">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c2e99-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2e99-113">See also</span></span>

[<span data-ttu-id="c2e99-114">Foreach deyimi (C# dil belirtimi)</span><span class="sxs-lookup"><span data-stu-id="c2e99-114">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="c2e99-115">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="c2e99-115">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="c2e99-116">for</span><span class="sxs-lookup"><span data-stu-id="c2e99-116">for</span></span>](for.md)  
[<span data-ttu-id="c2e99-117">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="c2e99-117">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="c2e99-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c2e99-118">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="c2e99-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c2e99-119">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="c2e99-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c2e99-120">C# Programming Guide</span></span>](../../programming-guide/index.md)  