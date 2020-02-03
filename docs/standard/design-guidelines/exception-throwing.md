---
title: Özel Durum Oluşturma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 18927d242c2ed957d2bc9f8b481beeed775a4e4e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741667"
---
# <a name="exception-throwing"></a><span data-ttu-id="ec7ff-102">Özel Durum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec7ff-102">Exception Throwing</span></span>
<span data-ttu-id="ec7ff-103">Özel durum-bu bölümde açıklanan oluşturma yönergeleri, yürütme hatası anlamı için iyi bir tanım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="ec7ff-104">Yürütme hatası, bir üye için tasarlandıkları şeyi (üye adının ne kadar gösterdiği) yapamayacağı zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="ec7ff-105">Örneğin, `OpenFile` yöntemi çağırana bir açık dosya tutamacı döndüremez, bir yürütme hatası olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="ec7ff-106">Çoğu geliştirici, sıfıra bölme veya null başvurular gibi kullanım hataları için özel durumları kullanma konusunda rahat hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="ec7ff-107">Çerçevede, yürütme hataları da dahil olmak üzere tüm hata koşulları için özel durumlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="ec7ff-108">❌ hata kodları döndürmez.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="ec7ff-109">Özel durumlar, çerçeveler içindeki hataların bildirilme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="ec7ff-110">özel durumlar oluşturarak rapor yürütme hatalarıyla ✔️.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="ec7ff-111">✔️, kodunuzun daha fazla yürütme için güvenli olmadığı bir durumla karşılaştığında bir özel durum oluşturmak yerine `System.Environment.FailFast` (.NET Framework 2,0 özelliği) çağırarak işlemi sonlandırmaktan yarar.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="ec7ff-112">❌, mümkünse normal denetim akışı için özel durumlar kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="ec7ff-113">Olası yarış koşullarına sahip sistem arızaları ve işlemler haricinde, çerçeve tasarımcıları, kullanıcıların özel durum oluşturmayan kodlar yazabilmesi için API 'Ler tasarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="ec7ff-114">Örneğin, kullanıcılar özel durum oluşturmayan bir kod yazabilmesi için bir üyeyi çağırmadan önce önkoşulları denetlemek için bir yol sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="ec7ff-115">Başka bir üyenin ön koşulları 'nı denetlemek için kullanılan üye, genellikle test edici olarak adlandırılır ve işi gerçekten yapan üyeye bir doer denir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="ec7ff-116">Sınayıcı-doer deseninin kabul edilemez bir performans yükü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="ec7ff-117">Bu gibi durumlarda, bu şekilde adlandırılan TRY-Parse deseninin göz önünde bulundurulmaları gerekir (daha fazla bilgi için bkz. [özel durumlar ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) ).</span><span class="sxs-lookup"><span data-stu-id="ec7ff-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="ec7ff-118">✔️ özel durum oluşturma performansı etkilerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="ec7ff-119">Saniyede 100 ' den yüksek olan throw ücretleri, çoğu uygulamanın performansını önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="ec7ff-120">✔️, üye sözleşmesinin ihlal edildiği (sistem hatası yerine) ve bunları sözleşmenin bir parçası olarak kabul eden, genel olarak çağrılabilir Üyeler tarafından oluşturulan tüm özel durumları belgeleyin.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="ec7ff-121">Sözleşmenin bir parçası olan özel durumlar bir sürümden sonrakine değişmemelidir (yani, özel durum türü değişmemelidir ve yeni özel durumlar eklenmemelidir).</span><span class="sxs-lookup"><span data-stu-id="ec7ff-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="ec7ff-122">❌, herhangi bir seçeneğe göre oluşturabilecek veya olmayan ortak üyelere sahip DEĞILDIR.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="ec7ff-123">❌, dönüş değeri veya bir `out` parametresi olarak özel durumlar döndüren ortak üyelere sahip DEĞILDIR.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="ec7ff-124">Özel durum tabanlı hata raporlama avantajlarının çoğunu yapmak yerine ortak API 'lerden özel durumlar döndürme.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="ec7ff-125">✔️ özel durum Oluşturucu yöntemleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="ec7ff-126">Farklı yerlerden aynı özel durumu oluşturmak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="ec7ff-127">Kod blobunun önüne geçmek için özel durumlar oluşturan ve özelliklerini başlatacak yardımcı yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="ec7ff-128">Ayrıca, özel durum oluşturan Üyeler satır içine alınır.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="ec7ff-129">Throw deyiminizi oluşturucunun içinde taşımak üyenin satır içine eklenmesine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="ec7ff-130">❌ özel durum filtresi bloklarından özel durumlar oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="ec7ff-131">Özel durum filtresi bir özel durum harekete geçirirse, özel durum CLR tarafından yakalanır ve filtre false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="ec7ff-132">Bu davranış, yürütülen filtreden ayırt edilemez ve açıkça false döndürüyor ve bu nedenle hata ayıklama çok zor.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="ec7ff-133">❌ finally bloklarından özel durumları açıkça oluşturmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="ec7ff-134">Oluşturulan çağırma yöntemlerinin sonucu olarak, örtülü olarak oluşan özel durumlar kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="ec7ff-135">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ec7ff-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ec7ff-136">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="ec7ff-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ec7ff-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-137">See also</span></span>

- [<span data-ttu-id="ec7ff-138">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ec7ff-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ec7ff-139">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ec7ff-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
