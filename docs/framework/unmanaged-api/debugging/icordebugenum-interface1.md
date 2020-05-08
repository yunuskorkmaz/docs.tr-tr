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
ms.openlocfilehash: 7575be3f5074243b251c80b8dd5bdbb12e5d50fd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976336"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="c3ddf-102">ICorDebugEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3ddf-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="c3ddf-103">Bir hata ayıklama uygulaması tarafından kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3ddf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c3ddf-104">Methods</span></span>  
  
|<span data-ttu-id="c3ddf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c3ddf-105">Method</span></span>|<span data-ttu-id="c3ddf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3ddf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3ddf-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ddf-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="c3ddf-108">Bu `ICorDebugEnum` nesnenin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="c3ddf-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ddf-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="c3ddf-110">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="c3ddf-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ddf-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="c3ddf-112">İmleci numaralandırmanın başlangıcına kaydırır.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="c3ddf-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ddf-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="c3ddf-114">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3ddf-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3ddf-115">Remarks</span></span>  
 <span data-ttu-id="c3ddf-116">Aşağıdaki Numaralandırıcılar öğesinden `ICorDebugEnum`türetilir:</span><span class="sxs-lookup"><span data-stu-id="c3ddf-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="c3ddf-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="c3ddf-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="c3ddf-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="c3ddf-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="c3ddf-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="c3ddf-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="c3ddf-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="c3ddf-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="c3ddf-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="c3ddf-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="c3ddf-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="c3ddf-137">Icordebugvariablehomeenum</span><span class="sxs-lookup"><span data-stu-id="c3ddf-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="c3ddf-138">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ddf-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3ddf-139">Requirements</span></span>  
 <span data-ttu-id="c3ddf-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ddf-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ddf-141">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3ddf-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3ddf-142">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3ddf-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3ddf-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ddf-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ddf-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3ddf-144">See also</span></span>

- [<span data-ttu-id="c3ddf-145">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3ddf-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
