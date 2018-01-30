---
title: "Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme"
description: "C# dizeyi birleştirmek için birden çok yolu vardır. Seçenekleri ve farklı seçenekler nedenler öğrenin."
ms.date: 01/11/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4bc5e04edba48065746b96841b628ec5843c5e9
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="36707-104">Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme</span><span class="sxs-lookup"><span data-stu-id="36707-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="36707-105">*Birleştirme* bir dizeyi başka bir dize sonuna ekleniyor işlemidir.</span><span class="sxs-lookup"><span data-stu-id="36707-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="36707-106">Kullanarak dizeyi birleştirme + işleci.</span><span class="sxs-lookup"><span data-stu-id="36707-106">You concatenate strings by using the + operator.</span></span> <span data-ttu-id="36707-107">Dize değişmez değerleri ve dize sabitleri için birleştirme derleme zamanında oluşur; çalışma zamanı birleştirme oluşur.</span><span class="sxs-lookup"><span data-stu-id="36707-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="36707-108">Dize değişkenleri için yalnızca çalışma zamanında birleştirme oluşur.</span><span class="sxs-lookup"><span data-stu-id="36707-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="36707-109">Aşağıdaki örnek, uzun bir dize sabit değeri küçük dizeleri kaynak kodundaki okunabilirliğini artırmak için bölmek için birleştirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="36707-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="36707-110">Bu bölümleri tek bir dize halinde derleme zamanında birleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="36707-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="36707-111">Söz konusu dizeleri sayısından bağımsız olarak hiçbir çalışma zamanı performans maliyeti yoktur.</span><span class="sxs-lookup"><span data-stu-id="36707-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="36707-112">Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri [dize ilişkilendirme](../tutorials/string-interpolation.md) veya <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="36707-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="36707-113">`+` İşleci kullanımı kolay ve sezgisel kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="36707-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="36707-114">Kullandığınız olsa bile birkaç + bir deyim işleçleri, dize içeriği yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="36707-114">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="36707-115">Aşağıdaki kodu kullanarak, iki örnek gösterilmektedir `+` dizeyi birleştirmek için işleci:</span><span class="sxs-lookup"><span data-stu-id="36707-115">The following code shows two examples of using the `+` operator to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="36707-116">Bazı ifadelerinde dize ilişkilendirme aşağıdaki kodu gösterildiği kullanarak dizeyi birleştirmek kolaydır:</span><span class="sxs-lookup"><span data-stu-id="36707-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="36707-117">Dize birleştirme işlemleri C# Derleyici boş bir dize aynı boş bir dize değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="36707-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="36707-118">Dizeyi birleştirmek için diğer yöntemler <xref:System.String.Concat%2A?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="36707-118">Other methods to concatenate strings are <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="36707-119">İyi bir dizeden bileşen dizeleri az sayıda oluştururken bu yöntemler çalışır.</span><span class="sxs-lookup"><span data-stu-id="36707-119">These methods work well when you are building a string from a small number of component strings.</span></span> <span data-ttu-id="36707-120">Birleştirilmiş dizenizi yapın dize sayısı bildiğiniz durumlarda bu methdos ayrıca harika bir seçim değildir.</span><span class="sxs-lookup"><span data-stu-id="36707-120">These methdos are also a great choice when you know the number of strings that make up your concatenated string.</span></span>

<span data-ttu-id="36707-121">Diğer durumlarda burada birleştirme kaç kaynak dizeleri tanımadığınız ve kaynak dizeleri gerçek sayısını oldukça büyük bir Döngüdeki dizelerini birleştirme.</span><span class="sxs-lookup"><span data-stu-id="36707-121">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="36707-122"><xref:System.Text.StringBuilder> Sınıfı bu senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="36707-122">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="36707-123">Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="36707-123">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="36707-124">Daha fazla bilgi edinebilirsiniz [nedenleri dize birleştirme seçin veya `StringBuilder` sınıfı](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="36707-124">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="36707-125">Bir koleksiyon dizelerden katılmak için başka bir seçenek kullanmaktır [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36707-125">Another option to join strings from a collection is to use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="36707-126">Bu yöntem bir lambda ifadesi kullanarak kaynak dizeleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="36707-126">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="36707-127">Lambda ifadesi varolan Birikme her dizesi eklemek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="36707-127">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="36707-128">Aşağıdaki örnek, dizisindeki her sözcüğün arasında bir boşluk ekleyerek sözcükler dizisi birleştirir:</span><span class="sxs-lookup"><span data-stu-id="36707-128">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a><span data-ttu-id="36707-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36707-129">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="36707-130">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="36707-130">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="36707-131">Dizeler</span><span class="sxs-lookup"><span data-stu-id="36707-131">Strings</span></span>](../programming-guide/strings/index.md)
