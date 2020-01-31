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
ms.openlocfilehash: cc5598f9cbec4b97bb75f83fb18ccf8742904272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783003"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="b0857-102">ICorDebugEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0857-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="b0857-103">Bir hata ayıklama uygulaması tarafından kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b0857-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0857-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b0857-104">Methods</span></span>  
  
|<span data-ttu-id="b0857-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b0857-105">Method</span></span>|<span data-ttu-id="b0857-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0857-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0857-107">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0857-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="b0857-108">Bu `ICorDebugEnum` nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0857-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="b0857-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0857-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="b0857-110">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b0857-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b0857-111">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0857-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="b0857-112">İmleci numaralandırmanın başlangıcına kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b0857-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b0857-113">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0857-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="b0857-114">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b0857-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0857-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0857-115">Remarks</span></span>  
 <span data-ttu-id="b0857-116">Aşağıdaki Numaralandırıcılar `ICorDebugEnum`türetilir:</span><span class="sxs-lookup"><span data-stu-id="b0857-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="b0857-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="b0857-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="b0857-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="b0857-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="b0857-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="b0857-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="b0857-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="b0857-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="b0857-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="b0857-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="b0857-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="b0857-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="b0857-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="b0857-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="b0857-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="b0857-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="b0857-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="b0857-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="b0857-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="b0857-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="b0857-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="b0857-137">Icordebugvariablehomeenum</span><span class="sxs-lookup"><span data-stu-id="b0857-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="b0857-138">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b0857-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0857-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0857-139">Requirements</span></span>  
 <span data-ttu-id="b0857-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0857-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0857-141">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0857-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0857-142">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0857-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0857-143">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0857-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0857-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0857-144">See also</span></span>

- [<span data-ttu-id="b0857-145">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b0857-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
