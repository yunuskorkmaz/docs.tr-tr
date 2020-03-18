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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400605"
---
# <a name="constructor-design"></a><span data-ttu-id="19157-102">Oluşturucu Tasarımı</span><span class="sxs-lookup"><span data-stu-id="19157-102">Constructor Design</span></span>

<span data-ttu-id="19157-103">İki tür yapıcı vardır: tip yapıcılar ve örnek yapıcılar.</span><span class="sxs-lookup"><span data-stu-id="19157-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="19157-104">Tür oluşturucular statiktir ve tür kullanılmadan önce CLR tarafından çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="19157-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="19157-105">Örnek oluşturucular, bir tür örneği oluşturulduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="19157-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="19157-106">Tür oluşturucular herhangi bir parametre alamaz.</span><span class="sxs-lookup"><span data-stu-id="19157-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="19157-107">Örnek yapıcılar yapabilir.</span><span class="sxs-lookup"><span data-stu-id="19157-107">Instance constructors can.</span></span> <span data-ttu-id="19157-108">Herhangi bir parametre almayan örnek yapıcılar genellikle parametresiz yapıcılar olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="19157-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="19157-109">Yapıcılar, bir tür örnekleri oluşturmanın en doğal yoludur.</span><span class="sxs-lookup"><span data-stu-id="19157-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="19157-110">Çoğu geliştirici, örnek oluşturmanın alternatif yollarını (fabrika yöntemleri gibi) düşünmeden önce bir oluşturucuüzerinde arama yapar ve kullanmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="19157-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="19157-111">✔️ basit, ideal varsayılan, yapıcılar sağlayan düşünün.</span><span class="sxs-lookup"><span data-stu-id="19157-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="19157-112">Basit bir oluşturucu nun çok az sayıda parametresi vardır ve tüm parametreler ilkel veya enumdur.</span><span class="sxs-lookup"><span data-stu-id="19157-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="19157-113">Bu tür basit yapıcılar çerçevenin kullanılabilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="19157-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="19157-114">✔️, istenilen işlemin anlambilimi doğrudan yeni bir örneğin yapımıyla eşleninmiyorsa veya konstrüktör tasarım yönergelerini izleyerek doğal değilse, yapıcı yerine statik bir fabrika yöntemi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="19157-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="19157-115">✔️ DO, ana özellikleri ayarlamak için kısayol olarak oluşturucu parametreleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="19157-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="19157-116">Boş yapıcıyı ve ardından bazı özellik kümelerini kullanmakla birden çok bağımsız değişkeni olan bir oluşturucu kullanmak arasında anlam ayrımı olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="19157-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="19157-117">✔️ Yapı parametreleri için aynı adı ve bir özellik için yapı parametreleri yalnızca özelliği ayarlamak için kullanılırsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="19157-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="19157-118">Bu parametreler ve özellikleri arasındaki tek fark kasa olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19157-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="19157-119">✔️ yapıcı minimum iş yapmak.</span><span class="sxs-lookup"><span data-stu-id="19157-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="19157-120">Yapıcılar, yapıcı parametreleri yakalamak dışında çok fazla iş yapmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="19157-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="19157-121">Başka bir işlemin maliyeti gerekli olana kadar geciktirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="19157-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="19157-122">✔️ DO, uygunsa örnek oluşturuculardan özel durumlar atar.</span><span class="sxs-lookup"><span data-stu-id="19157-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="19157-123">✔️ DO, böyle bir oluşturucu gerekliyse, sınıflardaki kamu parametresiz oluşturucuyu açıkça beyan edin.</span><span class="sxs-lookup"><span data-stu-id="19157-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="19157-124">Bir türde herhangi bir oluşturucuaçıkça beyan etmezseniz, birçok dil (C# gibi) otomatik olarak bir kamu parametresiz oluşturucu ekler.</span><span class="sxs-lookup"><span data-stu-id="19157-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="19157-125">(Soyut sınıflar korunan bir yapıcı alır.)</span><span class="sxs-lookup"><span data-stu-id="19157-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="19157-126">Bir sınıfa parametreli oluşturucu eklemek derleyicinin parametresiz oluşturucuyu eklemesini engeller.</span><span class="sxs-lookup"><span data-stu-id="19157-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="19157-127">Bu genellikle kazara kırılma değişikliklerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="19157-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="19157-128">❌Yapılar üzerinde parametresiz yapıcıları açıkça tanımlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="19157-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="19157-129">Bu, parametresiz oluşturucu tanımlanmamışsa, dizideki her yuvada çalıştırılması gerekmedığından, dizi oluşturmayı hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="19157-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="19157-130">C# da dahil olmak üzere birçok derleyicinin bu nedenle yapı oluşturuculara sahip olması izin vermeyin.</span><span class="sxs-lookup"><span data-stu-id="19157-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="19157-131">❌Oluşturucusu içindeki bir nesneye sanal üyeleri çağırmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="19157-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="19157-132">En çok türetilmiş türün oluşturucusu henüz tam olarak çalıştırılmasa bile, sanal bir üyeyi çağırmak en çok türetilmiş geçersiz kılmanın çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="19157-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="19157-133">Tip Oluşturucu Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="19157-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="19157-134">✔️ statik yapıcılar özel yapmak.</span><span class="sxs-lookup"><span data-stu-id="19157-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="19157-135">Bir tür e-baş harflerini almak için sınıf oluşturucu olarak da adlandırılan statik bir oluşturucu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19157-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="19157-136">CLR, türün ilk örneği oluşturulmadan veya bu türdeki statik üyeler çağrılmadan önce statik oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="19157-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="19157-137">Statik oluşturucu çağrıldığında kullanıcının denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="19157-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="19157-138">Statik bir oluşturucu özel değilse, CLR dışındaki kodla çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="19157-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="19157-139">Oluşturucuda gerçekleştirilen işlemlere bağlı olarak, bu beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="19157-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="19157-140">C# derleyicisi statik yapıcıları özel olmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="19157-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="19157-141">❌Statik oluşturuculardan özel durumlar ATMAYIN.</span><span class="sxs-lookup"><span data-stu-id="19157-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="19157-142">Bir tür oluşturucudan bir özel durum atılırsa, tür geçerli uygulama etki alanında kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="19157-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="19157-143">✔️, çalışma zamanı açıkça tanımlanmış statik oluşturucusu olmayan türlerin performansını en iyi duruma getirebildiği için, statik alanları açıkça statik oluşturucukullanmak yerine satır satır da başlatmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="19157-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="19157-144">*2005, 2009 Microsoft Corporation © bölümleri. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="19157-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="19157-145">*Pearson Education, Inc.'in izniyle [Framework Design Guidelines: Conventions, Idioms and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina ve Brad Abrams tarafından 22 Ekim 2008'de Addison-Wesley Professional tarafından Microsoft Windows Geliştirme Serisi'nin bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="19157-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="19157-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19157-146">See also</span></span>

- [<span data-ttu-id="19157-147">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="19157-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="19157-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="19157-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
