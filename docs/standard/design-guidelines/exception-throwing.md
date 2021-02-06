---
description: 'Hakkında daha fazla bilgi edinin: özel durum atma'
title: Özel Durum Oluşturma
ms.date: 10/22/2008
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: b1cf7a4eecc32a9f76ea06c47dd6c16d3afe5470
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642143"
---
# <a name="exception-throwing"></a><span data-ttu-id="e0de1-103">Özel Durum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0de1-103">Exception Throwing</span></span>

<span data-ttu-id="e0de1-104">Özel durum-bu bölümde açıklanan oluşturma yönergeleri, yürütme hatası anlamı için iyi bir tanım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-104">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="e0de1-105">Yürütme hatası, bir üye için tasarlandıkları şeyi (üye adının ne kadar gösterdiği) yapamayacağı zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0de1-105">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="e0de1-106">Örneğin, `OpenFile` Yöntem çağırana bir açık dosya tutamacı döndüremez, bir yürütme hatası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-106">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="e0de1-107">Çoğu geliştirici, sıfıra bölme veya null başvurular gibi kullanım hataları için özel durumları kullanma konusunda rahat hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-107">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="e0de1-108">Çerçevede, yürütme hataları da dahil olmak üzere tüm hata koşulları için özel durumlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0de1-108">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="e0de1-109">❌ Hata kodlarını döndürmeyin.</span><span class="sxs-lookup"><span data-stu-id="e0de1-109">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="e0de1-110">Özel durumlar, çerçeveler içindeki hataların bildirilme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-110">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="e0de1-111">özel durumlar oluşturarak rapor yürütme hatalarıyla ✔️.</span><span class="sxs-lookup"><span data-stu-id="e0de1-111">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="e0de1-112">✔️, `System.Environment.FailFast` kodunuz daha fazla yürütme için güvenli olmayan bir durumla karşılaştığında bir özel durum oluşturmak yerine (.NET Framework 2,0 özelliği) işlemi SONLANDıRARAK deneyin.</span><span class="sxs-lookup"><span data-stu-id="e0de1-112">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="e0de1-113">❌ Mümkünse normal denetim akışı için özel durumlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e0de1-113">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="e0de1-114">Olası yarış koşullarına sahip sistem arızaları ve işlemler haricinde, çerçeve tasarımcıları, kullanıcıların özel durum oluşturmayan kodlar yazabilmesi için API 'Ler tasarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-114">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="e0de1-115">Örneğin, kullanıcılar özel durum oluşturmayan bir kod yazabilmesi için bir üyeyi çağırmadan önce önkoşulları denetlemek için bir yol sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0de1-115">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="e0de1-116">Başka bir üyenin ön koşulları 'nı denetlemek için kullanılan üye, genellikle test edici olarak adlandırılır ve işi gerçekten yapan üyeye bir doer denir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-116">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="e0de1-117">Tester-Doer deseninin kabul edilemez bir performans yükü olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="e0de1-117">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="e0de1-118">Bu gibi durumlarda, bu şekilde çağrılan Try-Parse deseninin göz önünde bulundurulmaları gerekir (daha fazla bilgi için bkz. [özel durumlar ve performans](exceptions-and-performance.md) ).</span><span class="sxs-lookup"><span data-stu-id="e0de1-118">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="e0de1-119">✔️ özel durum oluşturma performansı etkilerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e0de1-119">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="e0de1-120">Saniyede 100 ' den yüksek olan throw ücretleri, çoğu uygulamanın performansını önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-120">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="e0de1-121">✔️, üye sözleşmesinin ihlal edildiği (sistem hatası yerine) ve bunları sözleşmenin bir parçası olarak kabul eden, genel olarak çağrılabilir Üyeler tarafından oluşturulan tüm özel durumları belgeleyin.</span><span class="sxs-lookup"><span data-stu-id="e0de1-121">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="e0de1-122">Sözleşmenin bir parçası olan özel durumlar bir sürümden sonrakine değişmemelidir (yani, özel durum türü değişmemelidir ve yeni özel durumlar eklenmemelidir).</span><span class="sxs-lookup"><span data-stu-id="e0de1-122">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="e0de1-123">❌ Herhangi bir seçeneğe göre oluşturabilecek veya olmayan ortak üyelere sahip değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0de1-123">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="e0de1-124">❌ Dönüş değeri veya bir parametre olarak özel durumlar döndüren ortak üyelere sahip DEĞILDIR `out` .</span><span class="sxs-lookup"><span data-stu-id="e0de1-124">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="e0de1-125">Özel durum tabanlı hata raporlama avantajlarının çoğunu yapmak yerine ortak API 'lerden özel durumlar döndürme.</span><span class="sxs-lookup"><span data-stu-id="e0de1-125">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="e0de1-126">✔️ özel durum Oluşturucu yöntemleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="e0de1-126">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="e0de1-127">Farklı yerlerden aynı özel durumu oluşturmak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="e0de1-127">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="e0de1-128">Kod blobunun önüne geçmek için özel durumlar oluşturan ve özelliklerini başlatacak yardımcı yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0de1-128">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="e0de1-129">Ayrıca, özel durum oluşturan Üyeler satır içine alınır.</span><span class="sxs-lookup"><span data-stu-id="e0de1-129">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="e0de1-130">Throw deyiminizi oluşturucunun içinde taşımak üyenin satır içine eklenmesine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-130">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="e0de1-131">❌ Özel durum filtresi bloklarından özel durumlar atamayın.</span><span class="sxs-lookup"><span data-stu-id="e0de1-131">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="e0de1-132">Özel durum filtresi bir özel durum harekete geçirirse, özel durum CLR tarafından yakalanır ve filtre false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0de1-132">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="e0de1-133">Bu davranış, yürütülen filtreden ayırt edilemez ve açıkça false döndürüyor ve bu nedenle hata ayıklama çok zor.</span><span class="sxs-lookup"><span data-stu-id="e0de1-133">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="e0de1-134">❌ Finally bloklarından özel durumları açıkça oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e0de1-134">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="e0de1-135">Oluşturulan çağırma yöntemlerinin sonucu olarak, örtülü olarak oluşan özel durumlar kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e0de1-135">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="e0de1-136">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e0de1-136">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e0de1-137">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="e0de1-137">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e0de1-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0de1-138">See also</span></span>

- [<span data-ttu-id="e0de1-139">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e0de1-139">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e0de1-140">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e0de1-140">Design Guidelines for Exceptions</span></span>](exceptions.md)
