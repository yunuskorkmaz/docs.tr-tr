---
title: ICorDebugEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9afaeebfdb98a404ea53b0b5ec147f8c8104e14d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989072"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="1c4b8-102">ICorDebugEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c4b8-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="1c4b8-103">Hata ayıklama bir uygulama tarafından kullanılan numaralandırıcılar için soyut temel arayüz görev yapar.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c4b8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1c4b8-104">Methods</span></span>  
  
|<span data-ttu-id="1c4b8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1c4b8-105">Method</span></span>|<span data-ttu-id="1c4b8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c4b8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c4b8-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4b8-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="1c4b8-108">Bu bir kopyasını oluşturur `ICorDebugEnum` nesne.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="1c4b8-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4b8-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="1c4b8-110">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="1c4b8-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4b8-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="1c4b8-112">İmleç numaralandırma başlangıcına taşır.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="1c4b8-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c4b8-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="1c4b8-114">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c4b8-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c4b8-115">Remarks</span></span>  
 <span data-ttu-id="1c4b8-116">Aşağıdaki numaralandırıcılar türetilmesi `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="1c4b8-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="1c4b8-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="1c4b8-119">Icordebugblockingobjectenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="1c4b8-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-123">"Icordebugerrorınfoenum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="1c4b8-124">Icordebugexceptionobjectcallstackenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="1c4b8-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="1c4b8-126">Icordebuggcreferenceenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="1c4b8-127">Icordebugguidtotypeenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="1c4b8-128">Icordebugheapenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="1c4b8-129">Icordebugheapsegmentenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="1c4b8-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="1c4b8-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="1c4b8-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="1c4b8-137">Icordebugvariablehomeenum</span><span class="sxs-lookup"><span data-stu-id="1c4b8-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="1c4b8-138">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c4b8-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c4b8-139">Requirements</span></span>  
 <span data-ttu-id="1c4b8-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c4b8-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c4b8-141">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c4b8-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c4b8-142">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c4b8-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c4b8-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c4b8-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4b8-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c4b8-144">See also</span></span>

- [<span data-ttu-id="1c4b8-145">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1c4b8-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
