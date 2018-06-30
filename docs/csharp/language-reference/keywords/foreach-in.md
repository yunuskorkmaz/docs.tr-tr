---
title: foreach, in (C# Başvurusu)
ms.date: 06/28/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: e4b5ba6fb97d82d2b6f03e77995b9d3c2b9d68c6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104422"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="ed2f3-102">foreach, in (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ed2f3-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="ed2f3-103">`foreach` Deyimini uygulayan türünün bir örneği bir deyim veya her öğe için deyimleri bloğu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="ed2f3-104">`foreach` Deyimi bu türlerde sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="ed2f3-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="ed2f3-105">Parametresiz ortak olan `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü</span><span class="sxs-lookup"><span data-stu-id="ed2f3-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="ed2f3-106">dönüş türü `GetEnumerator` yöntemi ortak olan `Current` özelliği ve parametresiz ortak `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="ed2f3-107">Bir oranda noktası içinde `foreach` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) deyimi ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ed2f3-108">Ayrıca çıkabilirsiniz bir `foreach` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="ed2f3-109">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ed2f3-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="ed2f3-110">Aşağıdaki örnek kullanımını gösterir `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="ed2f3-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="ed2f3-111">Sonraki örnek kullanır `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamaz türü:</span><span class="sxs-lookup"><span data-stu-id="ed2f3-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="ed2f3-112">C# 7.3 ile başlayarak, ne zaman koleksiyon türünü destekler `ref` erişim öğeleri için yineleme değişkeni ile bildirebilir `ref` veya `ref readonly` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-112">Beginning with C# 7.3, when the collection type supports `ref` access to its elements, you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="ed2f3-113">Aşağıdaki örnek kullanan bir `ref` stackalloc dizideki her öğe değerini ayarlamak için yineleme değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="ed2f3-114">`ref readonly` Sürüm tekrarlanan tüm değerleri yazdırmak için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="ed2f3-115">`readonly` Bildirimini örtük bir yerel değişken bildirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="ed2f3-116">Örtük değişken bildirimleri ile birlikte kullanılabilir `ref` veya `ref readonly` açıkça gibi bildirimleri yazılan değişken bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp-interactive[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="ed2f3-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ed2f3-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ed2f3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed2f3-118">See also</span></span>

[<span data-ttu-id="ed2f3-119">Foreach deyimi (C# dil belirtimi)</span><span class="sxs-lookup"><span data-stu-id="ed2f3-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="ed2f3-120">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="ed2f3-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="ed2f3-121">for</span><span class="sxs-lookup"><span data-stu-id="ed2f3-121">for</span></span>](for.md)  
[<span data-ttu-id="ed2f3-122">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="ed2f3-122">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="ed2f3-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ed2f3-123">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="ed2f3-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ed2f3-124">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="ed2f3-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ed2f3-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  