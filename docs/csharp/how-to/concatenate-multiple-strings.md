---
title: Birden çok dize nasıl işlenir (C# Guide)
description: C#'da dizeleri birleştirmeye birden çok yol vardır. Seçenekleri ve farklı seçeneklerin arkasındaki nedenleri öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 87ec5104f36d0c6cce12037e70dacf2752ef5e62
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121045"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="42b46-104">Birden çok dize nasıl işlenir (C# Guide)</span><span class="sxs-lookup"><span data-stu-id="42b46-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="42b46-105">*Birleştirme,* bir dizeyi başka bir dizesonuna bağlama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="42b46-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="42b46-106">`+` İşleç kullanarak dizeleri birleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="42b46-107">Dize literals ve dize sabitleri için, concatenation derleme zamanda oluşur; çalışma zamanı bir araya gelme gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="42b46-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="42b46-108">Dize değişkenleri için, concatenation yalnızca çalışma zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="42b46-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="42b46-109">Aşağıdaki örnek, kaynak kodundaki okunabilirliği artırmak için uzun bir dize edebi sini daha küçük dizeleri bölmek için yapılan bir araya getiriyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="42b46-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="42b46-110">Bu parçalar derleme zamanda tek bir dize içine sıkıştırılır.</span><span class="sxs-lookup"><span data-stu-id="42b46-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="42b46-111">İlgili dizeleri sayısıne bakılmaksızın çalışma zamanı performans maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="42b46-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="42b46-112">Dize değişkenlerini birleştirmek için, `+` veya `+=` işleçleri, [dize enterpolasyonunu](../language-reference/tokens/interpolated.md) <xref:System.String.Format%2A?displayProperty=nameWithType>veya yöntemleri <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="42b46-113">Operatör `+` kullanımı kolaydır ve sezgisel kod için yapar.</span><span class="sxs-lookup"><span data-stu-id="42b46-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="42b46-114">Bir deyimde `+` birden fazla işleç kullansanız bile, dize içeriği yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="42b46-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="42b46-115">Aşağıdaki kod, dizeleri `+` birleştirmek için ve `+=` işleçleri kullanma örneklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="42b46-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="42b46-116">Bazı ifadelerde, aşağıdaki kodun gösterdiği gibi dize enterpolasyonu kullanarak dizeleri birleştirmek daha kolaydır:</span><span class="sxs-lookup"><span data-stu-id="42b46-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="42b46-117">Dize ayırma işlemlerinde, C# derleyicisi boş bir dize yle aynı null dizeyi ele alır.</span><span class="sxs-lookup"><span data-stu-id="42b46-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="42b46-118">Dizeleri birleştirmeye başka bir <xref:System.String.Format%2A?displayProperty=nameWithType>yöntem de .</span><span class="sxs-lookup"><span data-stu-id="42b46-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="42b46-119">Bu yöntem, az sayıda bileşen dizesinden bir dize oluşturuyorsanız iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="42b46-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="42b46-120">Diğer durumlarda dizeleri, kaç kaynak dizesini birleştirdiğinizi bilmediğiniz ve gerçek kaynak dizeleri sayısının oldukça büyük olabileceği bir döngüde birleştiriyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="42b46-121">Sınıf <xref:System.Text.StringBuilder> bu senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="42b46-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="42b46-122">Aşağıdaki kod dizeleri birleştirmek için sınıfın <xref:System.Text.StringBuilder.Append%2A> yöntemini <xref:System.Text.StringBuilder> kullanır.</span><span class="sxs-lookup"><span data-stu-id="42b46-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="42b46-123">[Dize concatenation veya sınıf seçmek için `StringBuilder` nedenler](xref:System.Text.StringBuilder#StringAndSB)hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="42b46-124">Bir koleksiyondan dizeleri birleştirmek için <xref:System.String.Concat%2A?displayProperty=nameWithType> başka bir seçenek yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="42b46-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="42b46-125">Kaynak <xref:System.String.Join%2A?displayProperty=nameWithType> dizeleri bir delimetre ile ayrılmış olmalıdır yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="42b46-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="42b46-126">Aşağıdaki kod, her iki yöntemi kullanarak bir sözcük dizisini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="42b46-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="42b46-127">Sonunda, bir koleksiyondan dizeleri <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> birleştirmek için [LINQ](../programming-guide/concepts/linq/index.md) ve yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="42b46-128">Bu yöntem, bir lambda ifadesi kullanarak kaynak dizeleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="42b46-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="42b46-129">Lambda ifadesi, her dizeyi varolan birikime eklemek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="42b46-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="42b46-130">Aşağıdaki örnek, dizideki her sözcük arasına bir boşluk ekleyerek bir sözcük dizisini birleştirir:</span><span class="sxs-lookup"><span data-stu-id="42b46-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="42b46-131">Örnek [koduna](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)bakarak bu örnekleri deneyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-131">You can try these samples by looking at the [sample code](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="42b46-132">Veya, bir zip [dosyası olarak](../../../samples/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42b46-132">Or, you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="42b46-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42b46-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="42b46-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="42b46-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="42b46-135">Dizeler</span><span class="sxs-lookup"><span data-stu-id="42b46-135">Strings</span></span>](../programming-guide/strings/index.md)
