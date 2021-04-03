---
title: Çalıştırma zamanı olayları
description: ETW, LTTng veya EventPipe ile kullanılabilen .NET Runtime (CoreCLR) tarafından yayılan Tanılama olaylarını gözden geçirin.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589997"
---
# <a name="net-runtime-events"></a><span data-ttu-id="90498-103">.NET çalışma zamanı olayları</span><span class="sxs-lookup"><span data-stu-id="90498-103">.NET runtime events</span></span>

<span data-ttu-id="90498-104">.NET çalışma zamanı (CoreCLR),, ve gibi çeşitli mekanizmalarla tüketilebilen .NET uygulamanızla ilgili sorunları tanılamak için kullanılabilecek çeşitli olayları yayar `ETW` `LTTng` `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="90498-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="90498-105">Bu belge .NET Core çalışma zamanı tarafından tetiklenen olaylara başvuru görevi görür.</span><span class="sxs-lookup"><span data-stu-id="90498-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="90498-106">.NET Framework çalışma zamanı olayları için bkz. [CLR ETW olayları](../../framework/performance/clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="90498-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="90498-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="90498-107">In this section</span></span>

<span data-ttu-id="90498-108">[Çekişme olayları](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="90498-109">Bu olaylar izleyici kilitleme çekişmeleri hakkında bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="90498-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="90498-110">[Çöp toplama olayları](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="90498-111">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="90498-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="90498-112">Çöp toplamanın kaç kez gerçekleştirildiğini belirleme, çöp toplama sırasında ne kadar bellek serbest bırakılmış vb. gibi tanılama ve hata ayıklama konusunda yardımcı olurlar.</span><span class="sxs-lookup"><span data-stu-id="90498-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="90498-113">[Özel durum olayları](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="90498-114">Bu çalışma zamanı olayları, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="90498-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="90498-115">[Birlikte çalışma olayları](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="90498-116">Bu çalışma zamanı olayları ortak ara dil (CıL) saplama oluşturma hakkındaki bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="90498-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="90498-117">[Yükleyici ve Ciltçi olayları](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="90498-118">Bu olaylar derlemeleri ve modülleri yükleme ve kaldırma ile ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="90498-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="90498-119">[Yöntem olayları](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="90498-120">Bu olaylar yöntemlere özgü bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="90498-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="90498-121">Bu olayların yükü sembol çözümlemesi için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="90498-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="90498-122">Ayrıca, bu olaylar yöntemin kaç kez çağrıldığı gibi yararlı bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="90498-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="90498-123">[İş parçacığı olayları](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="90498-124">Bu olaylar, çalışan ve g/ç iş parçacıkları hakkında bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="90498-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="90498-125">[Tür olayları](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="90498-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="90498-126">Bu olaylar tür sistemi hakkında bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="90498-126">These events collect information about the type system.</span></span>
