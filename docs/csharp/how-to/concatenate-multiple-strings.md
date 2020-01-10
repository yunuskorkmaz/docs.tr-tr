---
title: Birden çok dizeyi birleştirme (C# kılavuz)
description: İçindeki C#dizeleri birleştirme için birden çok yol vardır. Seçenekleri ve farklı seçimlerin arkasındaki nedenleri öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713895"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="4160d-104">Birden çok dizeyi birleştirme (C# kılavuz)</span><span class="sxs-lookup"><span data-stu-id="4160d-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="4160d-105">*Birleştirme* , bir dizeyi başka bir dizenin sonuna ekleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="4160d-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="4160d-106">Dizeleri `+` işlecini kullanarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4160d-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="4160d-107">Dize sabit değerleri ve dize sabitleri için birleştirme, derleme zamanında oluşur; çalışma zamanı birleştirme gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="4160d-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="4160d-108">Dize değişkenleri için, birleştirme yalnızca çalışma zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4160d-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="4160d-109">Aşağıdaki örnek, kaynak kodda okunabilirliğini geliştirmek için bir uzun dize sabit değerini daha küçük dizelere bölmek için birleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="4160d-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="4160d-110">Bu parçalar, derleme zamanında tek bir dizeye birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4160d-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="4160d-111">Dahil edilen dizelerin sayısından bağımsız olarak, çalışma zamanı performans maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="4160d-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="4160d-112">Dize değişkenlerini birleştirmek için `+` veya `+=` işleçlerini, [dize ilişkilendirmeyi](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4160d-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4160d-113">`+` işleci kullanımı kolaydır ve sezgisel kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="4160d-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="4160d-114">Tek bir ifadede birkaç `+` işleç kullansanız bile, dize içeriği yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4160d-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="4160d-115">Aşağıdaki kod, dizeleri birleştirmek için `+` ve `+=` işleçlerini kullanma örneklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4160d-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="4160d-116">Bazı ifadelerde, aşağıdaki kodda gösterildiği gibi dize ilişkilendirmeyi kullanarak dizeleri birleştirmek daha kolay olur:</span><span class="sxs-lookup"><span data-stu-id="4160d-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="4160d-117">Dize birleştirme işlemlerinde, C# derleyici null bir dizeyi boş bir dize ile aynı şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="4160d-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="4160d-118">Dizeleri birleştirme yöntemi <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4160d-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4160d-119">Bu yöntem, az sayıda bileşen dizesinden bir dize oluştururken iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="4160d-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="4160d-120">Diğer durumlarda dizeleri bir döngüde birleştiriyor olabilirsiniz; burada, hangi kaynak dizeleri birleştirmiş olduğunuzu ve kaynak dizelerinin gerçek sayısı çok büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="4160d-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="4160d-121"><xref:System.Text.StringBuilder> sınıfı bu senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4160d-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="4160d-122">Aşağıdaki kod dizeleri birleştirmek için <xref:System.Text.StringBuilder> sınıfının <xref:System.Text.StringBuilder.Append%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4160d-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="4160d-123">[Dize bitiştirilmesi veya `StringBuilder` sınıfını seçme nedenleri](xref:System.Text.StringBuilder#StringAndSB)hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4160d-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="4160d-124">Bir koleksiyondaki dizeleri birleştirmek için başka bir seçenek de <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="4160d-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4160d-125">Kaynak dizelerin bir delikile ayrılması gerekiyorsa <xref:System.String.Join%2A?displayProperty=nameWithType> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4160d-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="4160d-126">Aşağıdaki kod her iki yöntemi kullanarak bir sözcük dizisini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="4160d-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="4160d-127">En sonda, bir koleksiyondaki dizeleri birleştirmek için [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4160d-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="4160d-128">Bu yöntem, kaynak dizelerini bir lambda ifadesi kullanarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="4160d-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="4160d-129">Lambda ifadesi, her bir dizeyi var olan birikme ekleme işini yapar.</span><span class="sxs-lookup"><span data-stu-id="4160d-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="4160d-130">Aşağıdaki örnek, dizideki her sözcük arasına bir boşluk ekleyerek bir sözcük dizisini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="4160d-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="4160d-131">Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4160d-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="4160d-132">Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4160d-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="4160d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4160d-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="4160d-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4160d-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="4160d-135">Dizeler</span><span class="sxs-lookup"><span data-stu-id="4160d-135">Strings</span></span>](../programming-guide/strings/index.md)
