---
title: "foreach, in (C# Başvurusu)"
ms.date: 10/11/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5601682d53a01ff07aba7e416aa81ded4c03e4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="bcc1a-102">foreach, in (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bcc1a-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="bcc1a-103">`foreach` Deyimi bir dizi veya uygulayan bir nesne koleksiyonu her öğe için bir grup katıştırılmış ifadeler yineler <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="bcc1a-104">`foreach` Deyimi istiyor, ancak öğe eklemek veya beklenmeyen yan etkileri önlemek için kaynak koleksiyondan kaldırmak için kullanılamaz bilgileri almak için koleksiyon yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="bcc1a-105">Gerekirse eklemek veya kaynak koleksiyondan öğeleri, kullanmak bir [için](for.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="bcc1a-106">Katıştırılmış ifadeler dizisi ya da koleksiyonu her öğe için yürütme devam edin.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="bcc1a-107">Koleksiyondaki tüm öğeler için yineleme tamamladıktan sonra sonraki deyimi aşağıdaki denetimi aktarılır `foreach` bloğu.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="bcc1a-108">Bir oranda noktası içinde `foreach` bloğu kullanarak döngü dışında bölünebilir [sonu](break.md) anahtar sözcüğü ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="bcc1a-109">A `foreach` döngü ayrıca çıkıldı tarafından [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="bcc1a-110">Hakkında daha fazla bilgi için `foreach` anahtar sözcüğü ve kodu örnekleri, aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bcc1a-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="bcc1a-111">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="bcc1a-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="bcc1a-112">Nasıl yapılır: foreach ile koleksiyon sınıfına erişme</span><span class="sxs-lookup"><span data-stu-id="bcc1a-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="bcc1a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="bcc1a-113">Example</span></span>
 <span data-ttu-id="bcc1a-114">Aşağıdaki kod üç örnekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-114">The following code shows three examples.</span></span>

> [!TIP]
> <span data-ttu-id="bcc1a-115">Sözdizimiyle denemek ve kullanım örneğine daha benzer farklı kullanımları denemek için örnekler değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="bcc1a-116">Kodu çalıştırmak için "Çalıştır" tuşlarına basın, sonra düzenleme ve basın "yeniden çalıştır".</span><span class="sxs-lookup"><span data-stu-id="bcc1a-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="bcc1a-117">Tipik bir `foreach` dizisi içeriğini görüntüler döngüsü</span><span class="sxs-lookup"><span data-stu-id="bcc1a-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="bcc1a-118">bir [için](../../../csharp/language-reference/keywords/for.md) aynı şeyi yapar döngüsü</span><span class="sxs-lookup"><span data-stu-id="bcc1a-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="bcc1a-119">bir `foreach` dizideki öğelerin sayısını tutar döngüsü</span><span class="sxs-lookup"><span data-stu-id="bcc1a-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="bcc1a-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="bcc1a-120">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bcc1a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bcc1a-121">See Also</span></span>  

[<span data-ttu-id="bcc1a-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bcc1a-122">C# Reference</span></span>](../index.md)

[<span data-ttu-id="bcc1a-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bcc1a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="bcc1a-124">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="bcc1a-124">C# Keywords</span></span>](index.md)

[<span data-ttu-id="bcc1a-125">Yineleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="bcc1a-125">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="bcc1a-126">için</span><span class="sxs-lookup"><span data-stu-id="bcc1a-126">for</span></span>](for.md)
