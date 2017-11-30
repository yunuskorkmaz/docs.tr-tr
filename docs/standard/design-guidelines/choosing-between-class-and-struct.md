---
title: "Sınıf ve yapı arasında seçim yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6659853e9c410ece3233cfa630c9066303a871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="a49ef-102">Sınıf ve yapı arasında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="a49ef-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="a49ef-103">Her framework Tasarımcısı bakarken temel tasarım kararlarından biri bir türü (bir başvuru türü) bir sınıf veya yapı (bir değer türü) olarak tasarlamanız verilip biridir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="a49ef-104">Başvuru türleri ve değer türlerini davranış farklılıkları iyi anlaşılmasını, bu seçenek yaparken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="a49ef-105">İlk yığın biz başvuru türleri değer türleri ya yığında ayrılan veya içeren içinde satır içi türleri ve ne zaman serbest ancak yığında ayrılmış ve atık toplanan olmasıdır değerlendirir değer türleri ve başvuru türleri arasında fark unwinds veya ne zaman, içeren türde serbest.</span><span class="sxs-lookup"><span data-stu-id="a49ef-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="a49ef-106">Bu nedenle, genel ayırma ve başvuru türleri ayırma kaldırma işlemleri ucuz ayırma ve değer türlerini ayırma kaldırma işlemleri altındadır.</span><span class="sxs-lookup"><span data-stu-id="a49ef-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="a49ef-107">Ardından, başvuru türleri bir dizi genişletme öğeleri olan bir dizi anlamı satır sonu, öbek üzerinde bulunan başvuru türündeki örneklerin yalnızca başvurular tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="a49ef-108">Değer türü diziler satır içi dizi öğeleri değer türü gerçek örneklerini olduğu anlamına gelir, ayrılır.</span><span class="sxs-lookup"><span data-stu-id="a49ef-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="a49ef-109">Bu nedenle, ayırma ve ayırma kaldırma işlemleri değer türü dizi ayırma ve başvuru türü dizi ayırma kaldırma işlemleri ucuz.</span><span class="sxs-lookup"><span data-stu-id="a49ef-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="a49ef-110">Ayrıca, çoğu durumda değer türü diziler kadar daha iyi yere göre başvuru sergiler.</span><span class="sxs-lookup"><span data-stu-id="a49ef-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="a49ef-111">Sonraki fark bellek kullanımı ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="a49ef-112">Değer türleri, ne zaman bir başvuru türü veya uyguladıkları arabirimlerinden biri, cast Kutulu.</span><span class="sxs-lookup"><span data-stu-id="a49ef-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="a49ef-113">Sarmalanmamış Al ne zaman değer türüne dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="a49ef-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="a49ef-114">Kutuları yığında ayrılmış ve atık olarak toplanmış, çok fazla kutulama ve kutudan çıkarma nesneler olduğundan öbek, atık toplayıcı ve sonuçta uygulamanın performansını olumsuz etkileyebilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="a49ef-115">Başvuru türleri cast olarak buna karşılık, böyle bir kutulama oluşur.</span><span class="sxs-lookup"><span data-stu-id="a49ef-115">In contrast, no such boxing occurs as reference types are cast.</span></span>  
  
 <span data-ttu-id="a49ef-116">Ardından, tüm değer değer türü atamaları kopyalama ancak başvuru türü atamalarıyla başvuru kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a49ef-116">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="a49ef-117">Bu nedenle, büyük referans tür atamaları büyük değer türleri atamaları ucuz.</span><span class="sxs-lookup"><span data-stu-id="a49ef-117">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="a49ef-118">Son olarak, değer türleri değeriyle geçirilir ancak başvuru türleri başvuruya göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-118">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="a49ef-119">Bir başvuru türünde bir örnek yapılan değişiklikler tüm başvuruları örneğini işaret etkiler.</span><span class="sxs-lookup"><span data-stu-id="a49ef-119">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="a49ef-120">Değer türü örnekleri değeriyle geçirildiğinde kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a49ef-120">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="a49ef-121">Bir değer türü örneği değiştirildiğinde, Elbette kendi kopyaları hiçbirini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="a49ef-121">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="a49ef-122">Kopya açıkça kullanıcı tarafından oluşturulmaz, ancak bağımsız değişkenler geçirilir ya da değerleri döndürülen dönüş örtük olarak oluşturulmuş olduğundan değiştirilebilir değer türleri birçok kullanıcılar için kafa karıştırıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-122">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="a49ef-123">Bu nedenle, değer türleri sabit olmalı.</span><span class="sxs-lookup"><span data-stu-id="a49ef-123">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="a49ef-124">Altın kural, bir çerçeve türlerinde çoğunluğu sınıfları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a49ef-124">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="a49ef-125">Bununla birlikte, içinde bir değer türü özelliklerini yapılar kullanmak daha uygun kolaylaştırır bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="a49ef-125">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="a49ef-126">**✓ DÜŞÜNÜN** türünün örnekleri küçük ve yaygın olarak kısa süreli veya diğer nesneleri genellikle katıştırılmış yapı yerine bir sınıf tanımlama.</span><span class="sxs-lookup"><span data-stu-id="a49ef-126">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="a49ef-127">**KAÇININ x** türü tüm aşağıdaki özelliklere sahip olmadığı sürece yapı tanımlama:</span><span class="sxs-lookup"><span data-stu-id="a49ef-127">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="a49ef-128">Mantıksal olarak, ilkel türler için benzer tek bir değeri temsil eder (`int`, `double`vb..).</span><span class="sxs-lookup"><span data-stu-id="a49ef-128">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="a49ef-129">Bir örnek boyutu altında 16 bayt vardır.</span><span class="sxs-lookup"><span data-stu-id="a49ef-129">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="a49ef-130">Değişmez.</span><span class="sxs-lookup"><span data-stu-id="a49ef-130">It is immutable.</span></span>  
  
-   <span data-ttu-id="a49ef-131">Bunu sık Kutulu gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a49ef-131">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="a49ef-132">Diğer durumlarda, sınıflar türlerinizi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a49ef-132">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="a49ef-133">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="a49ef-133">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a49ef-134">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="a49ef-134">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49ef-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a49ef-135">See Also</span></span>  
 [<span data-ttu-id="a49ef-136">Türü tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a49ef-136">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="a49ef-137">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a49ef-137">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
