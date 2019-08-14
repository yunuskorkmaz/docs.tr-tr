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
author: KrzysztofCwalina
ms.openlocfilehash: a43ec815275e58f4bc6462fb4f5cb4733267de31
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972112"
---
# <a name="constructor-design"></a><span data-ttu-id="93cdc-102">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="93cdc-102">Constructor Design</span></span>

<span data-ttu-id="93cdc-103">İki tür Oluşturucu vardır: tür oluşturucular ve örnek oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="93cdc-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="93cdc-104">Tür oluşturucuları statiktir ve tür kullanılmadan önce CLR tarafından çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="93cdc-105">Örnek oluşturucular, bir tür örneği oluşturulduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="93cdc-106">Tür oluşturucular hiçbir parametre alamaz.</span><span class="sxs-lookup"><span data-stu-id="93cdc-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="93cdc-107">Örnek oluşturucular olabilir.</span><span class="sxs-lookup"><span data-stu-id="93cdc-107">Instance constructors can.</span></span> <span data-ttu-id="93cdc-108">Parametre kullanmayan örnek oluşturucular genellikle parametresiz oluşturucular olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="93cdc-109">Oluşturucular, bir türün örneklerini oluşturmanın en doğal yoludur.</span><span class="sxs-lookup"><span data-stu-id="93cdc-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="93cdc-110">Çoğu geliştirici, örnek oluşturma (örneğin, Factory yöntemleri) için alternatif yolları düşünmeleri için bir oluşturucuyu arar ve kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="93cdc-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="93cdc-111">**✓ CONSIDER** sağlayan basit, ideal olarak varsayılan, Oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="93cdc-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="93cdc-112">Basit bir oluşturucunun çok az sayıda parametresi vardır ve tüm parametreler temel elemanlar veya Numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="93cdc-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="93cdc-113">Bu tür basit oluşturucular Framework kullanılabilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="93cdc-114">**✓ CONSIDER** statik Üreteç yöntemi yerine bir oluşturucu istenen işlemin semantiği doğrudan yapımı yeni bir örneğini eşleşmiyorsa ya da Oluşturucusu tasarım yönergeleri izleyerek doğal olmayan hissi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="93cdc-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="93cdc-115">**✓ DO** ana özelliklerini ayarlamak için kısayol olarak Oluşturucusu parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="93cdc-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="93cdc-116">Boş oluşturucuyu, ardından bazı özellik kümelerini ve birden çok bağımsız değişkenle bir oluşturucuyu kullanarak, semantik bir farklılık olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="93cdc-117">**✓ DO** Oluşturucu parametreleri yalnızca özelliğini ayarlamak için kullanılan Oluşturucu parametreleri ve bir özellik için aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="93cdc-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="93cdc-118">Bu parametre ve özellikler arasındaki tek fark büyük küçük harf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="93cdc-119">**✓ DO** Oluşturucusu en az iş.</span><span class="sxs-lookup"><span data-stu-id="93cdc-119">**✓ DO** minimal work in the constructor.</span></span>

