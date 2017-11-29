---
title: ManualResetEvent ve ManualResetEventSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="a14e1-102">ManualResetEvent ve ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="a14e1-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="a14e1-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Sınıfı işareti verilen sonra el ile sıfırlamanız gerekir bir yerel bekleme tanıtıcısı olayını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a14e1-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="a14e1-104">Bu sınıf temel sınıfı olan özel bir durum gösteren <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a14e1-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a14e1-105">Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) el ile özelliklerini ve kullanmak için kavramsal belgeler sıfırlama olaylar.</span><span class="sxs-lookup"><span data-stu-id="a14e1-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="a14e1-106">A <xref:System.Threading.ManualResetEvent> nesne kadar iş kalır, <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a14e1-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a14e1-107">Nesnenin durumu işaret ederken iş parçacığı veya işaret edilene sonra olayı bekle iş parçacığı bekleniyor, herhangi bir sayı serbest bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="a14e1-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="a14e1-108"><xref:System.Threading.ManualResetEvent>Win32 öğesine karşılık gelen `CreateEvent` çağrısı, belirtme `true` için `bManualReset` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a14e1-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="a14e1-109">İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> bekleme süresini çok kısa olması beklenen ve olay işlem sınır arası değil zamanı daha iyi performans için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a14e1-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="a14e1-110"><xref:System.Threading.ManualResetEventSlim>Olay işaret hale beklerken kısa bir süre dönmesini meşgul kullanır.</span><span class="sxs-lookup"><span data-stu-id="a14e1-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="a14e1-111">Bekleme süresini kısa, dönen bekleme tanıtıcıları kullanarak bekleme daha çok daha ucuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="a14e1-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="a14e1-112">Ancak, olay belirli bir zaman döneminde sinyal hale değil, <xref:System.Threading.ManualResetEventSlim> resorts normal olay işleyici bekleyin.</span><span class="sxs-lookup"><span data-stu-id="a14e1-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14e1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a14e1-113">See Also</span></span>  
 [<span data-ttu-id="a14e1-114">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a14e1-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="a14e1-115">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="a14e1-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="a14e1-116">Bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="a14e1-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="a14e1-117">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a14e1-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="a14e1-118">SpinWait</span><span class="sxs-lookup"><span data-stu-id="a14e1-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="a14e1-119">Semafor ve SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="a14e1-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
