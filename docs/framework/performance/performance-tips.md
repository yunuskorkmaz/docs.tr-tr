---
title: .NET Performans İpuçları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.workload:
- wiwagn
ms.openlocfilehash: ac1f5b9e0897650751320a7f5a9290c378d428b6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="net-performance-tips"></a><span data-ttu-id="cbac5-102">.NET Performans İpuçları</span><span class="sxs-lookup"><span data-stu-id="cbac5-102">.NET Performance Tips</span></span>
<span data-ttu-id="cbac5-103">Terim *performans* genellikle bir program yürütme hızını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-103">The term *performance* generally refers to the execution speed of a program.</span></span> <span data-ttu-id="cbac5-104">Kaynak kodunuz temel belirli kurallarında izleyerek bazen yürütme hızını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-104">You can sometimes increase execution speed by following certain basic rules in your source code.</span></span> <span data-ttu-id="cbac5-105">Bazı programlarda kodu yakından inceleyin ve mümkün olduğunca hızlı çalıştığından emin olmak için profil oluşturucular kullanmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-105">In some programs, it is important to examine code closely and use profilers to make sure that it is running as fast as possible.</span></span> <span data-ttu-id="cbac5-106">Diğer programlarda hızlı yazılan kod çalışarak çalıştığından gibi en iyi duruma getirme gerçekleştirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-106">In other programs, you do not have to perform such optimization because the code is running acceptably fast as it is written.</span></span> <span data-ttu-id="cbac5-107">Bu makalede, bazı ortak burada performans olumsuz etkilenebilir alanları ve bunun yanı sıra ek performans konulara bağlantılar geliştirme ipuçları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-107">This article lists some common areas where performance can suffer and tips for improving it as well as links to additional performance topics.</span></span> <span data-ttu-id="cbac5-108">Planlama ve performans için ölçme hakkında daha fazla bilgi için bkz: [performans](../../../docs/framework/performance/index.md)</span><span class="sxs-lookup"><span data-stu-id="cbac5-108">For more information about planning and measuring for performance, see [Performance](../../../docs/framework/performance/index.md)</span></span>  
  
## <a name="boxing-and-unboxing"></a><span data-ttu-id="cbac5-109">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="cbac5-109">Boxing and Unboxing</span></span>  
 <span data-ttu-id="cbac5-110">En iyi değer kullanmaktan kaçınmak için bunlar burada olmalıdır durumlarda türleri çok sayıda kez, örneğin genel olmayan koleksiyon sınıfları gibi Kutulu <xref:System.Collections.ArrayList?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbac5-110">It is best to avoid using value types in situations where they must be boxed a high number of times, for example in non-generic collections classes such as <xref:System.Collections.ArrayList?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cbac5-111">Genel koleksiyonlar gibi kullanarak değer türleri kutulama önleyebilirsiniz <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbac5-111">You can avoid boxing of value types by using generic collections such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cbac5-112">Kutulama ve kutudan çıkarma pkı'ya pahalı işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-112">Boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="cbac5-113">Değer türü Kutulu, tamamen yeni bir nesne oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-113">When a value type is boxed, an entirely new object must be created.</span></span> <span data-ttu-id="cbac5-114">Basit başvuru atama en çok 20 kez daha uzun sürer.</span><span class="sxs-lookup"><span data-stu-id="cbac5-114">This can take up to 20 times longer than a simple reference assignment.</span></span> <span data-ttu-id="cbac5-115">Kutudan çıkarma, atama işleminin atama dört kez daha uzun sürebilir.</span><span class="sxs-lookup"><span data-stu-id="cbac5-115">When unboxing, the casting process can take four times as long as an assignment.</span></span> <span data-ttu-id="cbac5-116">Daha fazla bilgi için bkz: [kutulama ve kutudan çıkarma](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="cbac5-116">For more information, see [Boxing and Unboxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="strings"></a><span data-ttu-id="cbac5-117">Dizeler</span><span class="sxs-lookup"><span data-stu-id="cbac5-117">Strings</span></span>  
 <span data-ttu-id="cbac5-118">Çok sayıda dize değişkenleri birleştirmek, örneğin sıkı bir döngüde kullanın <xref:System.Text.StringBuilder?displayProperty=nameWithType> yerine C# [+ işleci](~/docs/csharp/language-reference/operators/addition-operator.md) veya Visual Basic [birleştirme işleçleri](~/docs/visual-basic/language-reference/operators/concatenation-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cbac5-118">When you concatenate a large number of string variables, for example in a tight loop, use <xref:System.Text.StringBuilder?displayProperty=nameWithType> instead of the C# [+ operator](~/docs/csharp/language-reference/operators/addition-operator.md) or the Visual Basic [Concatenation Operators](~/docs/visual-basic/language-reference/operators/concatenation-operators.md).</span></span> <span data-ttu-id="cbac5-119">Daha fazla bilgi için bkz: [nasıl yapılır: birden çok dizeyi birleştirme](../../csharp/how-to/concatenate-multiple-strings.md) ve [Visual Basic'de birleştirme işleçleri](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cbac5-119">For more information, see [How to: Concatenate Multiple Strings](../../csharp/how-to/concatenate-multiple-strings.md) and [Concatenation Operators in Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).</span></span>  
  
