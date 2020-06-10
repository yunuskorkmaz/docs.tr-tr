---
title: Birden çok dizeyi birleştirme (C# Kılavuzu)
description: C# dilinde dizeleri birleştirmek için birden çok yol vardır. Seçenekleri ve farklı seçimlerin arkasındaki nedenleri öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: ef3d79c5b40d08cb76e58eba1c8831c468fd1fc0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663024"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="1caa9-104">Birden çok dizeyi birleştirme (C# Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1caa9-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="1caa9-105">*Birleştirme* , bir dizeyi başka bir dizenin sonuna ekleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="1caa9-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="1caa9-106">İşlecini kullanarak dizeleri birleştirebilirsiniz `+` .</span><span class="sxs-lookup"><span data-stu-id="1caa9-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="1caa9-107">Dize sabit değerleri ve dize sabitleri için birleştirme, derleme zamanında oluşur; çalışma zamanı birleştirme gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="1caa9-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="1caa9-108">Dize değişkenleri için, birleştirme yalnızca çalışma zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1caa9-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="1caa9-109">Aşağıdaki örnek, kaynak kodda okunabilirliğini geliştirmek için bir uzun dize sabit değerini daha küçük dizelere bölmek için birleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="1caa9-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="1caa9-110">Bu parçalar, derleme zamanında tek bir dizeye birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1caa9-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="1caa9-111">Dahil edilen dizelerin sayısından bağımsız olarak, çalışma zamanı performans maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="1caa9-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

<span data-ttu-id="1caa9-112">Dize değişkenlerini birleştirmek için, `+` veya `+=` işleçlerini, [dize ilişkilendirmeyi](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType> , <xref:System.String.Concat%2A?displayProperty=nameWithType> ya da yöntemlerini kullanabilirsiniz <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1caa9-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="1caa9-113">`+`İşleci kullanımı kolaydır ve sezgisel kod sunar.</span><span class="sxs-lookup"><span data-stu-id="1caa9-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="1caa9-114">`+`Tek bir ifadede birkaç işleç kullansanız bile, dize içeriği yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1caa9-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="1caa9-115">Aşağıdaki kod `+` `+=` dizeleri birleştirmek için ve işleçlerini kullanma örneklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="1caa9-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

<span data-ttu-id="1caa9-116">Bazı ifadelerde, aşağıdaki kodda gösterildiği gibi dize ilişkilendirmeyi kullanarak dizeleri birleştirmek daha kolay olur:</span><span class="sxs-lookup"><span data-stu-id="1caa9-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> <span data-ttu-id="1caa9-117">Dize birleştirme işlemlerinde, C# derleyicisi boş bir dizeyi boş bir dizeyle aynı şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="1caa9-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="1caa9-118">Dizeleri birleştirme yöntemi <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1caa9-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1caa9-119">Bu yöntem, az sayıda bileşen dizesinden bir dize oluştururken iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="1caa9-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="1caa9-120">Diğer durumlarda, dizeleri birleşik olarak kaç tane kaynak dizesi birleştirmiş olduğunuzu ve kaynak dizelerinin gerçek sayısını bildiğiniz bir döngüde birleştiriyorsunuz olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1caa9-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="1caa9-121"><xref:System.Text.StringBuilder>Sınıfı bu senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1caa9-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="1caa9-122">Aşağıdaki kod, <xref:System.Text.StringBuilder.Append%2A> <xref:System.Text.StringBuilder> dizeleri birleştirmek için sınıfının yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1caa9-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

<span data-ttu-id="1caa9-123">[Dize birleştirme veya `StringBuilder` sınıf seçme nedenleri](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types)hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1caa9-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span></span>

<span data-ttu-id="1caa9-124">Bir koleksiyondaki dizeleri birleştirmek için başka bir seçenek <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1caa9-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1caa9-125"><xref:System.String.Join%2A?displayProperty=nameWithType>Kaynak dizelerin bir sınırlayıcı ile ayrılması gerekiyorsa yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1caa9-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="1caa9-126">Aşağıdaki kod her iki yöntemi kullanarak bir sözcük dizisini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="1caa9-126">The following code combines an array of words using both methods:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

<span data-ttu-id="1caa9-127">Son olarak, [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> yöntemini bir koleksiyondaki dizeleri birleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1caa9-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="1caa9-128">Bu yöntem, kaynak dizelerini bir lambda ifadesi kullanarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1caa9-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="1caa9-129">Lambda ifadesi, her bir dizeyi var olan birikme ekleme işini yapar.</span><span class="sxs-lookup"><span data-stu-id="1caa9-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="1caa9-130">Aşağıdaki örnek, dizideki her sözcük arasına bir boşluk ekleyerek bir sözcük dizisini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="1caa9-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a><span data-ttu-id="1caa9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1caa9-131">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="1caa9-132">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1caa9-132">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="1caa9-133">Dizeler</span><span class="sxs-lookup"><span data-stu-id="1caa9-133">Strings</span></span>](../programming-guide/strings/index.md)
