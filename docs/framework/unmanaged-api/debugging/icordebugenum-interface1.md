---
title: Icordebugenum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEnum
helpviewer_keywords: ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751cca87962473501ef29a4deb99d9d24be33396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="4c174-102">Icordebugenum Interface1</span><span class="sxs-lookup"><span data-stu-id="4c174-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="4c174-103">Hata ayıklama bir uygulama tarafından kullanılan numaralandırmalar için Özet temel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="4c174-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c174-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c174-104">Methods</span></span>  
  
|<span data-ttu-id="4c174-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4c174-105">Method</span></span>|<span data-ttu-id="4c174-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c174-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c174-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c174-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="4c174-108">Bu bir kopyasını oluşturur `ICorDebugEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4c174-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="4c174-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c174-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="4c174-110">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4c174-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="4c174-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c174-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="4c174-112">İmleç numaralandırması başlangıcına taşır.</span><span class="sxs-lookup"><span data-stu-id="4c174-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="4c174-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c174-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="4c174-114">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="4c174-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c174-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c174-115">Remarks</span></span>  
 <span data-ttu-id="4c174-116">Aşağıdaki numaralandırıcılar türetin `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="4c174-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="4c174-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="4c174-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="4c174-119">Icordebugblockingobjectenum</span><span class="sxs-lookup"><span data-stu-id="4c174-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="4c174-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="4c174-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="4c174-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="4c174-123">"Icordebugerrorınfoenum"</span><span class="sxs-lookup"><span data-stu-id="4c174-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="4c174-124">Icordebugexceptionobjectcallstackenum</span><span class="sxs-lookup"><span data-stu-id="4c174-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="4c174-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="4c174-126">Icordebuggcreferenceenum</span><span class="sxs-lookup"><span data-stu-id="4c174-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="4c174-127">Icordebugguidtotypeenum</span><span class="sxs-lookup"><span data-stu-id="4c174-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="4c174-128">Icordebugheapenum</span><span class="sxs-lookup"><span data-stu-id="4c174-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="4c174-129">Icordebugheapsegmentenum</span><span class="sxs-lookup"><span data-stu-id="4c174-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="4c174-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="4c174-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="4c174-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="4c174-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="4c174-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="4c174-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="4c174-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="4c174-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="4c174-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="4c174-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="4c174-138">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4c174-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c174-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c174-139">Requirements</span></span>  
 <span data-ttu-id="4c174-140">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c174-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c174-141">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c174-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c174-142">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c174-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c174-143">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c174-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c174-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c174-144">See Also</span></span>  
 [<span data-ttu-id="4c174-145">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c174-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
