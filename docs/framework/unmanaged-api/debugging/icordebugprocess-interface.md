---
title: Icordebugprocess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee526a79d89a9e4e3483daa07a512b6b7f920e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="f0081-102">Icordebugprocess Interface1</span><span class="sxs-lookup"><span data-stu-id="f0081-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="f0081-103">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0081-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="f0081-104">Bu arabirim Icordebugcontroller sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="f0081-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0081-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0081-105">Methods</span></span>  
  
|<span data-ttu-id="f0081-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f0081-106">Method</span></span>|<span data-ttu-id="f0081-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0081-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0081-108">ClearCurrentException yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="f0081-109">Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.</span><span class="sxs-lookup"><span data-stu-id="f0081-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="f0081-110">EnableLogMessages yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="f0081-111">Etkinleştirir ve günlük iletileri için hata ayıklayıcı göndermeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f0081-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="f0081-112">EnumerateAppDomains yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="f0081-113">Tüm uygulama etki alanlarının işleminde numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f0081-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="f0081-114">EnumerateObjects yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="f0081-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f0081-115">Not implemented.</span></span>|  
|[<span data-ttu-id="f0081-116">GetHandle yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="f0081-117">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f0081-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="f0081-118">Gethelperthreadıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="f0081-119">Hata Ayıklayıcı'nın iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı kimliği alır.</span><span class="sxs-lookup"><span data-stu-id="f0081-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="f0081-120">GetID yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="f0081-121">İşlemin işletim sistemi (OS) Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f0081-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="f0081-122">GetObject yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="f0081-123">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f0081-123">Not implemented.</span></span>|  
|[<span data-ttu-id="f0081-124">GetThread yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="f0081-125">Belirtilen işletim sistemi iş parçacığına sahip Icordebugthread örneği alır kimliği</span><span class="sxs-lookup"><span data-stu-id="f0081-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="f0081-126">GetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="f0081-127">Bağlam için verilen iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="f0081-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="f0081-128">Isossuspended yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="f0081-129">İş parçacığı İşlem Durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f0081-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="f0081-130">Istransitionstub yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="f0081-131">Bir adresi yönetilen kod geçiş neden olacak bir saplama içinde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f0081-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="f0081-132">ModifyLogSwitch yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="f0081-133">Belirtilen günlük anahtar önem derecesi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0081-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="f0081-134">ReadMemory yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="f0081-135">Bellek işleminden okur.</span><span class="sxs-lookup"><span data-stu-id="f0081-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="f0081-136">SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="f0081-137">Verilen iş parçacığı bağlamının ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f0081-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="f0081-138">ThreadForFiberCookie yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="f0081-139">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="f0081-139">Deprecated.</span></span>|  
|[<span data-ttu-id="f0081-140">WriteMemory yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0081-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="f0081-141">İşlem bellek alanı için veri yazar.</span><span class="sxs-lookup"><span data-stu-id="f0081-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0081-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0081-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0081-143">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f0081-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0081-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0081-144">Requirements</span></span>  
 <span data-ttu-id="f0081-145">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0081-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0081-146">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0081-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0081-147">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0081-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0081-148">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0081-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0081-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0081-149">See Also</span></span>  
 [<span data-ttu-id="f0081-150">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0081-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="f0081-151">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0081-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