## <a name="destructors"></a><span data-ttu-id="cbac5-120">Yıkıcılar</span><span class="sxs-lookup"><span data-stu-id="cbac5-120">Destructors</span></span>  
 <span data-ttu-id="cbac5-121">Boş Yıkıcılar kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cbac5-121">Empty destructors should not be used.</span></span> <span data-ttu-id="cbac5-122">Bir sınıf bir yıkıcı içeriyorsa, bir giriş Finalize sıraya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cbac5-122">When a class contains a destructor, an entry is created in the Finalize queue.</span></span> <span data-ttu-id="cbac5-123">Yok Edicisi çağrıldığında atık toplayıcı sırasını işlemek üzere çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cbac5-123">When the destructor is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="cbac5-124">Yıkıcı boşsa, bu yalnızca bir performans kaybı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cbac5-124">If the destructor is empty, this simply results in a loss of performance.</span></span> <span data-ttu-id="cbac5-125">Daha fazla bilgi için bkz: [Yıkıcılar](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) ve [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="cbac5-125">For more information, see [Destructors](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) and [Object Lifetime: How Objects Are Created and Destroyed](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="cbac5-126">Diğer Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cbac5-126">Other Resources</span></span>  
  
-   [<span data-ttu-id="cbac5-127">Yönetilen kodu daha hızlı yazma: Ne şeyler maliyet bildirin</span><span class="sxs-lookup"><span data-stu-id="cbac5-127">Writing Faster Managed Code: Know What Things Cost</span></span>](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [<span data-ttu-id="cbac5-128">Yazma yüksek performanslı uygulamalar yönetilen: Öncü</span><span class="sxs-lookup"><span data-stu-id="cbac5-128">Writing High-Performance Managed Applications: A Primer</span></span>](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [<span data-ttu-id="cbac5-129">Çöp toplayıcı temel kavramları ve performans ipuçları</span><span class="sxs-lookup"><span data-stu-id="cbac5-129">Garbage Collector Basics and Performance Hints</span></span>](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [<span data-ttu-id="cbac5-130">Performans İpuçları ve püf noktaları .NET uygulamalarında</span><span class="sxs-lookup"><span data-stu-id="cbac5-130">Performance Tips and Tricks in .NET Applications</span></span>](http://go.microsoft.com/fwlink/?LinkId=99297)  

-   [<span data-ttu-id="cbac5-131">Riko Mariani'nın performans ipuçları</span><span class="sxs-lookup"><span data-stu-id="cbac5-131">Rico Mariani's Performance Tidbits</span></span>](http://go.microsoft.com/fwlink/?LinkId=115679)  

-   [<span data-ttu-id="cbac5-132">Vance Morrison'ın blogu</span><span class="sxs-lookup"><span data-stu-id="cbac5-132">Vance Morrison's Blog</span></span>](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a><span data-ttu-id="cbac5-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbac5-133">See Also</span></span>  
 [<span data-ttu-id="cbac5-134">Performans</span><span class="sxs-lookup"><span data-stu-id="cbac5-134">Performance</span></span>](../../../docs/framework/performance/index.md)  
 [<span data-ttu-id="cbac5-135">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="cbac5-135">Programming Concepts</span></span>](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [<span data-ttu-id="cbac5-136">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cbac5-136">Visual Basic Programming Guide</span></span>](../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="cbac5-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cbac5-137">C# Programming Guide</span></span>](http://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)
