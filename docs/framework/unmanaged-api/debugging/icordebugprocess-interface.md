---
title: Icordebugprocess Interface1
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
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423175"
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="60259-102">Icordebugprocess Interface1</span><span class="sxs-lookup"><span data-stu-id="60259-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="60259-103">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="60259-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="60259-104">Bu arabirim Icordebugcontroller sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="60259-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60259-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="60259-105">Methods</span></span>  
  
|<span data-ttu-id="60259-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="60259-106">Method</span></span>|<span data-ttu-id="60259-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60259-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60259-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="60259-109">Geçerli yönetilmeyen özel durumu verilen iş parçacığı üzerinde temizler.</span><span class="sxs-lookup"><span data-stu-id="60259-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="60259-110">EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="60259-111">Etkinleştirir ve günlük iletileri için hata ayıklayıcı göndermeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="60259-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="60259-112">EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="60259-113">Tüm uygulama etki alanlarının işleminde numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="60259-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="60259-114">EnumerateObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="60259-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="60259-115">Not implemented.</span></span>|  
|[<span data-ttu-id="60259-116">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="60259-117">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="60259-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="60259-118">GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="60259-119">Hata Ayıklayıcı'nın iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı kimliği alır.</span><span class="sxs-lookup"><span data-stu-id="60259-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="60259-120">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="60259-121">İşlemin işletim sistemi (OS) Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="60259-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="60259-122">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="60259-123">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="60259-123">Not implemented.</span></span>|  
|[<span data-ttu-id="60259-124">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="60259-125">Belirtilen işletim sistemi iş parçacığına sahip Icordebugthread örneği alır kimliği</span><span class="sxs-lookup"><span data-stu-id="60259-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="60259-126">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="60259-127">Bağlam için verilen iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="60259-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="60259-128">IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="60259-129">İş parçacığı İşlem Durdurma hata ayıklayıcı sonucunda askıya olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="60259-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="60259-130">IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="60259-131">Bir adresi yönetilen kod geçiş neden olacak bir saplama içinde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="60259-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="60259-132">ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="60259-133">Belirtilen günlük anahtar önem derecesi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="60259-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="60259-134">ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="60259-135">Bellek işleminden okur.</span><span class="sxs-lookup"><span data-stu-id="60259-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="60259-136">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="60259-137">Verilen iş parçacığı bağlamının ayarlar.</span><span class="sxs-lookup"><span data-stu-id="60259-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="60259-138">ThreadForFiberCookie Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="60259-139">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="60259-139">Deprecated.</span></span>|  
|[<span data-ttu-id="60259-140">WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60259-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="60259-141">İşlem bellek alanı için veri yazar.</span><span class="sxs-lookup"><span data-stu-id="60259-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60259-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60259-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60259-143">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="60259-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60259-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60259-144">Requirements</span></span>  
 <span data-ttu-id="60259-145">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60259-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60259-146">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60259-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60259-147">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60259-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60259-148">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60259-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60259-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60259-149">See Also</span></span>  
 [<span data-ttu-id="60259-150">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60259-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="60259-151">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="60259-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
