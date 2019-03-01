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
ms.openlocfilehash: 7dc732a8e3419a7ca42f5180d1bd32128ec33417
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967522"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="1dea7-102">ICorDebugProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dea7-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="1dea7-103">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1dea7-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="1dea7-104">Icordebugcontroller öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="1dea7-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dea7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1dea7-105">Methods</span></span>  
  
|<span data-ttu-id="1dea7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1dea7-106">Method</span></span>|<span data-ttu-id="1dea7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dea7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dea7-108">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="1dea7-109">Verilen iş parçacığı üzerinde geçerli yönetilmeyen özel durum temizler.</span><span class="sxs-lookup"><span data-stu-id="1dea7-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="1dea7-110">EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="1dea7-111">Etkinleştirir ve günlük iletilerini göndermek için hata ayıklayıcı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1dea7-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="1dea7-112">EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="1dea7-113">Tüm uygulama etki alanlarının işleminde sıralar.</span><span class="sxs-lookup"><span data-stu-id="1dea7-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="1dea7-114">EnumerateObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="1dea7-115">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1dea7-115">Not implemented.</span></span>|  
|[<span data-ttu-id="1dea7-116">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="1dea7-117">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="1dea7-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="1dea7-118">GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="1dea7-119">Hata Ayıklayıcı'nın iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="1dea7-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="1dea7-120">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="1dea7-121">İşletim sistemi (OS) işlem Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="1dea7-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="1dea7-122">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="1dea7-123">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1dea7-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1dea7-124">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="1dea7-125">Belirtilen işletim sistemi iş parçacığı Icordebugthread örneği alır kimliği</span><span class="sxs-lookup"><span data-stu-id="1dea7-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="1dea7-126">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="1dea7-127">Verilen iş parçacığı için bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="1dea7-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1dea7-128">IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="1dea7-129">İşlem durdurulurken bir hata ayıklayıcı sonucunda iş parçacığını askıya olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1dea7-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="1dea7-130">IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="1dea7-131">Adres yönetilen koda geçiş neden olacak bir saplama içinde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1dea7-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="1dea7-132">ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="1dea7-133">Belirtilen log anahtarı önem düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1dea7-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="1dea7-134">ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="1dea7-135">Bellek işlemden okur.</span><span class="sxs-lookup"><span data-stu-id="1dea7-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="1dea7-136">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="1dea7-137">Verilen iş parçacığı bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1dea7-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1dea7-138">ThreadForFiberCookie Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="1dea7-139">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="1dea7-139">Deprecated.</span></span>|  
|[<span data-ttu-id="1dea7-140">WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dea7-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="1dea7-141">Belleği işlemdeki veri yazar.</span><span class="sxs-lookup"><span data-stu-id="1dea7-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dea7-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dea7-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1dea7-143">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1dea7-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dea7-144">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dea7-144">Requirements</span></span>  
 <span data-ttu-id="1dea7-145">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dea7-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dea7-146">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dea7-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dea7-147">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dea7-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dea7-148">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dea7-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dea7-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dea7-149">See also</span></span>
- [<span data-ttu-id="1dea7-150">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dea7-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="1dea7-151">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1dea7-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
