---
title: Ortak Dil Çalışma Zamanında ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7855007c7566d3be0012bbff2cb124ee2681cb6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398059"
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="81a68-102">Ortak Dil Çalışma Zamanında ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="81a68-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="81a68-103">Ortak dil çalışma zamanı (CLR) Windows (ETW) tanı bilgilerini hata ayıklama ve profil oluşturma olayları büyük değişik için yararlı olay izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="81a68-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="81a68-104">CLR ETW olayları Windows ETW izleme sistemi varolan profil oluşturma ve hata ayıklama ortak dil çalışma zamanı tarafından sağlanan desteği büyütmek üzere yararlanın.</span><span class="sxs-lookup"><span data-stu-id="81a68-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="81a68-105">ETW hakkında daha fazla bilgi makalesinde kullanılabilir [artırmak hata ayıklama ve performans ayarlama ETW ile](http://go.microsoft.com/fwlink/?LinkID=161142) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="81a68-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="81a68-106">XPerf'in hakkında bilgi girişi bulunabilir [Windows Performans Araç Seti - XPerf'in](http://go.microsoft.com/fwlink/?LinkID=161144) NTDebugging Web günlüğündeki.</span><span class="sxs-lookup"><span data-stu-id="81a68-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="81a68-107">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Veya daha sonra tüm olayları olay açıklanan konular için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="81a68-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="81a68-108">Windows Vista işletim sisteminin en düşük desteklenen istemci ve Windows Server 2008 minimum desteklenen sunucu.</span><span class="sxs-lookup"><span data-stu-id="81a68-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81a68-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="81a68-109">In This Section</span></span>  
 [<span data-ttu-id="81a68-110">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="81a68-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="81a68-111">Yakalama ve ETW olayları görüntülemek için komutları ve araçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81a68-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="81a68-112">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="81a68-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="81a68-113">Çalışma zamanı ve özeti sağlayıcıları hakkında bilgi edinmek ve nasıl bunları ETW veri toplama için kullanabileceğiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="81a68-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="81a68-114">CLR ETW Anahtar Sözcükleri ve Düzeyler</span><span class="sxs-lookup"><span data-stu-id="81a68-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="81a68-115">Çalışma zamanı ve olayları kategoriye göre filtrelemeyi sağlamak özeti sağlayıcıları için anahtar sözcükleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="81a68-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="81a68-116">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="81a68-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="81a68-117">CLR ETW hakkında ayrıntılı bilgi olayları, anahtar sözcükler, düzeyleri ve olay verilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="81a68-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a68-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81a68-118">See Also</span></span>  
 [<span data-ttu-id="81a68-119">.NET Framework'te ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="81a68-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