<span data-ttu-id="93cdc-120">Oluşturucular, Oluşturucu parametrelerini yakalamaya göre çok daha fazla çalışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="93cdc-121">Diğer bir işleme maliyeti, gerekli olana kadar Gecikmeli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="93cdc-122">**✓ DO** uygunsa örnek Oluşturucular, özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="93cdc-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="93cdc-123">**✓** , Bu tür bir Oluşturucu gerekliyse, sınıflarda Ortak parametresiz oluşturucuyu açık bir şekilde bildirir.</span><span class="sxs-lookup"><span data-stu-id="93cdc-123">**✓ DO** explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="93cdc-124">Bir tür üzerinde açıkça herhangi bir Oluşturucu bildirmezseniz, birçok dil (gibi C#) otomatik olarak ortak parametresiz bir Oluşturucu ekler.</span><span class="sxs-lookup"><span data-stu-id="93cdc-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="93cdc-125">(Soyut sınıflar korumalı bir Oluşturucu alır.)</span><span class="sxs-lookup"><span data-stu-id="93cdc-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="93cdc-126">Bir sınıfa parametreli Oluşturucu eklemek derleyicinin parametresiz oluşturucuyu eklemesini önler.</span><span class="sxs-lookup"><span data-stu-id="93cdc-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="93cdc-127">Bu genellikle yanlışlıkla önemli değişikliklere neden olur.</span><span class="sxs-lookup"><span data-stu-id="93cdc-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="93cdc-128">**X** yapılar üzerinde parametresiz oluşturucular AÇıKÇA tanımlamayı önleyin.</span><span class="sxs-lookup"><span data-stu-id="93cdc-128">**X AVOID** explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="93cdc-129">Bu, parametresiz Oluşturucu tanımlanmamışsa, dizideki her yuvada çalıştırılması gerekmediğinden, dizi oluşturmayı daha hızlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="93cdc-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="93cdc-130">Birçok derleyicilerin C#, bu nedenle yapıların parametresiz oluşturuculara sahip olduğuna izin vermez.</span><span class="sxs-lookup"><span data-stu-id="93cdc-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="93cdc-131">**X AVOID** kurucusu içinde bir nesne üzerinde sanal üyeler çağırma.</span><span class="sxs-lookup"><span data-stu-id="93cdc-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="93cdc-132">En türetilmiş türün Oluşturucusu henüz tam olarak çalıştırılmasa bile, sanal bir üyenin çağrılması en fazla türetilmiş geçersiz kılmanın çağrılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="93cdc-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="93cdc-133">Tür Oluşturucu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="93cdc-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="93cdc-134">**✓ DO** statik oluşturucular özel yap.</span><span class="sxs-lookup"><span data-stu-id="93cdc-134">**✓ DO** make static constructors private.</span></span>

<span data-ttu-id="93cdc-135">Sınıf oluşturucusu olarak da adlandırılan statik bir Oluşturucu, bir türü başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="93cdc-136">CLR, türün ilk örneği oluşturulmadan veya bu türdeki herhangi bir statik üye çağrılmadan önce statik oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="93cdc-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="93cdc-137">Statik Oluşturucu çağrıldığında kullanıcının denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="93cdc-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="93cdc-138">Statik bir Oluşturucu özel değilse, CLR dışındaki kodla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="93cdc-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="93cdc-139">Oluşturucuda gerçekleştirilen işlemlere bağlı olarak, bu beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="93cdc-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="93cdc-140">C# Derleyici statik oluşturucuları özel olmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="93cdc-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="93cdc-141">**X DO NOT** statik oluşturucular özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="93cdc-141">**X DO NOT** throw exceptions from static constructors.</span></span>

<span data-ttu-id="93cdc-142">Bir tür oluşturucusundan bir özel durum oluşturulursa, tür geçerli uygulama etki alanında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="93cdc-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="93cdc-143">**✓ CONSIDER** çalışma zamanı açıkça tanımlanmış bir statik oluşturucusu yok türleri performansını optimize etmek mümkün olduğundan statik oluşturucular açıkça kullanmak yerine statik alanları satır içi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="93cdc-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="93cdc-144">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="93cdc-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="93cdc-145">*, Framework tasarım yönergelerinden [Pearson Eğitim, Inc. izni ile yeniden yazdırılıyor: Microsoft Windows geliştirme serisi 'nin bir parçası olarak, bezysztof](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Cwalina ve atacan abkms, Ekim 22, 2008 ile Addison-Wesley Professional ile yeniden kullanılabilir .NET kitaplıkları için kurallar, ıoms ve desenler.*</span><span class="sxs-lookup"><span data-stu-id="93cdc-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="93cdc-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93cdc-146">See also</span></span>

- [<span data-ttu-id="93cdc-147">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="93cdc-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="93cdc-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="93cdc-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
