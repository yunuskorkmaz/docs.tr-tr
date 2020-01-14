---
title: Ortak Dil Çalışma Zamanında ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: 49d1141540fb00ab7ef462da5af84f02e6d9fc4d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937864"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="8abec-102">Ortak Dil Çalışma Zamanında ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="8abec-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="8abec-103">Ortak dil çalışma zamanı (CLR), çok çeşitli hata ayıklama ve profil oluşturma olayları aracılığıyla Windows için yararlı olay izleme (ETW) tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8abec-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="8abec-104">CLR ETW olayları, ortak dil çalışma zamanı tarafından sunulan mevcut profil oluşturma ve hata ayıklama desteğini artırmak için Windows ETW izleme sisteminden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="8abec-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="8abec-105">ETW hakkında daha fazla bilgi için, [ETW Ile hata ayıklamayı ve performansı ayarlamayı geliştirme](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) makalesini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abec-105">More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article.</span></span> <span data-ttu-id="8abec-106">XPerf hakkında daha fazla bilgi için, NTDebugging blogdaki [Windows performans araç seti-XPerf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) girdisinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abec-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](https://docs.microsoft.com/archive/blogs/ntdebugging/windows-performance-toolkit-xperf) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="8abec-107">.NET Framework 4 veya üzeri, olay konularında açıklanan tüm olaylar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8abec-107">The .NET Framework 4 or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="8abec-108">Windows Vista işletim sistemi desteklenen en düşük istemcdir ve Windows Server 2008 desteklenen en düşük sunucu.</span><span class="sxs-lookup"><span data-stu-id="8abec-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8abec-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8abec-109">In This Section</span></span>  
 [<span data-ttu-id="8abec-110">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="8abec-110">Controlling .NET Framework Logging</span></span>](controlling-logging.md)  
 <span data-ttu-id="8abec-111">ETW olaylarını yakalamaya ve görüntülemeye yönelik araçları ve komutları açıklar.</span><span class="sxs-lookup"><span data-stu-id="8abec-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="8abec-112">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="8abec-112">CLR ETW Providers</span></span>](clr-etw-providers.md)  
 <span data-ttu-id="8abec-113">Çalışma zamanı ve Özet sağlayıcılar hakkında bilgi ve bunları ETW veri toplama için nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8abec-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="8abec-114">CLR ETW Anahtar Sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="8abec-114">CLR ETW Keywords and Levels</span></span>](clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="8abec-115">Olayların kategoriye göre filtrelenmesini sağlayan çalışma zamanı ve Özet sağlayıcılarının anahtar sözcüklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8abec-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="8abec-116">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="8abec-116">CLR ETW Events</span></span>](clr-etw-events.md)  
 <span data-ttu-id="8abec-117">CLR ETW olayları, anahtar kelimeleri, düzeyleri ve olay verileri hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8abec-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8abec-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8abec-118">See also</span></span>

- [<span data-ttu-id="8abec-119">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="8abec-119">ETW Events in the .NET Framework</span></span>](etw-events.md)
