---
title: CLR ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: e879dcf385acbc522c0a3573cfa374550ea23333
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504129"
---
# <a name="clr-etw-events"></a><span data-ttu-id="20e3d-102">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-102">CLR ETW Events</span></span>
<span data-ttu-id="20e3d-103">Bu bölümdeki konular, Windows için olay izleme (ETW) olaylarını anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20e3d-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="20e3d-104">Her olayın ilişkili bir anahtar sözcüğü ve düzeyi vardır ve bu, [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md) konusunda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="20e3d-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="20e3d-105">CLR, olaylar için iki sağlayıcıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="20e3d-105">The CLR has two providers for the events:</span></span>  
  
- <span data-ttu-id="20e3d-106">Hangi anahtar kelimelerle (olay kategorileri) etkin olarak olay başlatan çalışma zamanı sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="20e3d-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="20e3d-107">CLR çalışma zamanı sağlayıcısı GUID 'SI e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="20e3d-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
- <span data-ttu-id="20e3d-108">Özel amaçlı kullanımları olan özet sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="20e3d-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="20e3d-109">CLR özeti sağlayıcısı GUID 'SI A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="20e3d-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="20e3d-110">Sağlayıcılar hakkında daha fazla bilgi için bkz. [CLR ETW sağlayıcıları](clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="20e3d-110">For more information about the providers, see [CLR ETW Providers](clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20e3d-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="20e3d-111">In This Section</span></span>  
 [<span data-ttu-id="20e3d-112">Çalışma Zamanı Bilgileri Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-112">Runtime Information Events</span></span>](runtime-information-etw-events.md)  
 <span data-ttu-id="20e3d-113">Çalışma zamanı hakkında SKU, sürüm numarası, çalışma zamanının etkinleştirildiği yol, ile başlatıldığı komut satırı parametreleri, GUID (varsa) ve diğer ilgili bilgiler dahil olmak üzere çalışma zamanı hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="20e3d-114">Özel Durum Thrown_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="20e3d-114">Exception Thrown_V1 Event</span></span>](exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="20e3d-115">Oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="20e3d-116">Çekişme Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-116">Contention Events</span></span>](contention-etw-events.md)  
 <span data-ttu-id="20e3d-117">İzleme kilitleri veya çalışma zamanının kullandığı yerel kilitler hakkında çekişme hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="20e3d-118">İş Parçacığı Havuzu Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-118">Thread Pool Events</span></span>](thread-pool-etw-events.md)  
 <span data-ttu-id="20e3d-119">Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="20e3d-120">Yükleyici Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-120">Loader Events</span></span>](loader-etw-events.md)  
 <span data-ttu-id="20e3d-121">Uygulama etki alanlarını, derlemeleri ve modülleri yükleme ve kaldırma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="20e3d-122">Yöntem Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-122">Method Events</span></span>](method-etw-events.md)  
 <span data-ttu-id="20e3d-123">Sembol çözümleme için CLR yöntemleriyle ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="20e3d-124">Atık Toplama Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-124">Garbage Collection Events</span></span>](garbage-collection-etw-events.md)  
 <span data-ttu-id="20e3d-125">Tanılama ve hata ayıklama konusunda yardımcı olmak için çöp koleksiyonuyla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="20e3d-126">Olayları Tam Zamanında İzleme</span><span class="sxs-lookup"><span data-stu-id="20e3d-126">JIT Tracing Events</span></span>](jit-tracing-etw-events.md)  
 <span data-ttu-id="20e3d-127">Tam zamanında (JıT) giriş ve kuyruk çağrıları hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="20e3d-128">Birlikte Çalışma Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-128">Interop Events</span></span>](interop-etw-events.md)  
 <span data-ttu-id="20e3d-129">Microsoft ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="20e3d-130">ARM Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-130">ARM Events</span></span>](application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="20e3d-131">Bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgilerini yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="20e3d-132">Güvenlik Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-132">Security Events</span></span>](security-etw-events.md)  
 <span data-ttu-id="20e3d-133">Tanımlayıcı ad ve Authenticode doğrulama hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="20e3d-134">Yığın Olayı</span><span class="sxs-lookup"><span data-stu-id="20e3d-134">Stack Event</span></span>](stack-etw-event.md)  
 <span data-ttu-id="20e3d-135">Bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılan bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="20e3d-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e3d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20e3d-136">See also</span></span>

- [<span data-ttu-id="20e3d-137">ETW Ile hata ayıklama ve performans ayarlamayı geliştirme</span><span class="sxs-lookup"><span data-stu-id="20e3d-137">Improve Debugging And Performance Tuning With ETW</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [<span data-ttu-id="20e3d-138">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="20e3d-138">Controlling .NET Framework Logging</span></span>](controlling-logging.md)
- [<span data-ttu-id="20e3d-139">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="20e3d-139">CLR ETW Providers</span></span>](clr-etw-providers.md)
- [<span data-ttu-id="20e3d-140">CLR ETW Anahtar Sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="20e3d-140">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)
- [<span data-ttu-id="20e3d-141">Ortak Dil Çalışma Zamanı Modülünde ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="20e3d-141">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
