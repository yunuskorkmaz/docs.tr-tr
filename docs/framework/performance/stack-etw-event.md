---
title: Yığın ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: f3014a04ba7cacbe37b6706e2919ffd7de19aa65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715918"
---
# <a name="stack-etw-event"></a><span data-ttu-id="587b8-102">Yığın ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="587b8-102">Stack ETW Event</span></span>
<span data-ttu-id="587b8-103">Yığın olayı, bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="587b8-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="587b8-104">Çalışma zamanı sağlayıcısı etkinleştirildiğinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="587b8-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="587b8-105">Bu çok yüksek bir sıklık olayıdır, çünkü başka bir çalışma zamanı olayı oluşturulduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="587b8-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="587b8-106">Bu nedenle, bu olayı dikkatli kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="587b8-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="587b8-107">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="587b8-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="587b8-108">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="587b8-108">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="587b8-109">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="587b8-109">Keyword for raising the event</span></span>|<span data-ttu-id="587b8-110">Düzey</span><span class="sxs-lookup"><span data-stu-id="587b8-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="587b8-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="587b8-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="587b8-112">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="587b8-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="587b8-113">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="587b8-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="587b8-114">Olay</span><span class="sxs-lookup"><span data-stu-id="587b8-114">Event</span></span>|<span data-ttu-id="587b8-115">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="587b8-115">Event ID</span></span>|<span data-ttu-id="587b8-116">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="587b8-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="587b8-117">82</span><span class="sxs-lookup"><span data-stu-id="587b8-117">82</span></span>|<span data-ttu-id="587b8-118">Bir olayı izleyen yığın izlemeleri oluşturmak için diğer olaylarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="587b8-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="587b8-119">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="587b8-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="587b8-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="587b8-120">Field name</span></span>|<span data-ttu-id="587b8-121">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="587b8-121">Data Type</span></span>|<span data-ttu-id="587b8-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="587b8-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="587b8-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="587b8-123">ClrInstanceID</span></span>|<span data-ttu-id="587b8-124">Win: uint16</span><span class="sxs-lookup"><span data-stu-id="587b8-124">win:Uint16</span></span>|<span data-ttu-id="587b8-125">Benzersiz çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="587b8-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="587b8-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="587b8-126">Reserved1</span></span>|<span data-ttu-id="587b8-127">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="587b8-127">win:UInt8</span></span>|<span data-ttu-id="587b8-128">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="587b8-128">Reserved.</span></span>|  
|<span data-ttu-id="587b8-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="587b8-129">Reserved2</span></span>|<span data-ttu-id="587b8-130">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="587b8-130">win:UInt8</span></span>|<span data-ttu-id="587b8-131">Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="587b8-131">Reserved.</span></span>|  
|<span data-ttu-id="587b8-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="587b8-132">FrameCount</span></span>|<span data-ttu-id="587b8-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="587b8-133">win:UInt32</span></span>|<span data-ttu-id="587b8-134">Yığın izlemesinde çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="587b8-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="587b8-135">Toplu İş</span><span class="sxs-lookup"><span data-stu-id="587b8-135">Stack</span></span>|<span data-ttu-id="587b8-136">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="587b8-136">win:Pointer</span></span>|<span data-ttu-id="587b8-137">Yönerge işaretçilerinin sütunları.</span><span class="sxs-lookup"><span data-stu-id="587b8-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="587b8-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="587b8-138">See also</span></span>

- [<span data-ttu-id="587b8-139">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="587b8-139">CLR ETW Events</span></span>](clr-etw-events.md)
