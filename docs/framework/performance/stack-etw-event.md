---
title: Yığın ETW Olayı
description: Bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılması gereken Stack ETW olayı hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: 3b890e587abd5cb1b7315fe41897f24638fd4604
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236214"
---
# <a name="stack-etw-event"></a><span data-ttu-id="75f06-103">Yığın ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="75f06-103">Stack ETW Event</span></span>

<span data-ttu-id="75f06-104">Yığın olayı, bir olay oluşturulduktan sonra yığın izlemeleri oluşturmak için diğer olaylarla birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f06-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="75f06-105">Çalışma zamanı sağlayıcısı etkinleştirildiğinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="75f06-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="75f06-106">Bu çok yüksek bir sıklık olayıdır, çünkü başka bir çalışma zamanı olayı oluşturulduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="75f06-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="75f06-107">Bu nedenle, bu olayı dikkatli kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="75f06-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="75f06-108">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75f06-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="75f06-109">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="75f06-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="75f06-110">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="75f06-110">Keyword for raising the event</span></span>|<span data-ttu-id="75f06-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="75f06-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="75f06-112">`StackKeyword` 0x40000000</span><span class="sxs-lookup"><span data-stu-id="75f06-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="75f06-113">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="75f06-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="75f06-114">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75f06-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="75f06-115">Olay</span><span class="sxs-lookup"><span data-stu-id="75f06-115">Event</span></span>|<span data-ttu-id="75f06-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="75f06-116">Event ID</span></span>|<span data-ttu-id="75f06-117">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="75f06-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="75f06-118">82</span><span class="sxs-lookup"><span data-stu-id="75f06-118">82</span></span>|<span data-ttu-id="75f06-119">Bir olayı izleyen yığın izlemeleri oluşturmak için diğer olaylarla birlikte.</span><span class="sxs-lookup"><span data-stu-id="75f06-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="75f06-120">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75f06-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="75f06-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="75f06-121">Field name</span></span>|<span data-ttu-id="75f06-122">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="75f06-122">Data Type</span></span>|<span data-ttu-id="75f06-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f06-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="75f06-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="75f06-124">ClrInstanceID</span></span>|<span data-ttu-id="75f06-125">Win: uint16</span><span class="sxs-lookup"><span data-stu-id="75f06-125">win:Uint16</span></span>|<span data-ttu-id="75f06-126">Benzersiz çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="75f06-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="75f06-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="75f06-127">Reserved1</span></span>|<span data-ttu-id="75f06-128">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="75f06-128">win:UInt8</span></span>|<span data-ttu-id="75f06-129">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="75f06-129">Reserved.</span></span>|  
|<span data-ttu-id="75f06-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="75f06-130">Reserved2</span></span>|<span data-ttu-id="75f06-131">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="75f06-131">win:UInt8</span></span>|<span data-ttu-id="75f06-132">Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="75f06-132">Reserved.</span></span>|  
|<span data-ttu-id="75f06-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="75f06-133">FrameCount</span></span>|<span data-ttu-id="75f06-134">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="75f06-134">win:UInt32</span></span>|<span data-ttu-id="75f06-135">Yığın izlemesinde çerçeve sayısı.</span><span class="sxs-lookup"><span data-stu-id="75f06-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="75f06-136">Yığın</span><span class="sxs-lookup"><span data-stu-id="75f06-136">Stack</span></span>|<span data-ttu-id="75f06-137">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="75f06-137">win:Pointer</span></span>|<span data-ttu-id="75f06-138">Yönerge işaretçilerinin sütunları.</span><span class="sxs-lookup"><span data-stu-id="75f06-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75f06-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f06-139">See also</span></span>

- [<span data-ttu-id="75f06-140">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="75f06-140">CLR ETW Events</span></span>](clr-etw-events.md)
