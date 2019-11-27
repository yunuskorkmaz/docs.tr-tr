---
title: CLR ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941af2568e72fe093860801bd2595b3037e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428170"
---
# <a name="clr-etw-events"></a><span data-ttu-id="a44fb-102">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-102">CLR ETW Events</span></span>
<span data-ttu-id="a44fb-103">Bu bölümdeki konular, Windows için olay izleme (ETW) olaylarını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a44fb-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="a44fb-104">Her olayın ilişkili bir anahtar sözcüğü ve düzeyi vardır ve bu, [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md) konusunda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a44fb-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="a44fb-105">CLR, olaylar için iki sağlayıcıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a44fb-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="a44fb-106">Hangi anahtar kelimelerle (olay kategorileri) etkin olarak olay başlatan çalışma zamanı sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a44fb-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="a44fb-107">CLR çalışma zamanı sağlayıcısı GUID 'SI e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="a44fb-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="a44fb-108">Özel amaçlı kullanımları olan özet sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a44fb-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="a44fb-109">CLR özeti sağlayıcısı GUID 'SI A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="a44fb-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="a44fb-110">Sağlayıcılar hakkında daha fazla bilgi için bkz. [CLR ETW sağlayıcıları](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="a44fb-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a44fb-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a44fb-111">In This Section</span></span>  
 [<span data-ttu-id="a44fb-112">Çalışma Zamanı Bilgileri Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="a44fb-113">Çalışma zamanı hakkında SKU, sürüm numarası, çalışma zamanının etkinleştirildiği yol, ile başlatıldığı komut satırı parametreleri, GUID (varsa) ve diğer ilgili bilgiler dahil olmak üzere çalışma zamanı hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="a44fb-114">Özel Durum Thrown_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="a44fb-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="a44fb-115">Oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="a44fb-116">Çekişme Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="a44fb-117">İzleme kilitleri veya çalışma zamanının kullandığı yerel kilitler hakkında çekişme hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="a44fb-118">İş Parçacığı Havuzu Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="a44fb-119">Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="a44fb-120">Yükleyici Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="a44fb-121">Uygulama etki alanlarını, derlemeleri ve modülleri yükleme ve kaldırma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="a44fb-122">Yöntem Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="a44fb-123">Sembol çözümleme için CLR yöntemleriyle ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="a44fb-124">Atık Toplama Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="a44fb-125">Tanılama ve hata ayıklama konusunda yardımcı olmak için çöp koleksiyonuyla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="a44fb-126">Olayları Tam Zamanında İzleme</span><span class="sxs-lookup"><span data-stu-id="a44fb-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="a44fb-127">Tam zamanında (JıT) giriş ve kuyruk çağrıları hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="a44fb-128">Birlikte Çalışma Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="a44fb-129">Microsoft ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="a44fb-130">ARM Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="a44fb-131">Bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgilerini yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="a44fb-132">Güvenlik Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="a44fb-133">Tanımlayıcı ad ve Authenticode doğrulama hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="a44fb-134">Yığın Olayı</span><span class="sxs-lookup"><span data-stu-id="a44fb-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="a44fb-135">Bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılan bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="a44fb-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44fb-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a44fb-136">See also</span></span>

- [<span data-ttu-id="a44fb-137">ETW Ile hata ayıklama ve performans ayarlamayı geliştirme</span><span class="sxs-lookup"><span data-stu-id="a44fb-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="a44fb-138">Windows performans blogu</span><span class="sxs-lookup"><span data-stu-id="a44fb-138">Windows Performance Blog</span></span>](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/)
- [<span data-ttu-id="a44fb-139">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="a44fb-139">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="a44fb-140">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="a44fb-140">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="a44fb-141">CLR ETW Anahtar Sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="a44fb-141">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="a44fb-142">Ortak Dil Çalışma Zamanı Modülünde ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="a44fb-142">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
