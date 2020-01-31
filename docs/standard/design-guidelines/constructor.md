---
title: Oluşturucu Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741741"
---
# <a name="constructor-design"></a><span data-ttu-id="ccce2-102">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="ccce2-102">Constructor Design</span></span>

<span data-ttu-id="ccce2-103">İki tür Oluşturucu vardır: tür oluşturucular ve örnek oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="ccce2-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="ccce2-104">Tür oluşturucuları statiktir ve tür kullanılmadan önce CLR tarafından çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="ccce2-105">Örnek oluşturucular, bir tür örneği oluşturulduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="ccce2-106">Tür oluşturucular hiçbir parametre alamaz.</span><span class="sxs-lookup"><span data-stu-id="ccce2-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="ccce2-107">Örnek oluşturucular olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccce2-107">Instance constructors can.</span></span> <span data-ttu-id="ccce2-108">Parametre kullanmayan örnek oluşturucular genellikle parametresiz oluşturucular olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="ccce2-109">Oluşturucular, bir türün örneklerini oluşturmanın en doğal yoludur.</span><span class="sxs-lookup"><span data-stu-id="ccce2-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="ccce2-110">Çoğu geliştirici, örnek oluşturma (örneğin, Factory yöntemleri) için alternatif yolları düşünmeleri için bir oluşturucuyu arar ve kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="ccce2-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="ccce2-111">✔️ basit, ideal varsayılan oluşturucular sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ccce2-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="ccce2-112">Basit bir oluşturucunun çok az sayıda parametresi vardır ve tüm parametreler temel elemanlar veya Numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="ccce2-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="ccce2-113">Bu tür basit oluşturucular Framework kullanılabilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="ccce2-114">✔️, istenen işlemin semantiğini yeni bir örneğin yapıcıya doğrudan eşlenmiyorsa veya oluşturucunun tasarım yönergeleri doğal olarak yoksa, Oluşturucu yerine bir statik fabrika yöntemi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ccce2-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="ccce2-115">✔️ Oluşturucu parametrelerini, ana özellikleri ayarlamak için kısayollar olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccce2-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="ccce2-116">Boş oluşturucuyu, ardından bazı özellik kümelerini ve birden çok bağımsız değişkenle bir oluşturucuyu kullanarak, semantik bir farklılık olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="ccce2-117">✔️, Oluşturucu parametreleri için aynı adı ve Oluşturucu parametreleri özelliği ayarlamak için kullanılırsa özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccce2-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="ccce2-118">Bu parametre ve özellikler arasındaki tek fark büyük küçük harf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="ccce2-119">✔️ oluşturucuda en az iş YAPıN.</span><span class="sxs-lookup"><span data-stu-id="ccce2-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="ccce2-120">Oluşturucular, Oluşturucu parametrelerini yakalamaya göre çok daha fazla çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="ccce2-121">Diğer bir işleme maliyeti, gerekli olana kadar Gecikmeli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="ccce2-122">✔️, uygunsa örnek oluşturuculardan özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ccce2-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="ccce2-123">Bu tür bir Oluşturucu gerekliyse, sınıflarda Ortak parametresiz oluşturucuyu açıkça bildirin ✔️.</span><span class="sxs-lookup"><span data-stu-id="ccce2-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="ccce2-124">Bir tür üzerinde açıkça herhangi bir Oluşturucu bildirmezseniz, birçok dil (gibi C#) otomatik olarak ortak parametresiz bir Oluşturucu ekler.</span><span class="sxs-lookup"><span data-stu-id="ccce2-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="ccce2-125">(Soyut sınıflar korumalı bir Oluşturucu alır.)</span><span class="sxs-lookup"><span data-stu-id="ccce2-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="ccce2-126">Bir sınıfa parametreli Oluşturucu eklemek derleyicinin parametresiz oluşturucuyu eklemesini önler.</span><span class="sxs-lookup"><span data-stu-id="ccce2-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="ccce2-127">Bu genellikle yanlışlıkla önemli değişikliklere neden olur.</span><span class="sxs-lookup"><span data-stu-id="ccce2-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="ccce2-128">❌ yapı birimlerinde açıkça parametresiz oluşturucular tanımlamayı ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="ccce2-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="ccce2-129">Bu, parametresiz Oluşturucu tanımlanmamışsa, dizideki her yuvada çalıştırılması gerekmediğinden, dizi oluşturmayı daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ccce2-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="ccce2-130">Birçok derleyicilerin C#, bu nedenle yapıların parametresiz oluşturuculara sahip olduğuna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ccce2-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="ccce2-131">❌ oluşturucusunun içindeki bir nesne üzerinde sanal üye çağırmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="ccce2-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="ccce2-132">En türetilmiş türün Oluşturucusu henüz tam olarak çalıştırılmasa bile, sanal bir üyenin çağrılması en fazla türetilmiş geçersiz kılmanın çağrılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ccce2-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="ccce2-133">Tür Oluşturucu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ccce2-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="ccce2-134">statik oluşturucuları özel hale getirmek ✔️.</span><span class="sxs-lookup"><span data-stu-id="ccce2-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="ccce2-135">Sınıf oluşturucusu olarak da adlandırılan statik bir Oluşturucu, bir türü başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="ccce2-136">CLR, türün ilk örneği oluşturulmadan veya bu türdeki herhangi bir statik üye çağrılmadan önce statik oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="ccce2-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="ccce2-137">Statik Oluşturucu çağrıldığında kullanıcının denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ccce2-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="ccce2-138">Statik bir Oluşturucu özel değilse, CLR dışındaki kodla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ccce2-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="ccce2-139">Oluşturucuda gerçekleştirilen işlemlere bağlı olarak, bu beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccce2-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="ccce2-140">C# Derleyici statik oluşturucuları özel olmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="ccce2-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="ccce2-141">❌ statik oluşturuculardan özel durumlar oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="ccce2-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="ccce2-142">Bir tür oluşturucusundan bir özel durum oluşturulursa, tür geçerli uygulama etki alanında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ccce2-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="ccce2-143">✔️, çalışma zamanı açıkça tanımlanmış bir statik oluşturucuya sahip olmayan türlerin performansını iyileştirebildiğinden, statik oluşturucuları açıkça kullanmak yerine, statik alanları satır içi olarak başlatmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ccce2-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="ccce2-144">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ccce2-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ccce2-145">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="ccce2-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ccce2-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccce2-146">See also</span></span>

- [<span data-ttu-id="ccce2-147">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ccce2-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="ccce2-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ccce2-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
