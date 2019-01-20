---
title: Hata Ayıklama Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415331"
---
# <a name="debugging-structures"></a><span data-ttu-id="cc82a-102">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="cc82a-102">Debugging Structures</span></span>
<span data-ttu-id="cc82a-103">Bu bölümde, hata ayıklama API'SİNİN kullandığı yönetilmeyen yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc82a-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cc82a-104">In This Section</span></span>  
 [<span data-ttu-id="cc82a-105">CLR_DEBUGGING_VERSION Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="cc82a-106">Ürün sürümü, hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="cc82a-107">CodeChunkInfo Yapısı1</span><span class="sxs-lookup"><span data-stu-id="cc82a-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="cc82a-108">Tek bir öbek kod bellekte temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc82a-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="cc82a-109">CorDebugBlockingObject Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="cc82a-110">Bir iş parçacığı ve iş parçacığı neden engellenir nedeni engelleyen bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="cc82a-111">CorDebugEHClause Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="cc82a-112">Bir özel durum işleme (EH) yan tümcesi için Ara dil (IL) belirli bir parçasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cc82a-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="cc82a-113">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="cc82a-114">Temsil, çerçeve bilgileri bir özel durum nesnesinden yığın.</span><span class="sxs-lookup"><span data-stu-id="cc82a-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="cc82a-115">CorDebugExceptionObjectStackFrame Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="cc82a-116">Eşlemeleri bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] , karşılık gelen GUID [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="cc82a-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="cc82a-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="cc82a-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="cc82a-118">Bir iş parçacığının çerçevelerde şu an etkin olan işlevler hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="cc82a-119">COR_ARRAY_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="cc82a-120">Bir dizi nesnesinin bellek düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="cc82a-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="cc82a-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="cc82a-122">Yerel kod için Microsoft Ara dil (MSIL) kodu eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="cc82a-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="cc82a-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="cc82a-124">Kod aralığı uzaklık bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="cc82a-125">COR_FIELD Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="cc82a-126">Bir alan bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="cc82a-127">COR_GC_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="cc82a-128">Atık olarak toplanmış olacak bir nesneyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="cc82a-129">COR_HEAPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="cc82a-130">Numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="cc82a-131">COR_HEAPOBJECT Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="cc82a-132">Yönetilen yığındaki bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="cc82a-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="cc82a-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="cc82a-134">Değişiklikleri, bir işlevin göreli uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="cc82a-135">COR_SEGMENT Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="cc82a-136">Bellek yönetilen yığında bir bölge hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="cc82a-137">COR_TYPEID Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="cc82a-138">Tür tanımlayıcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="cc82a-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="cc82a-139">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="cc82a-140">Bellekte bir nesne düzeni hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="cc82a-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="cc82a-141">COR_VERSION</span></span>  
 <span data-ttu-id="cc82a-142">Ortak dil çalışma zamanı standart Dört bölümlü sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="cc82a-143">StackTrace_SimpleContext Yapısı</span><span class="sxs-lookup"><span data-stu-id="cc82a-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="cc82a-144">Tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="cc82a-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

 <span data-ttu-id="cc82a-145">[CLRDATA_ADDRESS_RANGE yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-145">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>
 
 <span data-ttu-id="cc82a-146">[CLRDATA_IL_ADDRESS_MAP yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) bir IL adresi eşleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-146">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>
 
 <span data-ttu-id="cc82a-147">[DacpGetModuleAddress yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) modülü adresi isteği için bir kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc82a-147">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

  
## <a name="related-sections"></a><span data-ttu-id="cc82a-148">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cc82a-148">Related Sections</span></span>  
 [<span data-ttu-id="cc82a-149">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="cc82a-149">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="cc82a-150">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cc82a-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="cc82a-151">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cc82a-151">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="cc82a-152">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="cc82a-152">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="cc82a-153">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cc82a-153">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
