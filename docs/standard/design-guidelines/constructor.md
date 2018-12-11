---
title: Oluşturucu tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
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
author: KrzysztofCwalina
ms.openlocfilehash: b140be34d9359cfdca1250a924db787563127d19
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127790"
---
# <a name="constructor-design"></a><span data-ttu-id="15d88-102">Oluşturucu tasarımı</span><span class="sxs-lookup"><span data-stu-id="15d88-102">Constructor Design</span></span>
<span data-ttu-id="15d88-103">Oluşturucular iki tür vardır: oluşturucular ve örnek oluşturucuları yazın.</span><span class="sxs-lookup"><span data-stu-id="15d88-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="15d88-104">Türü oluşturucuları, statik ve türü kullanılmadan önce CLR tarafından çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="15d88-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="15d88-105">Örnek oluşturucuları, bir türün bir örneği oluşturulduğunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="15d88-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="15d88-106">Herhangi bir parametre türü oluşturucuları alamıyor.</span><span class="sxs-lookup"><span data-stu-id="15d88-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="15d88-107">Örnek oluşturucuları olabilir.</span><span class="sxs-lookup"><span data-stu-id="15d88-107">Instance constructors can.</span></span> <span data-ttu-id="15d88-108">Herhangi bir parametre yakalayana örnek oluşturucuları genellikle varsayılan oluşturucu çağrılır.</span><span class="sxs-lookup"><span data-stu-id="15d88-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="15d88-109">Oluşturucular, bir türün örneğini oluşturmak için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="15d88-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="15d88-110">Çoğu geliştirici, arayın ve bunlar örnekleri (örneğin, Fabrika yöntemleri) oluşturmanın farklı yolları düşünmeden önce bir oluşturucu kullanmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="15d88-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="15d88-111">**✓ CONSIDER** sağlayan basit, ideal olarak varsayılan, Oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="15d88-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="15d88-112">Basit bir oluşturucu çok küçük bir dizi parametre vardır ve tüm parametreleri ilkel veya sabit listeleri.</span><span class="sxs-lookup"><span data-stu-id="15d88-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="15d88-113">Basit tür oluşturucular framework'ün kullanılabilirlik artırın.</span><span class="sxs-lookup"><span data-stu-id="15d88-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="15d88-114">**✓ CONSIDER** statik Üreteç yöntemi yerine bir oluşturucu istenen işlemin semantiği doğrudan yapımı yeni bir örneğini eşleşmiyorsa ya da Oluşturucusu tasarım yönergeleri izleyerek doğal olmayan hissi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="15d88-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="15d88-115">**✓ DO** ana özelliklerini ayarlamak için kısayol olarak Oluşturucusu parametrelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="15d88-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="15d88-116">Semantik fark olmalıdır bazı özellik kümeleri tarafından izlenen boş oluşturucu ve birden çok bağımsız değişkenlerle bir kurucu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="15d88-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="15d88-117">**✓ DO** Oluşturucu parametreleri yalnızca özelliğini ayarlamak için kullanılan Oluşturucu parametreleri ve bir özellik için aynı adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="15d88-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="15d88-118">Bu tür parametreleri ve özellikleri arasındaki tek fark büyük/küçük harfleri.</span><span class="sxs-lookup"><span data-stu-id="15d88-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="15d88-119">**✓ DO** Oluşturucusu en az iş.</span><span class="sxs-lookup"><span data-stu-id="15d88-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="15d88-120">Oluşturucuları, oluşturucu parametresi kadar iş yakalama dışında yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15d88-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="15d88-121">Başka bir işlem maliyetini gerekli kadar Gecikmeli.</span><span class="sxs-lookup"><span data-stu-id="15d88-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="15d88-122">**✓ DO** uygunsa örnek Oluşturucular, özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="15d88-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="15d88-123">**✓ DO** böyle bir oluşturucu gerekliyse, sınıflar, bir ortak varsayılan oluşturucu açıkça bildirin.</span><span class="sxs-lookup"><span data-stu-id="15d88-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="15d88-124">Türe göre açıkça tüm oluşturucular bildirmeyin, birçok dili (C# gibi) genel bir varsayılan oluşturucu otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="15d88-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="15d88-125">(Soyut sınıflar korumalı Oluşturucu Al)</span><span class="sxs-lookup"><span data-stu-id="15d88-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="15d88-126">Parametreli bir kurucu ekleme, derleyici varsayılan oluşturucuyu eklemesini önler.</span><span class="sxs-lookup"><span data-stu-id="15d88-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="15d88-127">Bu genellikle yanlışlıkla bozucu değişiklikleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="15d88-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="15d88-128">**X AVOID** açıkça varsayılan oluşturucular üzerinde yapıları tanımlama.</span><span class="sxs-lookup"><span data-stu-id="15d88-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="15d88-129">Varsayılan Oluşturucu tanımlanmamışsa, dizideki her yuva çalıştırılacak sahip olmadığından bu dizi oluşturma daha hızlı sağlar.</span><span class="sxs-lookup"><span data-stu-id="15d88-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="15d88-130">C# ' de dahil olmak üzere birçok derleyiciler yapılar, bu nedenle parametresiz oluşturucular izin verme unutmayın.</span><span class="sxs-lookup"><span data-stu-id="15d88-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="15d88-131">**X AVOID** kurucusu içinde bir nesne üzerinde sanal üyeler çağırma.</span><span class="sxs-lookup"><span data-stu-id="15d88-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="15d88-132">En çok türetilen türü oluşturucusuna tamamen henüz çalıştırılmadı bile sanal bir üye çağırmak çağrılacak, en çok türetilen geçersiz kılma neden olur.</span><span class="sxs-lookup"><span data-stu-id="15d88-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="15d88-133">Tür oluşturucu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="15d88-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="15d88-134">**✓ DO** statik oluşturucular özel yap.</span><span class="sxs-lookup"><span data-stu-id="15d88-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="15d88-135">Bir sınıf oluşturucu olarak da adlandırılan bir statik Oluşturucu, bir tür başlatmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="15d88-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="15d88-136">CLR türünün ilk örneği oluşturulduğunda veya herhangi bir statik üyeye türdeki adlı önce statik oluşturucuyu çağırır.</span><span class="sxs-lookup"><span data-stu-id="15d88-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="15d88-137">Kullanıcının statik Oluşturucu ne zaman çağrıldığını üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="15d88-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="15d88-138">Statik oluşturucu özel değilse, CLR dışındaki kod tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="15d88-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="15d88-139">Oluşturucu içinde gerçekleştirilen işlemlere bağlı olarak bu, beklenmeyen davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="15d88-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="15d88-140">C# derleyicisi statik oluşturucular özel olmasını zorlar.</span><span class="sxs-lookup"><span data-stu-id="15d88-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="15d88-141">**X DO NOT** statik oluşturucular özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="15d88-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="15d88-142">Bir tür oluşturucusunda bir özel durum, geçerli uygulama etki alanında türü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="15d88-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="15d88-143">**✓ CONSIDER** çalışma zamanı açıkça tanımlanmış bir statik oluşturucusu yok türleri performansını optimize etmek mümkün olduğundan statik oluşturucular açıkça kullanmak yerine statik alanları satır içi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="15d88-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="15d88-144">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="15d88-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="15d88-145">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="15d88-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d88-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d88-146">See also</span></span>

- [<span data-ttu-id="15d88-147">Üye Tasarımı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="15d88-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="15d88-148">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="15d88-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
