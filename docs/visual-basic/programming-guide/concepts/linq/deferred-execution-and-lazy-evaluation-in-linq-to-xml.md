---
title: "Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a465c4448157505a42db57202298cb18e44a562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a><span data-ttu-id="b1327-102">Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1327-102">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="b1327-103">Sorgu ve eksen işlemleri genellikle ertelenmiş yürütme kullanmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b1327-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="b1327-104">Bu konuda, ertelenmiş yürütme ve bazı uygulama konuları avantajları ve gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1327-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="b1327-105">Ertelenmiş Yürütme</span><span class="sxs-lookup"><span data-stu-id="b1327-105">Deferred Execution</span></span>  
 <span data-ttu-id="b1327-106">Bir ifadenin değerlendirmesine kadar Gecikmeli yürütme anlamına gelir ertelenmiş kendi *gerçekleşen* değeri gerçekte gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b1327-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="b1327-107">Bir dizi zincirleme sorguları ya da işlemeleri içeren programlarda özellikle büyük veri koleksiyonları yönlendirme olduğunda ertelenmiş yürütme önemli ölçüde performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b1327-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="b1327-108">En iyi durumda yalnızca tek bir yineleme kaynak koleksiyonu aracılığıyla ertelenmiş yürütme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1327-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="b1327-109">LINQ teknolojileri ertelenmiş yürütme kapsamlı kullanımını her iki çekirdek üyelerinde olun <xref:System.Linq?displayProperty=nameWithType> sınıfları ve çeşitli LINQ ad alanlarında genişletme yöntemleri gibi <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1327-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=nameWithType> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="b1327-110">İstekli vs. Geç değerlendirme</span><span class="sxs-lookup"><span data-stu-id="b1327-110">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="b1327-111">Ertelenmiş yürütme uygulayan bir yöntem yazdığınızda, ayrıca geç değerlendirme veya istekli değerlendirme kullanarak yöntemini uygulamak karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1327-111">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="b1327-112">İçinde *geç değerlendirme*, tek bir öğeye kaynak koleksiyonunun yineleyici yapılan her çağrı sırasında işlenir.</span><span class="sxs-lookup"><span data-stu-id="b1327-112">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="b1327-113">Bu, hangi yineleyiciler uygulanan tipik yoludur.</span><span class="sxs-lookup"><span data-stu-id="b1327-113">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="b1327-114">İçinde *istekli değerlendirme*, yineleyici ilk çağrıda işlenmekte olan tüm koleksiyonunda neden olur.</span><span class="sxs-lookup"><span data-stu-id="b1327-114">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="b1327-115">Kaynak koleksiyonu geçici bir kopyasını de gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1327-115">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="b1327-116">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi sahip ilk öğe döndürmeden önce tüm koleksiyon sıralamak.</span><span class="sxs-lookup"><span data-stu-id="b1327-116">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="b1327-117">Ek görevlerin işlenmesi koleksiyon Değerlendirme boyunca eşit olarak dağıtır ve geçici verileri kullanımını en aza indirir çünkü geç değerlendirme genellikle daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1327-117">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="b1327-118">Elbette, bazı işlemler için Ara sonuçların gerçekleştirmeye üzere daha diğer bir seçenek yoktur.</span><span class="sxs-lookup"><span data-stu-id="b1327-118">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b1327-119">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b1327-119">Next Steps</span></span>  
 <span data-ttu-id="b1327-120">Bu öğreticide sonraki konu ertelenmiş yürütme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b1327-120">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="b1327-121">Ertelenmiş yürütme örneği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1327-121">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="b1327-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1327-122">See Also</span></span>  
 [<span data-ttu-id="b1327-123">Öğretici: Ertelenmiş yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1327-123">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [<span data-ttu-id="b1327-124">Kavramları ve terminolojiyi (işlev dönüştürme) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1327-124">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [<span data-ttu-id="b1327-125">Toplama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1327-125">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
