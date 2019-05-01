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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949155"
---
# <a name="stack-etw-event"></a><span data-ttu-id="64d4b-102">Yığın ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="64d4b-102">Stack ETW Event</span></span>
<span data-ttu-id="64d4b-103">Yığın olayı diğer olayları ile birlikte bir olay tetiklenir sonra yığın izlemelerini oluşturmak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="64d4b-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="64d4b-104">Çalışma zamanı sağlayıcısı etkin olduğunda günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="64d4b-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="64d4b-105">Başka bir çalışma zamanı olayı her oluşturulur çünkü bir çok yüksek sıklık düzeyi olay budur.</span><span class="sxs-lookup"><span data-stu-id="64d4b-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="64d4b-106">Bu nedenle, bu olay dikkatli kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="64d4b-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="64d4b-107">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="64d4b-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="64d4b-108">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="64d4b-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="64d4b-109">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="64d4b-109">Keyword for raising the event</span></span>|<span data-ttu-id="64d4b-110">Düzey</span><span class="sxs-lookup"><span data-stu-id="64d4b-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="64d4b-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="64d4b-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="64d4b-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="64d4b-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="64d4b-113">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64d4b-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="64d4b-114">Olay</span><span class="sxs-lookup"><span data-stu-id="64d4b-114">Event</span></span>|<span data-ttu-id="64d4b-115">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="64d4b-115">Event ID</span></span>|<span data-ttu-id="64d4b-116">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="64d4b-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="64d4b-117">82</span><span class="sxs-lookup"><span data-stu-id="64d4b-117">82</span></span>|<span data-ttu-id="64d4b-118">Yığın izlemelerini izleyerek bir olay oluşturmak için diğer olaylarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="64d4b-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="64d4b-119">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="64d4b-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="64d4b-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="64d4b-120">Field name</span></span>|<span data-ttu-id="64d4b-121">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="64d4b-121">Data Type</span></span>|<span data-ttu-id="64d4b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64d4b-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="64d4b-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="64d4b-123">ClrInstanceID</span></span>|<span data-ttu-id="64d4b-124">Kazanma: Uint16</span><span class="sxs-lookup"><span data-stu-id="64d4b-124">win:Uint16</span></span>|<span data-ttu-id="64d4b-125">Benzersiz bir çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="64d4b-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="64d4b-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="64d4b-126">Reserved1</span></span>|<span data-ttu-id="64d4b-127">Kazanma: UInt8</span><span class="sxs-lookup"><span data-stu-id="64d4b-127">win:UInt8</span></span>|<span data-ttu-id="64d4b-128">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="64d4b-128">Reserved.</span></span>|  
|<span data-ttu-id="64d4b-129">Ayrılmış2</span><span class="sxs-lookup"><span data-stu-id="64d4b-129">Reserved2</span></span>|<span data-ttu-id="64d4b-130">Kazanma: UInt8</span><span class="sxs-lookup"><span data-stu-id="64d4b-130">win:UInt8</span></span>|<span data-ttu-id="64d4b-131">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="64d4b-131">Reserved.</span></span>|  
|<span data-ttu-id="64d4b-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="64d4b-132">FrameCount</span></span>|<span data-ttu-id="64d4b-133">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="64d4b-133">win:UInt32</span></span>|<span data-ttu-id="64d4b-134">Yığın izleme çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="64d4b-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="64d4b-135">Yığın</span><span class="sxs-lookup"><span data-stu-id="64d4b-135">Stack</span></span>|<span data-ttu-id="64d4b-136">Kazanma: işaretçi</span><span class="sxs-lookup"><span data-stu-id="64d4b-136">win:Pointer</span></span>|<span data-ttu-id="64d4b-137">Yönerge işaretçileri sütunlar.</span><span class="sxs-lookup"><span data-stu-id="64d4b-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64d4b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64d4b-138">See also</span></span>

- [<span data-ttu-id="64d4b-139">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="64d4b-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
