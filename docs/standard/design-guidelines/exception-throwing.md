---
title: Özel durum
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbbe84811e3fa096b9e13c459143311bb75a198
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326640"
---
# <a name="exception-throwing"></a><span data-ttu-id="9d182-102">Özel durum</span><span class="sxs-lookup"><span data-stu-id="9d182-102">Exception Throwing</span></span>
<span data-ttu-id="9d182-103">Bu bölümde açıklanan özel durum atma yönergeleri iyi bir anlamı yürütme hatası tanımı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9d182-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="9d182-104">Üyesi ne olduğunu yapamayacağınız her yürütme hatası meydana gelir (ne üye adından da anlaşılacağı) yapmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9d182-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="9d182-105">Örneğin, varsa `OpenFile` bir yürütme hatası değerlendirilebilecek, metodu çağırana bir açık dosya tanıtıcısı döndüremiyor.</span><span class="sxs-lookup"><span data-stu-id="9d182-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="9d182-106">Çoğu geliştirici, özel durumlar bölme gibi kullanım hataları için sıfır ya da null başvuru kullanabileceğinizden haline geldi.</span><span class="sxs-lookup"><span data-stu-id="9d182-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="9d182-107">Framework, özel durumları, yürütme hataları dahil olmak üzere tüm hata koşulları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d182-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="9d182-108">**X DO NOT** hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d182-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="9d182-109">Özel durumları, hataları çerçeveleri raporlama birincil araçlarıdır.</span><span class="sxs-lookup"><span data-stu-id="9d182-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="9d182-110">**✓ DO** rapor yürütme hataları özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="9d182-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="9d182-111">**✓ CONSIDER** çağırarak işlem sonlandırılıyor `System.Environment.FailFast` (.NET Framework 2.0 özelliği) kodunuzu daha fazla yürütme için güvenli olduğu bir durumla karşılaşırsa yerine bir özel durum atma.</span><span class="sxs-lookup"><span data-stu-id="9d182-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="9d182-112">**X DO NOT** özel durumlar için normal akışı denetimi, mümkünse kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d182-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="9d182-113">Kullanıcıların özel durum oluşturmadığını kod yazabilmesi sistem hataları ve olası yarış durumlarını işlemleriyle dışında framework tasarımcıları API'leri tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d182-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="9d182-114">Örneğin, kullanıcılar özel durum oluşturmadığını kod yazabilmesi üyesi çağırmadan önce önkoşulları denetleme olanağı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d182-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="9d182-115">Başka bir üyesinin önkoşulları denetlemek için kullanılan bir üye genellikle test edici adlandırılır ve iş yapan üye bir doer çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9d182-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="9d182-116">Test edici Doer desenini kabul edilemez bir performansa sahip olabilir, durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9d182-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="9d182-117">Bu gibi durumlarda sözde deneyin-ayrıştırma desenindeki düşünülmesi gereken (bkz [özel durumlar ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="9d182-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="9d182-118">**✓ CONSIDER** özel durumları atma performans etkileri.</span><span class="sxs-lookup"><span data-stu-id="9d182-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="9d182-119">Saniye başına 100'ün üzerinde throw oranları, çoğu uygulama performansı önemli ölçüde etkiler olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="9d182-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="9d182-120">**✓ DO** belge herkese açık şekilde çağrılabilir üyeleri tarafından bir üye ihlali nedeniyle oluşturulan tüm özel durumları Sözleşme (bir sistem hatası yerine) ve bunları sizin sözleşmesinin bir parçası davran.</span><span class="sxs-lookup"><span data-stu-id="9d182-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="9d182-121">Sözleşmenin bir parçası olan özel durumlar sonraki bir sürümü değil değiştirilmelidir (yani, özel durum türü değiştirme ve yeni özel durumlar eklenmemelidir).</span><span class="sxs-lookup"><span data-stu-id="9d182-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="9d182-122">**X DO NOT** olması ya da throw veya yok edebilir Genel üyeler temel bazı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9d182-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="9d182-123">**X DO NOT** dönüş değeri olarak özel durumları döndüren Genel üyeler olması veya bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9d182-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="9d182-124">Özel durumlar, bunları atma yerine genel API'ler döndürme özel durum tabanlı hata raporlama avantajlarının birçoğundan faydalanılmasını boşa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9d182-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="9d182-125">**✓ CONSIDER** özel Oluşturucu yöntemleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="9d182-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="9d182-126">Farklı yerlerden aynı durum yaygındır.</span><span class="sxs-lookup"><span data-stu-id="9d182-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="9d182-127">Kod Şişirme önlemek için özel durumlar oluşturma ve bunların özelliklerini başlatır yardımcı yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d182-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="9d182-128">Ayrıca, özel durumlar üyeleri değil alıyorsanız satır içine alınmış.</span><span class="sxs-lookup"><span data-stu-id="9d182-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="9d182-129">Throw deyimi oluşturucu içinde taşıma, satır içine alınmayacak kadar üye izin vermeyi seçebilir.</span><span class="sxs-lookup"><span data-stu-id="9d182-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="9d182-130">**X DO NOT** özel durum filtresi taşlarından özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9d182-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="9d182-131">Özel durum filtresi özel durum harekete, CLR tarafından özel durum yakalandı ve filtre false döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d182-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="9d182-132">Bu davranış yürütme ile açıkça false döndüren filtresinden sihirden ve bu nedenle hata ayıklama oldukça zor.</span><span class="sxs-lookup"><span data-stu-id="9d182-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="9d182-133">**X AVOID** açıkça finally blokları özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="9d182-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="9d182-134">Throw yöntemleri çağırma özel durumlar oluşturulduğunda örtük olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9d182-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="9d182-135">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9d182-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9d182-136">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="9d182-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d182-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d182-137">See also</span></span>

- [<span data-ttu-id="9d182-138">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9d182-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="9d182-139">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9d182-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
