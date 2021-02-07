---
description: 'Bu konuda daha fazla bilgi edinin: ıcorı, Genum arabirimi'
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
ms.openlocfilehash: 20d2bb14bddcaf40802567ec78a8e318ac1db380
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694480"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="15d88-103">ICorDebugEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15d88-103">ICorDebugEnum Interface</span></span>

<span data-ttu-id="15d88-104">Bir hata ayıklama uygulaması tarafından kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="15d88-104">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15d88-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15d88-105">Methods</span></span>  
  
|<span data-ttu-id="15d88-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15d88-106">Method</span></span>|<span data-ttu-id="15d88-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15d88-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15d88-108">Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15d88-108">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="15d88-109">Bu nesnenin bir kopyasını oluşturur `ICorDebugEnum` .</span><span class="sxs-lookup"><span data-stu-id="15d88-109">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="15d88-110">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15d88-110">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="15d88-111">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="15d88-111">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="15d88-112">Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15d88-112">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="15d88-113">İmleci numaralandırmanın başlangıcına kaydırır.</span><span class="sxs-lookup"><span data-stu-id="15d88-113">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="15d88-114">Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15d88-114">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="15d88-115">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="15d88-115">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15d88-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15d88-116">Remarks</span></span>  

 <span data-ttu-id="15d88-117">Aşağıdaki Numaralandırıcılar öğesinden türetilir `ICorDebugEnum` :</span><span class="sxs-lookup"><span data-stu-id="15d88-117">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="15d88-118">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-118">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="15d88-119">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-119">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="15d88-120">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-120">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="15d88-121">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-121">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="15d88-122">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-122">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="15d88-123">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-123">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="15d88-124">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-124">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="15d88-125">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-125">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="15d88-126">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-126">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="15d88-127">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-127">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="15d88-128">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-128">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="15d88-129">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-129">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="15d88-130">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-130">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="15d88-131">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-131">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="15d88-132">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-132">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="15d88-133">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-133">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="15d88-134">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-134">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="15d88-135">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-135">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="15d88-136">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-136">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="15d88-137">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="15d88-137">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="15d88-138">Icordebugvariablehomeenum</span><span class="sxs-lookup"><span data-stu-id="15d88-138">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="15d88-139">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="15d88-139">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d88-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15d88-140">Requirements</span></span>  

 <span data-ttu-id="15d88-141">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d88-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d88-142">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15d88-142">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15d88-143">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="15d88-143">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d88-144">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d88-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d88-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d88-145">See also</span></span>

- [<span data-ttu-id="15d88-146">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15d88-146">Debugging Interfaces</span></span>](debugging-interfaces.md)
