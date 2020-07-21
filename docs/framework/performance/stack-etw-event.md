---
title: Yığın ETW Olayı
description: Bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılması gereken Stack ETW olayı hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474143"
---
# <a name="stack-etw-event"></a><span data-ttu-id="f380c-103">Yığın ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="f380c-103">Stack ETW Event</span></span>
<span data-ttu-id="f380c-104">Yığın olayı, bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f380c-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="f380c-105">Çalışma zamanı sağlayıcısı etkinleştirildiğinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f380c-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="f380c-106">Bu çok yüksek bir sıklık olayıdır, çünkü başka bir çalışma zamanı olayı oluşturulduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="f380c-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="f380c-107">Bu nedenle, bu olayı dikkatli kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f380c-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="f380c-108">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f380c-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f380c-109">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f380c-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f380c-110">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="f380c-110">Keyword for raising the event</span></span>|<span data-ttu-id="f380c-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="f380c-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f380c-112">`StackKeyword`0x40000000</span><span class="sxs-lookup"><span data-stu-id="f380c-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="f380c-113">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="f380c-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="f380c-114">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f380c-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f380c-115">Olay</span><span class="sxs-lookup"><span data-stu-id="f380c-115">Event</span></span>|<span data-ttu-id="f380c-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="f380c-116">Event ID</span></span>|<span data-ttu-id="f380c-117">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="f380c-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="f380c-118">82</span><span class="sxs-lookup"><span data-stu-id="f380c-118">82</span></span>|<span data-ttu-id="f380c-119">Bir olayı izleyen yığın izlemeleri oluşturmak için diğer olaylarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="f380c-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="f380c-120">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f380c-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f380c-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="f380c-121">Field name</span></span>|<span data-ttu-id="f380c-122">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f380c-122">Data Type</span></span>|<span data-ttu-id="f380c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f380c-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f380c-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f380c-124">ClrInstanceID</span></span>|<span data-ttu-id="f380c-125">Win: uint16</span><span class="sxs-lookup"><span data-stu-id="f380c-125">win:Uint16</span></span>|<span data-ttu-id="f380c-126">Benzersiz çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f380c-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="f380c-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="f380c-127">Reserved1</span></span>|<span data-ttu-id="f380c-128">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="f380c-128">win:UInt8</span></span>|<span data-ttu-id="f380c-129">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f380c-129">Reserved.</span></span>|  
|<span data-ttu-id="f380c-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="f380c-130">Reserved2</span></span>|<span data-ttu-id="f380c-131">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="f380c-131">win:UInt8</span></span>|<span data-ttu-id="f380c-132">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f380c-132">Reserved.</span></span>|  
|<span data-ttu-id="f380c-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="f380c-133">FrameCount</span></span>|<span data-ttu-id="f380c-134">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f380c-134">win:UInt32</span></span>|<span data-ttu-id="f380c-135">Yığın izlemesinde çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="f380c-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="f380c-136">Yığın</span><span class="sxs-lookup"><span data-stu-id="f380c-136">Stack</span></span>|<span data-ttu-id="f380c-137">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="f380c-137">win:Pointer</span></span>|<span data-ttu-id="f380c-138">Yönerge işaretçilerinin sütunları.</span><span class="sxs-lookup"><span data-stu-id="f380c-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f380c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f380c-139">See also</span></span>

- [<span data-ttu-id="f380c-140">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="f380c-140">CLR ETW Events</span></span>](clr-etw-events.md)
