---
title: Sistem çalışma zamanı olaylarını yazın
description: TypeLoadStart ve TypeLoadStop gibi .NET tür sistemine özgü tanılama bilgilerini toplanan .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96589989"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="204dc-103">.NET çalışma zamanı türü olayları</span><span class="sxs-lookup"><span data-stu-id="204dc-103">.NET runtime type events</span></span>

<span data-ttu-id="204dc-104">Bu olaylar, yükleme türleriyle ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="204dc-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="204dc-105">Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="204dc-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="204dc-106">TypeLoadStart olayı</span><span class="sxs-lookup"><span data-stu-id="204dc-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="204dc-107">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="204dc-107">Keyword for raising the event</span></span>|<span data-ttu-id="204dc-108">Olay</span><span class="sxs-lookup"><span data-stu-id="204dc-108">Event</span></span>|<span data-ttu-id="204dc-109">Level</span><span class="sxs-lookup"><span data-stu-id="204dc-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="204dc-110">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="204dc-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="204dc-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="204dc-111">Informational (4)</span></span>|  

|<span data-ttu-id="204dc-112">Olay</span><span class="sxs-lookup"><span data-stu-id="204dc-112">Event</span></span>|<span data-ttu-id="204dc-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="204dc-113">Event ID</span></span>|<span data-ttu-id="204dc-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="204dc-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="204dc-115">73</span><span class="sxs-lookup"><span data-stu-id="204dc-115">73</span></span>|<span data-ttu-id="204dc-116">Bir tür yüklemesi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="204dc-116">A type load has started.</span></span>|

|<span data-ttu-id="204dc-117">Alan adı</span><span class="sxs-lookup"><span data-stu-id="204dc-117">Field name</span></span>|<span data-ttu-id="204dc-118">Veri türü</span><span class="sxs-lookup"><span data-stu-id="204dc-118">Data type</span></span>|<span data-ttu-id="204dc-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="204dc-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="204dc-120">Tür yükleme işleminin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="204dc-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="204dc-121">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="204dc-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="204dc-122">TypeLoadStop olayı</span><span class="sxs-lookup"><span data-stu-id="204dc-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="204dc-123">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="204dc-123">Keyword for raising the event</span></span>|<span data-ttu-id="204dc-124">Level</span><span class="sxs-lookup"><span data-stu-id="204dc-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="204dc-125">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="204dc-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="204dc-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="204dc-126">Informational (4)</span></span>|  

|<span data-ttu-id="204dc-127">Olay</span><span class="sxs-lookup"><span data-stu-id="204dc-127">Event</span></span>|<span data-ttu-id="204dc-128">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="204dc-128">Event ID</span></span>|<span data-ttu-id="204dc-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="204dc-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="204dc-130">74</span><span class="sxs-lookup"><span data-stu-id="204dc-130">74</span></span>|<span data-ttu-id="204dc-131">Bir tür yüklemesi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="204dc-131">A type load is finished.</span></span>|

|<span data-ttu-id="204dc-132">Alan adı</span><span class="sxs-lookup"><span data-stu-id="204dc-132">Field name</span></span>|<span data-ttu-id="204dc-133">Veri türü</span><span class="sxs-lookup"><span data-stu-id="204dc-133">Data type</span></span>|<span data-ttu-id="204dc-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="204dc-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="204dc-135">Tür yükleme işleminin KIMLIĞI (karşılık gelen TypeLoadStart olayının Typeloadstartıd ile eşleşir).</span><span class="sxs-lookup"><span data-stu-id="204dc-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="204dc-136">Yük düzeyini yazın.</span><span class="sxs-lookup"><span data-stu-id="204dc-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="204dc-137">Tür tanıtıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="204dc-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="204dc-138">Türün adı.</span><span class="sxs-lookup"><span data-stu-id="204dc-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="204dc-139">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="204dc-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
