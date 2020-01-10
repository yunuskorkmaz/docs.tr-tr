---
title: Çekişme ETW olayları-.NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716131"
---
# <a name="contention-etw-events"></a><span data-ttu-id="49077-102">Çekişme ETW olayları</span><span class="sxs-lookup"><span data-stu-id="49077-102">Contention ETW events</span></span>

<span data-ttu-id="49077-103">Çekişme olayları, çalışma zamanı tarafından kullanılan <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitleri veya yerel kilitler için çekişme olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="49077-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="49077-104">Başka bir iş parçacığı kilitlemeye sahip olsa da bir iş parçacığı kilit beklerken bir çekişme meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="49077-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="49077-105">Aşağıdaki tabloda, çekişme olaylarının oluşturulduğu anahtar sözcüğü ve olayların düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="49077-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="49077-106">Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="49077-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="49077-107">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="49077-107">Keyword for raising the event</span></span>|<span data-ttu-id="49077-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="49077-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="49077-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="49077-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="49077-110">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="49077-110">Informational (4)</span></span>|

<span data-ttu-id="49077-111">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="49077-111">The following table shows event information:</span></span>

|<span data-ttu-id="49077-112">Olay</span><span class="sxs-lookup"><span data-stu-id="49077-112">Event</span></span>|<span data-ttu-id="49077-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="49077-113">Event ID</span></span>|<span data-ttu-id="49077-114">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="49077-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="49077-115">81</span><span class="sxs-lookup"><span data-stu-id="49077-115">81</span></span>|<span data-ttu-id="49077-116">Çekişme başlar.</span><span class="sxs-lookup"><span data-stu-id="49077-116">Contention starts.</span></span> <span data-ttu-id="49077-117">Bu olay, bir iş parçacığının bir kilit elde etmeden önce geçen dönme süresini içermez; yalnızca iş parçacığı bir kilit almayı bekliyorsa tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="49077-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="49077-118">91</span><span class="sxs-lookup"><span data-stu-id="49077-118">91</span></span>|<span data-ttu-id="49077-119">Çekişme bitiyor.</span><span class="sxs-lookup"><span data-stu-id="49077-119">Contention ends.</span></span>|

<span data-ttu-id="49077-120">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="49077-120">The following table shows event data:</span></span>

|<span data-ttu-id="49077-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="49077-121">Field name</span></span>|<span data-ttu-id="49077-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="49077-122">Data type</span></span>|<span data-ttu-id="49077-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49077-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="49077-124">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="49077-124">Flags</span></span>|<span data-ttu-id="49077-125">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="49077-125">win:UInt8</span></span>|<span data-ttu-id="49077-126">yönetilen için 0; Yerel için 1.</span><span class="sxs-lookup"><span data-stu-id="49077-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="49077-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="49077-127">ClrInstanceID</span></span>|<span data-ttu-id="49077-128">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="49077-128">win:UInt16</span></span>|<span data-ttu-id="49077-129">CLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="49077-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="49077-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49077-130">See also</span></span>

- [<span data-ttu-id="49077-131">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="49077-131">CLR ETW Events</span></span>](clr-etw-events.md)
