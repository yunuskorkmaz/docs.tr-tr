---
title: Kilit çakışması çalışma zamanı olaylarını izleme
description: İzleyici kilit çekişmelerini özel bilgi toplamak için bkz. ETW olayları.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589998"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="816ce-103">.NET çalışma zamanı çekişme olayları</span><span class="sxs-lookup"><span data-stu-id="816ce-103">.NET runtime contention events</span></span>

<span data-ttu-id="816ce-104">Bu çalışma zamanı olayları `Monitor.Enter` , veya C# lock anahtar sözcüğü gibi izleyici kilit çekişmeleri hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="816ce-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="816ce-105">Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="816ce-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="816ce-106">ContentionStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="816ce-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="816ce-107">Bu olay, bir izleyici kilit çakışması başlangıcında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="816ce-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="816ce-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="816ce-108">Keyword for raising the event</span></span>|<span data-ttu-id="816ce-109">Level</span><span class="sxs-lookup"><span data-stu-id="816ce-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="816ce-110">`ContentionKeyword` 0x4000</span><span class="sxs-lookup"><span data-stu-id="816ce-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="816ce-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="816ce-111">Informational (4)</span></span>|

 <span data-ttu-id="816ce-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="816ce-112">The following table shows event information.</span></span>

|<span data-ttu-id="816ce-113">Olay</span><span class="sxs-lookup"><span data-stu-id="816ce-113">Event</span></span>|<span data-ttu-id="816ce-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="816ce-114">Event ID</span></span>|<span data-ttu-id="816ce-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="816ce-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="816ce-116">81</span><span class="sxs-lookup"><span data-stu-id="816ce-116">81</span></span>|<span data-ttu-id="816ce-117">İzleyici Kilidi çakışması başlar.</span><span class="sxs-lookup"><span data-stu-id="816ce-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="816ce-118">Alan adı</span><span class="sxs-lookup"><span data-stu-id="816ce-118">Field name</span></span>|<span data-ttu-id="816ce-119">Veri türü</span><span class="sxs-lookup"><span data-stu-id="816ce-119">Data type</span></span>|<span data-ttu-id="816ce-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="816ce-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="816ce-121">`0` yönetilen için; `1` yerel için.</span><span class="sxs-lookup"><span data-stu-id="816ce-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="816ce-122">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="816ce-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="816ce-123">ContentionStop_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="816ce-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="816ce-124">Bu olay, bir izleyici kilit çakışması sonunda yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="816ce-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="816ce-125">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="816ce-125">Keyword for raising the event</span></span>|<span data-ttu-id="816ce-126">Level</span><span class="sxs-lookup"><span data-stu-id="816ce-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="816ce-127">`ContentionKeyword` 0x4000</span><span class="sxs-lookup"><span data-stu-id="816ce-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="816ce-128">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="816ce-128">Informational (4)</span></span>|

 <span data-ttu-id="816ce-129">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="816ce-129">The following table shows event information.</span></span>

|<span data-ttu-id="816ce-130">Olay</span><span class="sxs-lookup"><span data-stu-id="816ce-130">Event</span></span>|<span data-ttu-id="816ce-131">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="816ce-131">Event ID</span></span>|<span data-ttu-id="816ce-132">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="816ce-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="816ce-133">91</span><span class="sxs-lookup"><span data-stu-id="816ce-133">91</span></span>|<span data-ttu-id="816ce-134">İzleyici Kilidi çakışması sona erer.</span><span class="sxs-lookup"><span data-stu-id="816ce-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="816ce-135">Alan adı</span><span class="sxs-lookup"><span data-stu-id="816ce-135">Field name</span></span>|<span data-ttu-id="816ce-136">Veri türü</span><span class="sxs-lookup"><span data-stu-id="816ce-136">Data type</span></span>|<span data-ttu-id="816ce-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="816ce-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="816ce-138">`0` yönetilen için; `1` yerel için.</span><span class="sxs-lookup"><span data-stu-id="816ce-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="816ce-139">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="816ce-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="816ce-140">Nanosaniye cinsinden çekişme süresi.</span><span class="sxs-lookup"><span data-stu-id="816ce-140">Duration of the contention in nanoseconds.</span></span>|
