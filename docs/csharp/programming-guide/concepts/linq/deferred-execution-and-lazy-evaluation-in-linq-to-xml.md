---
title: "Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 847d8f830c26f54521664accc4bf569f822f255a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="0bbd9-102">Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0bbd9-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="0bbd9-103">Sorgu ve eksen işlemleri genellikle ertelenmiş yürütme kullanmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="0bbd9-104">Bu konuda, ertelenmiş yürütme ve bazı uygulama konuları avantajları ve gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="0bbd9-105">Ertelenmiş Yürütme</span><span class="sxs-lookup"><span data-stu-id="0bbd9-105">Deferred Execution</span></span>  
 <span data-ttu-id="0bbd9-106">Bir ifadenin değerlendirmesine kadar Gecikmeli yürütme anlamına gelir ertelenmiş kendi *gerçekleşen* değeri gerçekte gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="0bbd9-107">Bir dizi zincirleme sorguları ya da işlemeleri içeren programlarda özellikle büyük veri koleksiyonları yönlendirme olduğunda ertelenmiş yürütme önemli ölçüde performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="0bbd9-108">En iyi durumda yalnızca tek bir yineleme kaynak koleksiyonu aracılığıyla ertelenmiş yürütme sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="0bbd9-109">LINQ teknolojileri ertelenmiş yürütme kapsamlı kullanımını her iki çekirdek üyelerinde olun <xref:System.Linq?displayProperty=nameWithType> sınıfları ve çeşitli LINQ ad alanlarında genişletme yöntemleri gibi <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0bbd9-110">Ertelenmiş yürütme C# dili tarafından doğrudan içinde desteklenir [verim](../../../../csharp/language-reference/keywords/yield.md) anahtar sözcüğü (biçiminde `yield-return` deyimi) yineleyici bloğu içinde kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-110">Deferred execution is supported directly in the C# language by the [yield](../../../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="0bbd9-111">Bu tür bir yineleyici türü koleksiyonu döndürmelidir <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> (veya türetilmiş bir tür).</span><span class="sxs-lookup"><span data-stu-id="0bbd9-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="0bbd9-112">İstekli vs. Geç değerlendirme</span><span class="sxs-lookup"><span data-stu-id="0bbd9-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="0bbd9-113">Ertelenmiş yürütme uygulayan bir yöntem yazdığınızda, ayrıca geç değerlendirme veya istekli değerlendirme kullanarak yöntemini uygulamak karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="0bbd9-114">İçinde *geç değerlendirme*, tek bir öğeye kaynak koleksiyonunun yineleyici yapılan her çağrı sırasında işlenir.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="0bbd9-115">Bu, hangi yineleyiciler uygulanan tipik yoludur.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-115">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="0bbd9-116">İçinde *istekli değerlendirme*, yineleyici ilk çağrıda işlenmekte olan tüm koleksiyonunda neden olur.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="0bbd9-117">Kaynak koleksiyonu geçici bir kopyasını de gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="0bbd9-118">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi sahip ilk öğe döndürmeden önce tüm koleksiyon sıralamak.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="0bbd9-119">Ek görevlerin işlenmesi koleksiyon Değerlendirme boyunca eşit olarak dağıtır ve geçici verileri kullanımını en aza indirir çünkü geç değerlendirme genellikle daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="0bbd9-120">Elbette, bazı işlemler için Ara sonuçların gerçekleştirmeye üzere daha diğer bir seçenek yoktur.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0bbd9-121">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0bbd9-121">Next Steps</span></span>  
 <span data-ttu-id="0bbd9-122">Bu öğreticide sonraki konu ertelenmiş yürütme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="0bbd9-123">Ertelenmiş yürütme örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="0bbd9-123">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="0bbd9-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-124">See Also</span></span>  
 [<span data-ttu-id="0bbd9-125">Öğretici: Sorguları birlikte (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="0bbd9-125">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)  
 [<span data-ttu-id="0bbd9-126">Kavramları ve terminolojiyi (işlev dönüştürme) (C#)</span><span class="sxs-lookup"><span data-stu-id="0bbd9-126">Concepts and Terminology (Functional Transformation) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="0bbd9-127">Toplama işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0bbd9-127">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
 [<span data-ttu-id="0bbd9-128">uyarı simgesi</span><span class="sxs-lookup"><span data-stu-id="0bbd9-128">yield</span></span>](../../../../csharp/language-reference/keywords/yield.md)
