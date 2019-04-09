---
title: Yığın ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076487"
---
# <a name="stack-etw-event"></a><span data-ttu-id="5fd7f-102">Yığın ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="5fd7f-102">Stack ETW Event</span></span>
<span data-ttu-id="5fd7f-103">Yığın olayı diğer olayları ile birlikte bir olay tetiklenir sonra yığın izlemelerini oluşturmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="5fd7f-104">Çalışma zamanı sağlayıcısı etkin olduğunda günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="5fd7f-105">Başka bir çalışma zamanı olayı her oluşturulur çünkü bir çok yüksek sıklık düzeyi olay budur.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="5fd7f-106">Bu nedenle, bu olay dikkatli kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="5fd7f-107">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="5fd7f-108">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="5fd7f-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5fd7f-109">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="5fd7f-109">Keyword for raising the event</span></span>|<span data-ttu-id="5fd7f-110">Düzey</span><span class="sxs-lookup"><span data-stu-id="5fd7f-110">Level</span></span>|  
|-----------------------------------|-----------|  
|`StackKeyword` <span data-ttu-id="5fd7f-111">(0x40000000)</span><span class="sxs-lookup"><span data-stu-id="5fd7f-111">(0x40000000)</span></span>|<span data-ttu-id="5fd7f-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="5fd7f-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="5fd7f-113">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="5fd7f-114">Olay</span><span class="sxs-lookup"><span data-stu-id="5fd7f-114">Event</span></span>|<span data-ttu-id="5fd7f-115">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="5fd7f-115">Event ID</span></span>|<span data-ttu-id="5fd7f-116">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="5fd7f-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="5fd7f-117">82</span><span class="sxs-lookup"><span data-stu-id="5fd7f-117">82</span></span>|<span data-ttu-id="5fd7f-118">Yığın izlemelerini izleyerek bir olay oluşturmak için diğer olaylarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="5fd7f-119">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="5fd7f-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="5fd7f-120">Field name</span></span>|<span data-ttu-id="5fd7f-121">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5fd7f-121">Data Type</span></span>|<span data-ttu-id="5fd7f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fd7f-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5fd7f-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5fd7f-123">ClrInstanceID</span></span>|<span data-ttu-id="5fd7f-124">Kazanma: Uint16</span><span class="sxs-lookup"><span data-stu-id="5fd7f-124">win:Uint16</span></span>|<span data-ttu-id="5fd7f-125">Benzersiz bir çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="5fd7f-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="5fd7f-126">Reserved1</span></span>|<span data-ttu-id="5fd7f-127">Kazanma: UInt8</span><span class="sxs-lookup"><span data-stu-id="5fd7f-127">win:UInt8</span></span>|<span data-ttu-id="5fd7f-128">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-128">Reserved.</span></span>|  
|<span data-ttu-id="5fd7f-129">Ayrılmış2</span><span class="sxs-lookup"><span data-stu-id="5fd7f-129">Reserved2</span></span>|<span data-ttu-id="5fd7f-130">Kazanma: UInt8</span><span class="sxs-lookup"><span data-stu-id="5fd7f-130">win:UInt8</span></span>|<span data-ttu-id="5fd7f-131">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-131">Reserved.</span></span>|  
|<span data-ttu-id="5fd7f-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="5fd7f-132">FrameCount</span></span>|<span data-ttu-id="5fd7f-133">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="5fd7f-133">win:UInt32</span></span>|<span data-ttu-id="5fd7f-134">Yığın izleme çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="5fd7f-135">Yığın</span><span class="sxs-lookup"><span data-stu-id="5fd7f-135">Stack</span></span>|<span data-ttu-id="5fd7f-136">Kazanma: işaretçi</span><span class="sxs-lookup"><span data-stu-id="5fd7f-136">win:Pointer</span></span>|<span data-ttu-id="5fd7f-137">Yönerge işaretçileri sütunlar.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fd7f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fd7f-138">See also</span></span>

- [<span data-ttu-id="5fd7f-139">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="5fd7f-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
