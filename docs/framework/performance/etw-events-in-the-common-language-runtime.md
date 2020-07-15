---
title: Ortak Dil Çalışma Zamanında ETW Olayları
description: Bir Özeti okuyun ve ortak dil çalışma zamanı (CLR) içindeki Windows için olay izleme (ETW) olayları ile ilgili bağlantıları görüntüleyin.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: aa422dcb7efbc0f6f7f09e09a6c9e44b40ada86b
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309488"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="c54f2-103">Ortak Dil Çalışma Zamanında ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="c54f2-103">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="c54f2-104">Ortak dil çalışma zamanı (CLR), çok çeşitli hata ayıklama ve profil oluşturma olayları aracılığıyla Windows için yararlı olay izleme (ETW) tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c54f2-104">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="c54f2-105">CLR ETW olayları, ortak dil çalışma zamanı tarafından sunulan mevcut profil oluşturma ve hata ayıklama desteğini artırmak için Windows ETW izleme sisteminden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="c54f2-105">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="c54f2-106">ETW hakkında daha fazla bilgi için, [ETW Ile hata ayıklamayı ve performansı ayarlamayı geliştirme](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) makalesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c54f2-106">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="c54f2-107">XPerf hakkında daha fazla bilgi için, NTDebugging blogdaki [Windows performans araç seti-XPerf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) girdisinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c54f2-107">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="c54f2-108">.NET Framework 4 veya üzeri, olay konularında açıklanan tüm olaylar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c54f2-108">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="c54f2-109">Windows Vista işletim sistemi desteklenen en düşük istemcdir ve Windows Server 2008 desteklenen en düşük sunucu.</span><span class="sxs-lookup"><span data-stu-id="c54f2-109">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c54f2-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c54f2-110">In This Section</span></span>  
 [<span data-ttu-id="c54f2-111">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="c54f2-111">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="c54f2-112">ETW olaylarını yakalamaya ve görüntülemeye yönelik araçları ve komutları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c54f2-112">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="c54f2-113">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="c54f2-113">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="c54f2-114">Çalışma zamanı ve Özet sağlayıcılar hakkında bilgi ve bunları ETW veri toplama için nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c54f2-114">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="c54f2-115">CLR ETW Anahtar Sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="c54f2-115">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="c54f2-116">Olayların kategoriye göre filtrelenmesini sağlayan çalışma zamanı ve Özet sağlayıcılarının anahtar sözcüklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c54f2-116">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="c54f2-117">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="c54f2-117">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="c54f2-118">CLR ETW olayları, anahtar kelimeleri, düzeyleri ve olay verileri hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c54f2-118">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54f2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c54f2-119">See also</span></span>

- [<span data-ttu-id="c54f2-120">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="c54f2-120">ETW Events in the .NET Framework</span></span>](etw-events.md)
