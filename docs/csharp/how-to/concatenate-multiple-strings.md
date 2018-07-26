---
title: 'Nasıl yapılır: (C# Kılavuzu) birden çok dizeyi birleştirme'
description: C# dizeyi birleştirmek için birden çok yolu vardır. Seçenekleri ve farklı seçenekler ardındaki nedenler öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: d4e57347a11b804f3ea7f4bb9736c134c4b71929
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961319"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="c4893-104">Nasıl yapılır: (C# Kılavuzu) birden çok dizeyi birleştirme</span><span class="sxs-lookup"><span data-stu-id="c4893-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="c4893-105">*Birleştirme* bir dizenin başka bir dizenin sonuna ekleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c4893-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="c4893-106">Kullanarak dizeleri birleştirme `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="c4893-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="c4893-107">Dize değişmez değerleri ve dize sabitleri için derleme zamanında birleştirme oluşur; hiçbir çalışma zamanı birleştirme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c4893-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="c4893-108">Dize değişkenleri için yalnızca çalışma zamanında birleştirme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c4893-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c4893-109">Aşağıdaki örnek, uzun bir dize sabit değeri daha küçük dizelere kaynak kodunda okunabilirliği artırmak için bölmek için birleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4893-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="c4893-110">Bu bölümleri tek bir dize olarak derleme zamanında bitiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c4893-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="c4893-111">İlgili dizeleri sayısından bağımsız olarak hiçbir çalışma zamanı performans maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="c4893-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="c4893-112">Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri [dize ilişkilendirme](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c4893-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c4893-113">`+` İşleci kullanımı kolay ve sezgisel kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4893-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="c4893-114">Birkaç kullanıyor olsanız bile `+` bir ifade, dize içerik işleci yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c4893-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="c4893-115">Aşağıdaki kod örnekleri kullanarak gösterir `+` ve `+=` dizeyi birleştirmek için işleçleri:</span><span class="sxs-lookup"><span data-stu-id="c4893-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="c4893-116">Bazı ifadeler dize ilişkilendirme, aşağıdaki kodun gösterdiği gibi kullanarak dizeyi birleştirmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="c4893-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="c4893-117">Dize birleştirme işlemleri, C# derleyicisi boş bir dize aynı boş bir dize değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c4893-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="c4893-118">Dizeleri birleştirmek için başka bir yöntem olan <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4893-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4893-119">Bu yöntem, iyi bir dizeden çok az sayıda bileşen dizeleri oluştururken çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4893-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="c4893-120">Diğer durumlarda, burada, birleştirme kaç kaynak dizeleri bilmiyorum ve kaynak dizeleri gerçek sayısı oldukça büyük bir döngüde dizelerini birleştirme.</span><span class="sxs-lookup"><span data-stu-id="c4893-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="c4893-121"><xref:System.Text.StringBuilder> Sınıfı, bu senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4893-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="c4893-122">Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c4893-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="c4893-123">Daha fazla bilgi edinebilirsiniz [nedenleri dize birleştirme seçin veya `StringBuilder` sınıfı](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="c4893-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="c4893-124">Dizeleri bir koleksiyondan katılmak için başka bir seçenek kullanmaktır <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4893-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c4893-125">Kullanım <xref:System.String.Join%2A?displayProperty=nameWithType> kaynak dizeleri bir sınırlayıcılarla ayrılmalıdır varsa yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4893-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="c4893-126">Aşağıdaki kod bir kelimelerin iki yöntemi kullanarak dizi birleştirir:</span><span class="sxs-lookup"><span data-stu-id="c4893-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="c4893-127">En son olarak, kullanabileceğiniz [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> dizeleri bir koleksiyondan katılmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c4893-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="c4893-128">Bu yöntem, lambda ifadesi kullanarak kaynak dizeleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c4893-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="c4893-129">Lambda ifadesi için mevcut birikmesi her dize eklemek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4893-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="c4893-130">Aşağıdaki örnekte, dizideki her bir sözcüğün arasına bir boşluk ekleyerek bir kelimelerin dizi birleştirir:</span><span class="sxs-lookup"><span data-stu-id="c4893-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="c4893-131">Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="c4893-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="c4893-132">Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="c4893-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4893-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4893-133">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="c4893-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4893-134">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="c4893-135">Dizeler</span><span class="sxs-lookup"><span data-stu-id="c4893-135">Strings</span></span>](../programming-guide/strings/index.md)
