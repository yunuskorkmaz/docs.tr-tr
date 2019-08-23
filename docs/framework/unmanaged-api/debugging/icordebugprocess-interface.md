---
title: ICorDebugProcess Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b99630ba60cd84254024b91dba9ef9922fd7e041
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943311"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="1aa6b-102">ICorDebugProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="1aa6b-103">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="1aa6b-104">Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1aa6b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1aa6b-105">Methods</span></span>  
  
|<span data-ttu-id="1aa6b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1aa6b-106">Method</span></span>|<span data-ttu-id="1aa6b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1aa6b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1aa6b-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="1aa6b-109">Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="1aa6b-110">EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="1aa6b-111">Hata ayıklayıcıya günlük iletilerinin gönderilmesini sağlar ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="1aa6b-112">EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="1aa6b-113">İşlemdeki tüm uygulama etki alanlarını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="1aa6b-114">EnumerateObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="1aa6b-115">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-115">Not implemented.</span></span>|  
|[<span data-ttu-id="1aa6b-116">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="1aa6b-117">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="1aa6b-118">GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="1aa6b-119">Hata ayıklayıcının iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="1aa6b-120">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="1aa6b-121">İşlemin işletim sistemi (OS) KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="1aa6b-122">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="1aa6b-123">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1aa6b-124">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="1aa6b-125">Belirtilen işletim sistemi iş parçacığı KIMLIĞINE sahip ICorDebugThread örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="1aa6b-126">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="1aa6b-127">Verilen iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1aa6b-128">IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="1aa6b-129">Hata ayıklayıcının işlemi durdurmasının bir sonucu olarak iş parçacığının askıya alınıp alınmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="1aa6b-130">IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="1aa6b-131">Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="1aa6b-132">ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="1aa6b-133">Belirtilen günlük anahtarının önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="1aa6b-134">ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="1aa6b-135">İşlemden belleği okur.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="1aa6b-136">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="1aa6b-137">Verilen iş parçacığının bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1aa6b-138">ThreadForFiberCookie Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="1aa6b-139">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-139">Deprecated.</span></span>|  
|[<span data-ttu-id="1aa6b-140">WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="1aa6b-141">İşlemdeki bir bellek alanına veri yazar.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aa6b-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1aa6b-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1aa6b-143">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa6b-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1aa6b-144">Requirements</span></span>  
 <span data-ttu-id="1aa6b-145">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aa6b-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa6b-146">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1aa6b-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aa6b-147">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1aa6b-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aa6b-148">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa6b-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa6b-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1aa6b-149">See also</span></span>

- [<span data-ttu-id="1aa6b-150">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1aa6b-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="1aa6b-151">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1aa6b-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
