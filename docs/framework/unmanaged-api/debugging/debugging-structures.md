---
title: "Hata Ayıklama Yapıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0293a20f5f735dd38b1d167ebc5057f645fa011a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-structures"></a><span data-ttu-id="97dbb-102">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="97dbb-102">Debugging Structures</span></span>
<span data-ttu-id="97dbb-103">Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97dbb-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97dbb-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="97dbb-104">In This Section</span></span>  
 [<span data-ttu-id="97dbb-105">Clr_debuggıng_versıon yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="97dbb-106">Hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) ürün sürümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="97dbb-107">Codechunkınfo Structure1</span><span class="sxs-lookup"><span data-stu-id="97dbb-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="97dbb-108">Tek bir Öbek bellek kod temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97dbb-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="97dbb-109">CorDebugBlockingObject yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="97dbb-110">Bir iş parçacığı ve iş parçacığı neden engellendi nedeni engelleyen bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="97dbb-111">CorDebugEHClause yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="97dbb-112">Bir özel durum işleme (EH) yan tümcesinin için belirli bir ara dile (IL) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97dbb-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="97dbb-113">CorDebugExceptionObjectStackFrame yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="97dbb-114">Bir özel durum nesnesi çerçeve bilgilerini temsil yığın.</span><span class="sxs-lookup"><span data-stu-id="97dbb-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="97dbb-115">CorDebugExceptionObjectStackFrame yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="97dbb-116">MAPS bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] ilgili GUID [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="97dbb-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="97dbb-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="97dbb-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="97dbb-118">Bir iş parçacığının çerçevelere şu an etkin olan işlevler hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="97dbb-119">COR_ARRAY_LAYOUT yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="97dbb-120">Bellekte bir dizi nesnesi düzen hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="97dbb-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="97dbb-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="97dbb-122">Yerel kod Microsoft Ara dili (MSIL) kodunu eşleştirmek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="97dbb-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="97dbb-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="97dbb-124">Kod bir aralık için uzaklık bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="97dbb-125">Cor_fıeld yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="97dbb-126">Bir nesne bir alanda hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="97dbb-127">COR_GC_REFERENCE yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="97dbb-128">Çöp toplanan olması için bir nesne hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="97dbb-129">Cor_heapınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="97dbb-130">Numaralandırılabilir olup olmadığını atık toplama yığın hakkında genel bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="97dbb-131">COR_HEAPOBJECT yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="97dbb-132">Yönetilen yığında bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="97dbb-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="97dbb-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="97dbb-134">Değişiklikler bir işlev göreli uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="97dbb-135">COR_SEGMENT yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="97dbb-136">Yönetilen yığın bellekte bir bölge hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="97dbb-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="97dbb-137">Cor_typeıd yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="97dbb-138">Tür tanımlayıcısı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="97dbb-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="97dbb-139">COR_TYPE_LAYOUT yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="97dbb-140">Bir nesnenin bellekte Düzen hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="97dbb-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="97dbb-141">COR_VERSION</span></span>  
 <span data-ttu-id="97dbb-142">Ortak dil çalışma zamanı standart dört bölümden oluşan sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="97dbb-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="97dbb-143">StackTrace_SimpleContext yapısı</span><span class="sxs-lookup"><span data-stu-id="97dbb-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="97dbb-144">Tam yerine kullanılabilir basit bir bağlam sağlar `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="97dbb-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="97dbb-145">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="97dbb-145">Related Sections</span></span>  
 [<span data-ttu-id="97dbb-146">Hata ayıklama coclass'ları</span><span class="sxs-lookup"><span data-stu-id="97dbb-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="97dbb-147">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97dbb-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="97dbb-148">Hata ayıklama genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="97dbb-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="97dbb-149">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="97dbb-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="97dbb-150">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="97dbb-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
