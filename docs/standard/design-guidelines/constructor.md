---
title: "Oluşturucu tasarım"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a46bf111b76ef6d07fa99cc3b19684a0726b7062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="constructor-design"></a><span data-ttu-id="ba71b-102">Oluşturucu tasarım</span><span class="sxs-lookup"><span data-stu-id="ba71b-102">Constructor Design</span></span>
<span data-ttu-id="ba71b-103">Oluşturucular iki tür vardır: oluşturucular ve örnek oluşturucuları yazın.</span><span class="sxs-lookup"><span data-stu-id="ba71b-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="ba71b-104">Türü oluşturucuları statik ve CLR tarafından türü kullanılmadan önce çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="ba71b-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="ba71b-105">Örnek oluşturucuları bir türünün bir örneği oluşturulduğunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ba71b-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="ba71b-106">Türü oluşturucuları parametreleri alamıyor.</span><span class="sxs-lookup"><span data-stu-id="ba71b-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="ba71b-107">Örnek oluşturucuları olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-107">Instance constructors can.</span></span> <span data-ttu-id="ba71b-108">Herhangi bir parametre ele yok örnek oluşturucuları genellikle varsayılan oluşturucular denir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="ba71b-109">Oluşturucular bir türün örneklerinin oluşturmak için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="ba71b-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="ba71b-110">Çoğu geliştirici arayın ve örnekler (örneğin, Fabrika yöntemleri) oluşturma alternatif yolu düşünmeden önce bir oluşturucu kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="ba71b-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="ba71b-111">**✓ DÜŞÜNÜN** sağlayan basit, ideal olarak varsayılan, Oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="ba71b-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="ba71b-112">Parametreler çok az sayıda basit bir oluşturucuya sahip ve tüm ilkel veya numaralandırmaları parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="ba71b-113">Bu tür basit oluşturucular framework kullanılabilirliğini artırın.</span><span class="sxs-lookup"><span data-stu-id="ba71b-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="ba71b-114">**✓ DÜŞÜNÜN** statik Üreteç yöntemi yerine bir oluşturucu istenen işlemin semantiği doğrudan yapımı yeni bir örneğini eşleşmiyorsa ya da Oluşturucusu tasarım yönergeleri izleyerek doğal olmayan hissi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ba71b-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="ba71b-115">**✓ YAPMAK** ana özelliklerini ayarlamak için kısayol olarak Oluşturucusu parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba71b-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="ba71b-116">Semantiği fark olmalıdır bazı özellik kümeleri tarafından izlenen boş Oluşturucusu kullanma ve birden çok bağımsız değişkenlerle bir oluşturucu kullanma.</span><span class="sxs-lookup"><span data-stu-id="ba71b-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="ba71b-117">**✓ YAPMAK** Oluşturucu parametreleri yalnızca özelliğini ayarlamak için kullanılan Oluşturucu parametreleri ve bir özellik için aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba71b-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="ba71b-118">Tür parametreleri ve özellikleri arasındaki tek fark büyük/küçük harfleri.</span><span class="sxs-lookup"><span data-stu-id="ba71b-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="ba71b-119">**✓ YAPMAK** Oluşturucusu en az iş.</span><span class="sxs-lookup"><span data-stu-id="ba71b-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="ba71b-120">Oluşturucular kadar iş yakalama dışında Oluşturucu parametreleri yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="ba71b-121">Başka bir işlem maliyetini gerekli kadar Gecikmeli.</span><span class="sxs-lookup"><span data-stu-id="ba71b-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="ba71b-122">**✓ YAPMAK** uygunsa örnek Oluşturucular, özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ba71b-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="ba71b-123">**✓ YAPMAK** böyle bir oluşturucu gerekliyse, sınıflar, bir ortak varsayılan oluşturucu açıkça bildirin.</span><span class="sxs-lookup"><span data-stu-id="ba71b-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="ba71b-124">Bir türde tüm oluşturucular açıkça bildirmeyin, birçok dilde (örneğin, C# ' ta) otomatik olarak ortak varsayılan bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ba71b-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="ba71b-125">(Soyut sınıflar korumalı Oluşturucu Al)</span><span class="sxs-lookup"><span data-stu-id="ba71b-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="ba71b-126">Parametreli oluşturucusu için sınıf ekleme derleyici varsayılan oluşturucu eklemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="ba71b-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="ba71b-127">Bu genellikle yanlışlıkla önemli değişiklikler neden olur.</span><span class="sxs-lookup"><span data-stu-id="ba71b-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="ba71b-128">**KAÇININ x** açıkça varsayılan oluşturucular üzerinde yapıları tanımlama.</span><span class="sxs-lookup"><span data-stu-id="ba71b-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="ba71b-129">Varsayılan Oluşturucu tanımlanmazsa, bu dizinin her bir yuvada çalıştırılacak sahip olmadığından bu dizi oluşturma daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="ba71b-130">C# ' de dahil olmak üzere birçok derleyicileri, bu nedenle parametresiz kurucular yapılar izin verme unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba71b-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="ba71b-131">**KAÇININ x** kurucusu içinde bir nesne üzerinde sanal üyeler çağırma.</span><span class="sxs-lookup"><span data-stu-id="ba71b-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="ba71b-132">En çok türetilen Tür oluşturucu tam henüz çalıştırılmadı olsa bile sanal üyesi çağırma çağrılacak, en çok türetilen override neden olur.</span><span class="sxs-lookup"><span data-stu-id="ba71b-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="ba71b-133">Türü kurucusunu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ba71b-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="ba71b-134">**✓ YAPMAK** statik oluşturucular özel yap.</span><span class="sxs-lookup"><span data-stu-id="ba71b-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="ba71b-135">Bir sınıf oluşturucu olarak da adlandırılan bir statik Oluşturucu türü başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba71b-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="ba71b-136">CLR türünün ilk örneği oluşturulduğunda veya ilgili türdeki tüm statik üyeler denir önce statik Oluşturucusu çağırır.</span><span class="sxs-lookup"><span data-stu-id="ba71b-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="ba71b-137">Kullanıcının statik Oluşturucusu ne zaman çağrıldığını üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba71b-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="ba71b-138">Statik oluşturucu özel durumda değilse, CLR dışında bir kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="ba71b-139">Oluşturucuda gerçekleştirilen işlemler bağlı olarak bu beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba71b-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="ba71b-140">C# Derleyici statik oluşturucular özel olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="ba71b-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="ba71b-141">**X yok** statik oluşturucular özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ba71b-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="ba71b-142">Bir özel durum türü oluşturucudan oluşturulursa türü geçerli uygulama etki alanında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="ba71b-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="ba71b-143">**✓ DÜŞÜNÜN** çalışma zamanı açıkça tanımlanmış bir statik oluşturucusu yok türleri performansını optimize etmek mümkün olduğundan statik oluşturucular açıkça kullanmak yerine statik alanları satır içi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="ba71b-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="ba71b-144">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ba71b-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ba71b-145">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="ba71b-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba71b-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba71b-146">See Also</span></span>  
 [<span data-ttu-id="ba71b-147">Üye tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ba71b-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="ba71b-148">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ba71b-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
