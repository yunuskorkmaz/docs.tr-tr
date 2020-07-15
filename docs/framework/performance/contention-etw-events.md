---
title: Çekişme ETW olayları-.NET
description: System. Threading. Monitor kilitleri veya çalışma zamanı tarafından kullanılan yerel kilitler için çekişme olduğunda oluşan çekişme ETW olayları hakkında ayrıntılı bilgi alın.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309607"
---
# <a name="contention-etw-events"></a><span data-ttu-id="810d0-103">Çekişme ETW olayları</span><span class="sxs-lookup"><span data-stu-id="810d0-103">Contention ETW events</span></span>

<span data-ttu-id="810d0-104">Çekişme, <xref:System.Threading.Monitor?displayProperty=nameWithType> çalışma zamanı tarafından kullanılan kilitler veya yerel kilitler için çekişme olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="810d0-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="810d0-105">Başka bir iş parçacığı kilitlemeye sahip olsa da bir iş parçacığı kilit beklerken bir çekişme meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="810d0-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="810d0-106">Aşağıdaki tabloda, çekişme olaylarının oluşturulduğu anahtar sözcüğü ve olayların düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="810d0-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="810d0-107">Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="810d0-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="810d0-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="810d0-108">Keyword for raising the event</span></span>|<span data-ttu-id="810d0-109">Düzey</span><span class="sxs-lookup"><span data-stu-id="810d0-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="810d0-110">`ContentionKeyword`0x4000</span><span class="sxs-lookup"><span data-stu-id="810d0-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="810d0-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="810d0-111">Informational (4)</span></span>|

<span data-ttu-id="810d0-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="810d0-112">The following table shows event information:</span></span>

|<span data-ttu-id="810d0-113">Olay</span><span class="sxs-lookup"><span data-stu-id="810d0-113">Event</span></span>|<span data-ttu-id="810d0-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="810d0-114">Event ID</span></span>|<span data-ttu-id="810d0-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="810d0-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="810d0-116">81</span><span class="sxs-lookup"><span data-stu-id="810d0-116">81</span></span>|<span data-ttu-id="810d0-117">Çekişme başlar.</span><span class="sxs-lookup"><span data-stu-id="810d0-117">Contention starts.</span></span> <span data-ttu-id="810d0-118">Bu olay, bir iş parçacığının bir kilit elde etmeden önce geçen dönme süresini içermez; yalnızca iş parçacığı bir kilit almayı bekliyorsa tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="810d0-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="810d0-119">91</span><span class="sxs-lookup"><span data-stu-id="810d0-119">91</span></span>|<span data-ttu-id="810d0-120">Çekişme bitiyor.</span><span class="sxs-lookup"><span data-stu-id="810d0-120">Contention ends.</span></span>|

<span data-ttu-id="810d0-121">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="810d0-121">The following table shows event data:</span></span>

|<span data-ttu-id="810d0-122">Alan adı</span><span class="sxs-lookup"><span data-stu-id="810d0-122">Field name</span></span>|<span data-ttu-id="810d0-123">Veri türü</span><span class="sxs-lookup"><span data-stu-id="810d0-123">Data type</span></span>|<span data-ttu-id="810d0-124">Description</span><span class="sxs-lookup"><span data-stu-id="810d0-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="810d0-125">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="810d0-125">Flags</span></span>|<span data-ttu-id="810d0-126">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="810d0-126">win:UInt8</span></span>|<span data-ttu-id="810d0-127">yönetilen için 0; Yerel için 1.</span><span class="sxs-lookup"><span data-stu-id="810d0-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="810d0-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="810d0-128">ClrInstanceID</span></span>|<span data-ttu-id="810d0-129">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="810d0-129">win:UInt16</span></span>|<span data-ttu-id="810d0-130">CLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="810d0-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="810d0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="810d0-131">See also</span></span>

- [<span data-ttu-id="810d0-132">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="810d0-132">CLR ETW Events</span></span>](clr-etw-events.md)
