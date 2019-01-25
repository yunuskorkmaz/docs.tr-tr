---
title: Çekişme ETW olayları - .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857651"
---
# <a name="contention-etw-events"></a><span data-ttu-id="5031b-102">Çekişme ETW olayları</span><span class="sxs-lookup"><span data-stu-id="5031b-102">Contention ETW events</span></span>

<span data-ttu-id="5031b-103">Çekişme olayları oluştuğunda için Çekişme olduğunda <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitler veya çalışma zamanı tarafından kullanılan yerel kilitler.</span><span class="sxs-lookup"><span data-stu-id="5031b-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="5031b-104">Başka bir iş parçacığı kilit sahip olduğu sırada bir kilit için bekleyen bir iş parçacığı Çekişme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5031b-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="5031b-105">Çekişme olayları altında oluşturulan anahtar sözcüğü ve olayları düzeyi aşağıdaki tabloda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5031b-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="5031b-106">Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5031b-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="5031b-107">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="5031b-107">Keyword for raising the event</span></span>|<span data-ttu-id="5031b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5031b-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5031b-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="5031b-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="5031b-110">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="5031b-110">Informational (4)</span></span>|

<span data-ttu-id="5031b-111">Aşağıdaki tabloda, olay bilgiler gösterir:</span><span class="sxs-lookup"><span data-stu-id="5031b-111">The following table shows event information:</span></span>

|<span data-ttu-id="5031b-112">Olay</span><span class="sxs-lookup"><span data-stu-id="5031b-112">Event</span></span>|<span data-ttu-id="5031b-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="5031b-113">Event ID</span></span>|<span data-ttu-id="5031b-114">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="5031b-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="5031b-115">81</span><span class="sxs-lookup"><span data-stu-id="5031b-115">81</span></span>|<span data-ttu-id="5031b-116">Çekişme başlatır.</span><span class="sxs-lookup"><span data-stu-id="5031b-116">Contention starts.</span></span> <span data-ttu-id="5031b-117">Bu olay, dönen bir iş parçacığı kilit için bekleyen önceki süre miktarını içermez; yalnızca iş parçacığının bir kilidi bekler olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="5031b-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="5031b-118">91</span><span class="sxs-lookup"><span data-stu-id="5031b-118">91</span></span>|<span data-ttu-id="5031b-119">Çekişme sona erer.</span><span class="sxs-lookup"><span data-stu-id="5031b-119">Contention ends.</span></span>|

<span data-ttu-id="5031b-120">Aşağıdaki tabloda, olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5031b-120">The following table shows event data:</span></span>

|<span data-ttu-id="5031b-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="5031b-121">Field name</span></span>|<span data-ttu-id="5031b-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="5031b-122">Data type</span></span>|<span data-ttu-id="5031b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5031b-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5031b-124">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="5031b-124">Flags</span></span>|<span data-ttu-id="5031b-125">Kazanma: UInt8</span><span class="sxs-lookup"><span data-stu-id="5031b-125">win:UInt8</span></span>|<span data-ttu-id="5031b-126">0 için yönetilen; Yerel için 1.</span><span class="sxs-lookup"><span data-stu-id="5031b-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="5031b-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5031b-127">ClrInstanceID</span></span>|<span data-ttu-id="5031b-128">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="5031b-128">win:UInt16</span></span>|<span data-ttu-id="5031b-129">CLR örneği için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="5031b-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5031b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5031b-130">See also</span></span>

- [<span data-ttu-id="5031b-131">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="5031b-131">CLR ETW Events</span></span>](clr-etw-events.md)
