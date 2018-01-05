---
title: "Yığın ETW Olayı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1107c6608fe5136eb6159b1d4f0a438e95c4dabb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="94ec5-102">Yığın ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="94ec5-102">Stack ETW Event</span></span>
<span data-ttu-id="94ec5-103">Yığın olayı diğer olaylar ile birlikte bir olay tetiklenir sonra Yığın izlemeleri oluşturmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94ec5-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="94ec5-104">Çalışma zamanı sağlayıcısı etkinleştirildiğinde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="94ec5-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="94ec5-105">Başka bir çalışma zamanı olay tetiklenir her tetiklenir çok sık olay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="94ec5-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="94ec5-106">Bu nedenle, bu olay dikkatli bir şekilde kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="94ec5-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="94ec5-107">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="94ec5-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="94ec5-108">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="94ec5-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="94ec5-109">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="94ec5-109">Keyword for raising the event</span></span>|<span data-ttu-id="94ec5-110">Düzey</span><span class="sxs-lookup"><span data-stu-id="94ec5-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="94ec5-111">`StackKeyword`(0x40000000)</span><span class="sxs-lookup"><span data-stu-id="94ec5-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="94ec5-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="94ec5-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="94ec5-113">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="94ec5-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="94ec5-114">Olay</span><span class="sxs-lookup"><span data-stu-id="94ec5-114">Event</span></span>|<span data-ttu-id="94ec5-115">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="94ec5-115">Event ID</span></span>|<span data-ttu-id="94ec5-116">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="94ec5-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="94ec5-117">82</span><span class="sxs-lookup"><span data-stu-id="94ec5-117">82</span></span>|<span data-ttu-id="94ec5-118">Bir olay aşağıdaki Yığın izlemeleri oluşturmak için diğer olaylarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="94ec5-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="94ec5-119">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="94ec5-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="94ec5-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="94ec5-120">Field name</span></span>|<span data-ttu-id="94ec5-121">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="94ec5-121">Data Type</span></span>|<span data-ttu-id="94ec5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94ec5-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="94ec5-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="94ec5-123">ClrInstanceID</span></span>|<span data-ttu-id="94ec5-124">Win: Uint16</span><span class="sxs-lookup"><span data-stu-id="94ec5-124">win:Uint16</span></span>|<span data-ttu-id="94ec5-125">Benzersiz çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="94ec5-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="94ec5-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="94ec5-126">Reserved1</span></span>|<span data-ttu-id="94ec5-127">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="94ec5-127">win:UInt8</span></span>|<span data-ttu-id="94ec5-128">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="94ec5-128">Reserved.</span></span>|  
|<span data-ttu-id="94ec5-129">Ayrılmış2</span><span class="sxs-lookup"><span data-stu-id="94ec5-129">Reserved2</span></span>|<span data-ttu-id="94ec5-130">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="94ec5-130">win:UInt8</span></span>|<span data-ttu-id="94ec5-131">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="94ec5-131">Reserved.</span></span>|  
|<span data-ttu-id="94ec5-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="94ec5-132">FrameCount</span></span>|<span data-ttu-id="94ec5-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="94ec5-133">win:UInt32</span></span>|<span data-ttu-id="94ec5-134">Yığın izleme çerçevelere sayısı.</span><span class="sxs-lookup"><span data-stu-id="94ec5-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="94ec5-135">Yığın</span><span class="sxs-lookup"><span data-stu-id="94ec5-135">Stack</span></span>|<span data-ttu-id="94ec5-136">Win: işaretçi</span><span class="sxs-lookup"><span data-stu-id="94ec5-136">win:Pointer</span></span>|<span data-ttu-id="94ec5-137">Yönerge işaretçileri sütunlarının.</span><span class="sxs-lookup"><span data-stu-id="94ec5-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94ec5-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94ec5-138">See Also</span></span>  
 [<span data-ttu-id="94ec5-139">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="94ec5-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
