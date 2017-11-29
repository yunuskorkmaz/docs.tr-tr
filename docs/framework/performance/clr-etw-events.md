---
title: "CLR ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d0619388b429bd1824a62bc29ccb222eea1ffde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-etw-events"></a><span data-ttu-id="bc3e3-102">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-102">CLR ETW Events</span></span>
<span data-ttu-id="bc3e3-103">Bu bölümdeki konular Windows (ETW) olayları için olay izleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-103">The topics in this section describe event tracing for Windows (ETW) events.</span></span> <span data-ttu-id="bc3e3-104">Her olay bir ilişkili anahtar sözcüğü ve düzeyi, hangi açıklanan [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) konu.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-104">Each event has an associated keyword and level, which are described in the [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) topic.</span></span> <span data-ttu-id="bc3e3-105">CLR olayları için iki sağlayıcı sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bc3e3-105">The CLR has two providers for the events:</span></span>  
  
-   <span data-ttu-id="bc3e3-106">Çalışma zamanı sağlayıcı bağlı olarak anahtar sözcükler (olayların kategorilerini) etkinleştirildiği olayları başlatır.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-106">The runtime provider, which raises events depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="bc3e3-107">CLR çalışma zamanı GUID e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-107">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
-   <span data-ttu-id="bc3e3-108">Özel amaçlı sahip özeti sağlayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-108">The rundown provider, which has special-purpose uses.</span></span> <span data-ttu-id="bc3e3-109">CLR özeti GUID a669021c-c450-4609-a035-5af59af4df18 sağlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-109">The CLR rundown provider GUID is a669021c-c450-4609-a035-5af59af4df18.</span></span>  
  
 <span data-ttu-id="bc3e3-110">Sağlayıcılar hakkında daha fazla bilgi için bkz: [CLR ETW sağlayıcılar](../../../docs/framework/performance/clr-etw-providers.md).</span><span class="sxs-lookup"><span data-stu-id="bc3e3-110">For more information about the providers, see [CLR ETW Providers](../../../docs/framework/performance/clr-etw-providers.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc3e3-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bc3e3-111">In This Section</span></span>  
 [<span data-ttu-id="bc3e3-112">Çalışma zamanı bilgileri olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-112">Runtime Information Events</span></span>](../../../docs/framework/performance/runtime-information-etw-events.md)  
 <span data-ttu-id="bc3e3-113">SKU, sürüm numarası, hangi çalışma zamanı etkinleştirildi, şekilde de dahil olmak üzere çalışma zamanı, GUID ile (varsa), başlatıldığından komut satırı parametreleri hakkında bilgi ve diğer ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-113">Captures information about the runtime, including the SKU, version number, the manner in which the runtime was activated, the command-line parameters it was started with, the GUID (if applicable), and other relevant information.</span></span>  
  
 [<span data-ttu-id="bc3e3-114">Özel durum Thrown_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="bc3e3-114">Exception Thrown_V1 Event</span></span>](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 <span data-ttu-id="bc3e3-115">Oluşturulan özel durumlar hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-115">Captures information about exceptions that are thrown.</span></span>  
  
 [<span data-ttu-id="bc3e3-116">Çekişme olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-116">Contention Events</span></span>](../../../docs/framework/performance/contention-etw-events.md)  
 <span data-ttu-id="bc3e3-117">Çalışma zamanı kullanır İzleyici kilitleri veya yerel kilit çakışması hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-117">Captures information about contention for monitor locks or native locks that the runtime uses.</span></span>  
  
 [<span data-ttu-id="bc3e3-118">İş parçacığı havuzu olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-118">Thread Pool Events</span></span>](../../../docs/framework/performance/thread-pool-etw-events.md)  
 <span data-ttu-id="bc3e3-119">Çalışan iş parçacığı havuzları ve g/ç iş parçacığı havuzları hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-119">Captures information about worker thread pools and I/O thread pools.</span></span>  
  
 [<span data-ttu-id="bc3e3-120">Yükleyici olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-120">Loader Events</span></span>](../../../docs/framework/performance/loader-etw-events.md)  
 <span data-ttu-id="bc3e3-121">Yükleme ve kaldırma uygulama etki alanları, derlemeler ve modüller hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-121">Captures information about loading and unloading application domains, assemblies, and modules.</span></span>  
  
 [<span data-ttu-id="bc3e3-122">Yöntem olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-122">Method Events</span></span>](../../../docs/framework/performance/method-etw-events.md)  
 <span data-ttu-id="bc3e3-123">Simge çözünürlüğü için CLR yöntemleri hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-123">Captures information about CLR methods for symbol resolution.</span></span>  
  
 [<span data-ttu-id="bc3e3-124">Çöp toplama olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-124">Garbage Collection Events</span></span>](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 <span data-ttu-id="bc3e3-125">Çöp toplama, tanılama ve hata ayıklama yardımcı olmak için ilgili bilgiler yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-125">Captures information pertaining to garbage collection, to help in diagnostics and debugging.</span></span>  
  
 [<span data-ttu-id="bc3e3-126">JIT izleme olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-126">JIT Tracing Events</span></span>](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 <span data-ttu-id="bc3e3-127">Tam zamanında (JIT) satır içi kullanım ve kuyruk çağrıları hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-127">Captures information about just-in-time (JIT) inlining and tail calls.</span></span>  
  
 [<span data-ttu-id="bc3e3-128">Birlikte çalışma olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-128">Interop Events</span></span>](../../../docs/framework/performance/interop-etw-events.md)  
 <span data-ttu-id="bc3e3-129">Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-129">Captures information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 [<span data-ttu-id="bc3e3-130">ARM olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-130">ARM Events</span></span>](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 <span data-ttu-id="bc3e3-131">Uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-131">Captures detailed diagnostic information about the state of an application domain.</span></span>  
  
 [<span data-ttu-id="bc3e3-132">Güvenlik olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-132">Security Events</span></span>](../../../docs/framework/performance/security-etw-events.md)  
 <span data-ttu-id="bc3e3-133">Güçlü ad ve Authenticode doğrulama bilgilerini yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-133">Captures information about strong name and Authenticode verification.</span></span>  
  
 [<span data-ttu-id="bc3e3-134">Yığın olayı</span><span class="sxs-lookup"><span data-stu-id="bc3e3-134">Stack Event</span></span>](../../../docs/framework/performance/stack-etw-event.md)  
 <span data-ttu-id="bc3e3-135">Bir olay tetiklenir sonra Yığın izlemeleri oluşturmak için kullanılan diğer olaylarla bilgilerini yakalar.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-135">Captures information that is used with other events to generate stack traces after an event is raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc3e3-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc3e3-136">See Also</span></span>  
 [<span data-ttu-id="bc3e3-137">Hata ayıklama geliştirmek ve performans ile ETW ayarlama</span><span class="sxs-lookup"><span data-stu-id="bc3e3-137">Improve Debugging And Performance Tuning With ETW</span></span>](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [<span data-ttu-id="bc3e3-138">Windows Performans blogu</span><span class="sxs-lookup"><span data-stu-id="bc3e3-138">Windows Performance Blog</span></span>](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [<span data-ttu-id="bc3e3-139">.NET Framework günlük kaydını denetleme</span><span class="sxs-lookup"><span data-stu-id="bc3e3-139">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 [<span data-ttu-id="bc3e3-140">CLR ETW sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="bc3e3-140">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 [<span data-ttu-id="bc3e3-141">CLR ETW anahtar sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="bc3e3-141">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [<span data-ttu-id="bc3e3-142">Ortak dil çalışma zamanında ETW olayları</span><span class="sxs-lookup"><span data-stu-id="bc3e3-142">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
