---
title: "Nasıl yapılır: Birden Çok Dizeyi Birleştirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="c076b-102">Nasıl yapılır: Birden Çok Dizeyi Birleştirme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c076b-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="c076b-103">*Birleştirme* bir dizeyi başka bir dize sonuna ekleniyor işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c076b-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="c076b-104">Ne zaman, birleştirme dize değişmez değerleri veya dize sabitleri kullanarak `+` işleci, derleyici, tek bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c076b-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="c076b-105">Hayır birleştirme oluştuğunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c076b-105">No run time concatenation occurs.</span></span> <span data-ttu-id="c076b-106">Ancak, dize değişkenleri yalnızca çalışma zamanında art arda eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c076b-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="c076b-107">Bu durumda, çeşitli yaklaşımlar performans etkilerini anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c076b-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c076b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c076b-108">Example</span></span>  
 <span data-ttu-id="c076b-109">Aşağıdaki örnek, uzun bir dize sabit değeri küçük dizeleri kaynak kodundaki okunabilirliğini artırmak için bölme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c076b-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="c076b-110">Bu bölümleri tek bir dize halinde derleme zamanında birleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c076b-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="c076b-111">Dizeleri dahil edilen sayısının maliyet zamanı performans Hayır çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="c076b-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c076b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c076b-112">Example</span></span>  
 <span data-ttu-id="c076b-113">Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri veya <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c076b-113">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c076b-114">`+` İşleci kullanımı kolay ve sezgisel kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="c076b-114">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="c076b-115">Kullandığınız olsa bile birkaç + bir deyim işleçleri, dize içeriği yalnızca bir kez kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c076b-115">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="c076b-116">Ancak bu işlem birden çok kez yineler, örneğin bir döngüde verimliliği sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c076b-116">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="c076b-117">Örneğin, aşağıdaki kodu not edin:</span><span class="sxs-lookup"><span data-stu-id="c076b-117">For example, note the following code:</span></span>  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="c076b-118">Dize birleştirme işlemleri, C# Derleyici boş bir dize aynı boş bir dize gibi davranır, ancak özgün boş bir dize değerini dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="c076b-118">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="c076b-119">Dizeleri (örneğin, bir döngü) çok sayıda birleştirme değil, bu kod performans maliyetini önemli büyük olasılıkla değil.</span><span class="sxs-lookup"><span data-stu-id="c076b-119">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="c076b-120">Aynı için doğrudur <xref:System.String.Concat%2A?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c076b-120">The same is true for the <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType> methods.</span></span>  
  
 <span data-ttu-id="c076b-121">Ancak, performansı önemli olduğu durumlarda her zaman kullanmalısınız <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c076b-121">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="c076b-122">Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> zincirleme etkisi olmadan dizeyi birleştirmek için sınıf `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="c076b-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c076b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c076b-123">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="c076b-124">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c076b-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c076b-125">Dizeleri</span><span class="sxs-lookup"><span data-stu-id="c076b-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
