---
title: foreach, in (C# Başvurusu)
ms.date: 06/29/2018
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: d3ce1122c54c14b1baf35641f28d062a2855d335
ms.sourcegitcommit: 736ec4d3e2c74895b47a0d36126657b95da383c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2018
ms.locfileid: "37140274"
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="02606-102">foreach, in (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="02606-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="02606-103">`foreach` Deyimini uygulayan türünün bir örneği bir deyim veya her öğe için deyimleri bloğu yürütür <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="02606-103">The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="02606-104">`foreach` Deyimi bu türlerde sınırlı değildir ve aşağıdaki koşulları karşılayan herhangi bir türde bir örneğine uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="02606-104">The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:</span></span>

- <span data-ttu-id="02606-105">Parametresiz ortak olan `GetEnumerator` yöntemi, dönüş türü olan sınıf, yapı veya arabirim türü</span><span class="sxs-lookup"><span data-stu-id="02606-105">has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,</span></span>
- <span data-ttu-id="02606-106">dönüş türü `GetEnumerator` yöntemi ortak olan `Current` özelliği ve parametresiz ortak `MoveNext` yöntemi, dönüş türü olan <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="02606-106">the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.</span></span>

<span data-ttu-id="02606-107">Bir oranda noktası içinde `foreach` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) deyimi ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="02606-107">At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="02606-108">Ayrıca çıkabilirsiniz bir `foreach` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="02606-108">You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="examples"></a><span data-ttu-id="02606-109">Örnekler</span><span class="sxs-lookup"><span data-stu-id="02606-109">Examples</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="02606-110">Aşağıdaki örnek kullanımını gösterir `foreach` örneği deyimiyle <xref:System.Collections.Generic.List%601> uygulayan tür <xref:System.Collections.Generic.IEnumerable%601> arabirimi:</span><span class="sxs-lookup"><span data-stu-id="02606-110">The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:</span></span>

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

<span data-ttu-id="02606-111">Sonraki örnek kullanır `foreach` örneği deyimiyle <xref:System.Span%601?displayProperty=nameWithType> arabirimlerden uygulamaz türü:</span><span class="sxs-lookup"><span data-stu-id="02606-111">The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:</span></span>

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

<span data-ttu-id="02606-112">C# ile 7.3, varsa başlayan Numaralandırıcının `Current` özelliği döndürür bir [başvuru dönüş değeri](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` burada `T` koleksiyon öğesi türü), yineleme değişkeni ile bildirebilir `ref` veya `ref readonly` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="02606-112">Beginning with C# 7.3, if the enumerator's `Current` property returns a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md) (`ref T` where `T` is the type of the collection element), you can declare the iteration variable with the `ref` or `ref readonly` modifier.</span></span> <span data-ttu-id="02606-113">Aşağıdaki örnek kullanan bir `ref` stackalloc dizideki her öğe değerini ayarlamak için yineleme değişkeni.</span><span class="sxs-lookup"><span data-stu-id="02606-113">The following example uses a `ref` iteration variable to set the value of each item in a stackalloc array.</span></span> <span data-ttu-id="02606-114">`ref readonly` Sürüm tekrarlanan tüm değerleri yazdırmak için koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="02606-114">The `ref readonly` version iterates the collection to print all the values.</span></span> <span data-ttu-id="02606-115">`readonly` Bildirimini örtük bir yerel değişken bildirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="02606-115">The `readonly` declaration uses an implicit local variable declaration.</span></span> <span data-ttu-id="02606-116">Örtük değişken bildirimleri ile birlikte kullanılabilir `ref` veya `ref readonly` açıkça gibi bildirimleri yazılan değişken bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="02606-116">Implicit variable declarations can be used with either `ref` or `ref readonly` declarations, as can explicitly typed variable declarations.</span></span>

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a><span data-ttu-id="02606-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="02606-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="02606-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02606-118">See also</span></span>

[<span data-ttu-id="02606-119">Foreach deyimi (C# dil belirtimi)</span><span class="sxs-lookup"><span data-stu-id="02606-119">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[<span data-ttu-id="02606-120">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="02606-120">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[<span data-ttu-id="02606-121">for</span><span class="sxs-lookup"><span data-stu-id="02606-121">for</span></span>](for.md)  
[<span data-ttu-id="02606-122">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="02606-122">Iteration Statements</span></span>](iteration-statements.md)  
[<span data-ttu-id="02606-123">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="02606-123">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="02606-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="02606-124">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="02606-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="02606-125">C# Programming Guide</span></span>](../../programming-guide/index.md)  
