---
title: 'Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme'
description: C# dizeyi birleştirmek için birden çok yolu vardır. Seçenekleri ve farklı seçenekler nedenler öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: d4e57347a11b804f3ea7f4bb9736c134c4b71929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213252"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="35ad1-104">Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme</span><span class="sxs-lookup"><span data-stu-id="35ad1-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="35ad1-105">*Birleştirme* bir dizeyi başka bir dize sonuna ekleniyor işlemidir.</span><span class="sxs-lookup"><span data-stu-id="35ad1-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="35ad1-106">Kullanarak dizeyi birleştirme `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="35ad1-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="35ad1-107">Dize değişmez değerleri ve dize sabitleri için birleştirme derleme zamanında oluşur; çalışma zamanı birleştirme oluşur.</span><span class="sxs-lookup"><span data-stu-id="35ad1-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="35ad1-108">Dize değişkenleri için yalnızca çalışma zamanında birleştirme oluşur.</span><span class="sxs-lookup"><span data-stu-id="35ad1-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="35ad1-109">Aşağıdaki örnek, uzun bir dize sabit değeri küçük dizeleri kaynak kodundaki okunabilirliğini artırmak için bölmek için birleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="35ad1-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="35ad1-110">Bu bölümleri tek bir dize halinde derleme zamanında birleşir.</span><span class="sxs-lookup"><span data-stu-id="35ad1-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="35ad1-111">Söz konusu dizeleri sayısından bağımsız olarak hiçbir çalışma zamanı performans maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="35ad1-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="35ad1-112">Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri [dize ilişkilendirme](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="35ad1-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="35ad1-113">`+` İşleci kullanımı kolay ve sezgisel kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="35ad1-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="35ad1-114">Birkaç kullanmak olsa bile `+` bir deyim, içerik dizesi işleçleri yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="35ad1-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="35ad1-115">Aşağıdaki kod kullanma örnekleri gösterir `+` ve `+=` dizeyi birleştirmek için işleçler:</span><span class="sxs-lookup"><span data-stu-id="35ad1-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="35ad1-116">Bazı ifadelerinde dize ilişkilendirme aşağıdaki kodu gösterildiği kullanarak dizeyi birleştirmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="35ad1-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="35ad1-117">Dize birleştirme işlemleri C# Derleyici boş bir dize aynı boş bir dize değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="35ad1-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="35ad1-118">Dizeyi birleştirmek için başka bir yöntem olduğu <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35ad1-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35ad1-119">Bu yöntem, iyi bir dizeden bileşen dizeleri az sayıda oluştururken çalışır.</span><span class="sxs-lookup"><span data-stu-id="35ad1-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="35ad1-120">Diğer durumlarda burada birleştirme kaç kaynak dizeleri tanımadığınız ve kaynak dizeleri gerçek sayısını oldukça büyük bir Döngüdeki dizelerini birleştirme.</span><span class="sxs-lookup"><span data-stu-id="35ad1-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="35ad1-121"><xref:System.Text.StringBuilder> Sınıfı bu senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="35ad1-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="35ad1-122">Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="35ad1-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="35ad1-123">Daha fazla bilgi edinebilirsiniz [nedenleri dize birleştirme seçin veya `StringBuilder` sınıfı](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="35ad1-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="35ad1-124">Bir koleksiyon dizelerden katılmak için başka bir seçenek kullanmaktır <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35ad1-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="35ad1-125">Kullanım <xref:System.String.Join%2A?displayProperty=nameWithType> kaynak dizeleri delimeter tarafından ayrılmış olması durumunda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35ad1-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="35ad1-126">Aşağıdaki kod iki yöntemi kullanarak sözcükleri dizisi birleştirir:</span><span class="sxs-lookup"><span data-stu-id="35ad1-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="35ad1-127">En son olarak, kullanabileceğiniz [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> koleksiyonu dizelerden katılmaya yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35ad1-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="35ad1-128">Bu yöntem bir lambda ifadesi kullanarak kaynak dizeleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="35ad1-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="35ad1-129">Lambda ifadesi varolan Birikme her dizesi eklemek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="35ad1-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="35ad1-130">Aşağıdaki örnek, dizisindeki her sözcüğün arasında bir boşluk ekleyerek sözcükler dizisi birleştirir:</span><span class="sxs-lookup"><span data-stu-id="35ad1-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="35ad1-131">Kodda bakarak bu örnekleri deneyebilirsiniz bizim [GitHub deposunu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="35ad1-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="35ad1-132">Veya örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="35ad1-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="35ad1-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35ad1-133">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="35ad1-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="35ad1-134">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="35ad1-135">Dizeler</span><span class="sxs-lookup"><span data-stu-id="35ad1-135">Strings</span></span>](../programming-guide/strings/index.md)
