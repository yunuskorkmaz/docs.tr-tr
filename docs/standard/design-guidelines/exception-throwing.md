---
title: "Özel durum atma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2c1fc02b64a494220070a1cfed928b616e4970c0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="exception-throwing"></a><span data-ttu-id="c6588-102">Özel durum atma</span><span class="sxs-lookup"><span data-stu-id="c6588-102">Exception Throwing</span></span>
<span data-ttu-id="c6588-103">Bu bölümde açıklanan özel durum atma yönergeleri yürütme hatası anlamını iyi tanımının gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c6588-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="c6588-104">Yürütme hatası oluşursa üyesi ne olduğunu yapamayacağı her (ne üye adından da anlaşılacağı) yapmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6588-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="c6588-105">Örneğin, varsa `OpenFile` yöntemi bir açılan dosya tanıtıcısı çağırana döndüremiyor, bir yürütme hatası kabul edilmesi.</span><span class="sxs-lookup"><span data-stu-id="c6588-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="c6588-106">Çoğu geliştirici özel durumlar bölme gibi kullanım hatalar için sıfır ya da null başvurular kullanabileceğinizden hale getirildi.</span><span class="sxs-lookup"><span data-stu-id="c6588-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="c6588-107">Framework'te özel durumları yürütme hatalar dahil olmak üzere tüm hata koşulları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6588-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="c6588-108">**X yok** hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6588-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="c6588-109">İstisnaları çerçeveleri hatalarını raporlama birincil anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c6588-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="c6588-110">**✓ YAPMAK** rapor yürütme hataları özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="c6588-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="c6588-111">**✓ DÜŞÜNÜN** çağırarak işlem sonlandırılıyor `System.Environment.FailFast` (.NET Framework 2.0 özelliği) kodunuzu daha fazla yürütme için güvenli olduğu bir durumla karşılaşırsa yerine bir özel durum atma.</span><span class="sxs-lookup"><span data-stu-id="c6588-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="c6588-112">**X yok** özel durumlar için normal akışı denetimi, mümkünse kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6588-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="c6588-113">Kullanıcıların özel durumlar oluşturmadığını kod yazabilirsiniz şekilde sistem hataları ve olası yarış durumlarını işlemleriyle dışında framework tasarımcıları API'leri tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6588-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="c6588-114">Örneğin, kullanıcıların özel durumlar oluşturmadığını kod yazabilirsiniz şekilde üyesi çağırmadan önce önkoşulları kontrol etmenin bir yolu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c6588-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="c6588-115">Başka bir üyesinin önkoşulları denetlemek için kullanılan üye genellikle tester adlandırılır ve gerçekte çalışır üye bir doer çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c6588-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="c6588-116">Kabul edilebilir bir performansa Tester Doer düzeni olabilir, durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="c6588-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="c6588-117">Böyle durumlarda, sözde deneyin ayrıştırma düzeni bulundurulması gerekir (bkz [özel durumları ve performans](../../../docs/standard/design-guidelines/exceptions-and-performance.md) daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="c6588-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="c6588-118">**✓ DÜŞÜNÜN** özel durumları atma performans etkileri.</span><span class="sxs-lookup"><span data-stu-id="c6588-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="c6588-119">Throw hızlarını saniyede 100 yukarıda büyük bir olasılıkla çoğu uygulamalarının performansını önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c6588-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="c6588-120">**✓ YAPMAK** belge herkese açık şekilde çağrılabilir üyeleri tarafından bir üye ihlali nedeniyle oluşturulan tüm özel durumları Sözleşme (bir sistem hatası yerine) ve bunları sizin sözleşmesinin bir parçası davran.</span><span class="sxs-lookup"><span data-stu-id="c6588-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="c6588-121">Sözleşmenin parçası olan özel durumlar değiştirme bir sürümünden sonraki (yani, özel durum türü değiştirme ve yeni özel durumlar eklenmemelidir).</span><span class="sxs-lookup"><span data-stu-id="c6588-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="c6588-122">**X yok** olması ya da throw veya yok edebilir Genel üyeler temel bazı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="c6588-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="c6588-123">**X yok** dönüş değeri olarak özel durumları döndüren Genel üyeler olması veya bir `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c6588-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="c6588-124">Bunları atma yerine ortak API'ler özel durumlar döndürme birçok özel durum tabanlı hata raporlama avantajı defeats.</span><span class="sxs-lookup"><span data-stu-id="c6588-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="c6588-125">**✓ DÜŞÜNÜN** özel Oluşturucu yöntemleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="c6588-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="c6588-126">Farklı yerlerden aynı özel durum yaygındır.</span><span class="sxs-lookup"><span data-stu-id="c6588-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="c6588-127">Kod oluşan şişirmeyi önlemek için özel durumlar oluşturma ve bunların özelliklerini başlatma yardımcı yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c6588-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="c6588-128">Ayrıca, özel durumlar oluşturma üyeleri değil aldıklarından içermesinden.</span><span class="sxs-lookup"><span data-stu-id="c6588-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="c6588-129">Throw deyimi oluşturucu içinde taşıma üye içermesinden olmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c6588-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="c6588-130">**X yok** özel durum filtresi taşlarından özel durumlar oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c6588-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="c6588-131">Bir özel durum filtresi bir özel durum oluşturur, CLR tarafından özel durum yakalandı ve filtre false döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6588-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="c6588-132">Bu davranış yürütme ve açıkça false değerinin döndürülmesi filtresinden ayırt ve bu nedenle hata ayıklamak çok zordur.</span><span class="sxs-lookup"><span data-stu-id="c6588-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="c6588-133">**KAÇININ x** açıkça finally blokları özel durumları atma.</span><span class="sxs-lookup"><span data-stu-id="c6588-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="c6588-134">Throw yöntemleri çağırma sonucu oluşan örtük olarak atılmış özel durumları kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c6588-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="c6588-135">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="c6588-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c6588-136">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="c6588-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6588-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6588-137">See Also</span></span>  
 [<span data-ttu-id="c6588-138">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c6588-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="c6588-139">Özel Durumlar için Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c6588-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
