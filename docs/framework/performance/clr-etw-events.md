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
ms.openlocfilehash: d7d1f7ba1a0384ed93932733f12aa3306e16b790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393925"
---
# <a name="clr-etw-events"></a><span data-ttu-id="46b3d-102">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-102">CLR ETW Events</span></span>
<span data-ttu-id="46b3d-103">Bu bölümdeki konular Windows (ETW) olayları için olay izleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="46b3d-104">Her olay bir ilişkili anahtar sözcüğü ve düzeyi, hangi açıklanan [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) konu.</span><span class="sxs-lookup"><span data-stu-id="46b3d-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="46b3d-105">CLR olayları için iki sağlayıcı sahiptir:</span><span class="sxs-lookup"><span data-stu-id="46b3d-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="46b3d-106">Çalışma zamanı sağlayıcı bağlı olarak anahtar sözcükler (olayların kategorilerini) etkinleştirildiği olayları başlatır.</span><span class="sxs-lookup"><span data-stu-id="46b3d-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="46b3d-107">CLR çalışma zamanı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="46b3d-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="46b3d-108">Özel amaçlı sahip özeti sağlayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="46b3d-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="46b3d-109">CLR özeti GUID a669021c-c450-4609-a035-5af59af4df18 sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="46b3d-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="46b3d-110">Sağlayıcılar hakkında daha fazla bilgi için bkz: [CLR ETW sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="46b3d-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46b3d-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="46b3d-111">In This Section</span></span>  
 [<span data-ttu-id="46b3d-112">Çalışma Zamanı Bilgileri Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="46b3d-113">SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde de dahil olmak üzere çalışma zamanı, GUID ile (varsa), başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="46b3d-114">Özel Durum Thrown_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="46b3d-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="46b3d-115">Oluşturulan özel durumlar hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="46b3d-116">Çekişme Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="46b3d-117">Çalışma zamanı kullanır İzleyici kilitleri veya yerel kilit çakışması hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="46b3d-118">İş Parçacığı Havuzu Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="46b3d-119">Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="46b3d-120">Yükleyici Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="46b3d-121">Yükleme ve kaldırma uygulama etki alanları, derlemeler ve modüller hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="46b3d-122">Yöntem Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="46b3d-123">Simge çözünürlüğü için CLR yöntemleri hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="46b3d-124">Atık Toplama Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="46b3d-125">Çöp toplama, tanılama ve hata ayıklama yardımcı olmak için ilgili bilgiler yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="46b3d-126">Olayları Tam Zamanında İzleme</span><span class="sxs-lookup"><span data-stu-id="46b3d-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="46b3d-127">Tam zamanında (JIT) satır içi kullanım ve kuyruk çağrıları hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="46b3d-128">Birlikte Çalışma Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="46b3d-129">Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="46b3d-130">ARM Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="46b3d-131">Uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="46b3d-132">Güvenlik Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="46b3d-133">Güçlü ad ve Authenticode doğrulama bilgilerini yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="46b3d-134">Yığın Olayı</span><span class="sxs-lookup"><span data-stu-id="46b3d-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="46b3d-135">Bir olay tetiklenir sonra Yığın izlemeleri oluşturmak için kullanılan diğer olaylarla bilgilerini yakalar.</span><span class="sxs-lookup"><span data-stu-id="46b3d-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b3d-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46b3d-136">See Also</span></span>  
 [<span data-ttu-id="46b3d-137">Hata ayıklama geliştirmek ve performans ile ETW ayarlama</span><span class="sxs-lookup"><span data-stu-id="46b3d-137">Improve Debugging And Performance Tuning With ETW</span></span>](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [<span data-ttu-id="46b3d-138">Windows Performans blogu</span><span class="sxs-lookup"><span data-stu-id="46b3d-138">Windows Performance Blog</span></span>](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [<span data-ttu-id="46b3d-139">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="46b3d-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 [<span data-ttu-id="46b3d-140">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="46b3d-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 [<span data-ttu-id="46b3d-141">CLR ETW Anahtar Sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="46b3d-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [<span data-ttu-id="46b3d-142">Ortak Dil Çalışma Zamanı Modülünde ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="46b3d-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
