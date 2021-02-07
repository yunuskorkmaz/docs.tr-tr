---
description: ': ICorDebugProcess arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7172ee12bf450235db1c18601c8ff7de51435520
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746795"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="50e86-103">ICorDebugProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e86-103">ICorDebugProcess Interface</span></span>

<span data-ttu-id="50e86-104">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="50e86-104">Represents a process that is executing managed code.</span></span> <span data-ttu-id="50e86-105">Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="50e86-105">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50e86-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="50e86-106">Methods</span></span>  
  
|<span data-ttu-id="50e86-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="50e86-107">Method</span></span>|<span data-ttu-id="50e86-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50e86-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50e86-109">ClearCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-109">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="50e86-110">Belirtilen iş parçacığında geçerli yönetilmeyen özel durumu temizler.</span><span class="sxs-lookup"><span data-stu-id="50e86-110">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="50e86-111">EnableLogMessages Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-111">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="50e86-112">Hata ayıklayıcıya günlük iletilerinin gönderilmesini sağlar ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="50e86-112">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="50e86-113">EnumerateAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-113">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="50e86-114">İşlemdeki tüm uygulama etki alanlarını numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="50e86-114">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="50e86-115">EnumerateObjects Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-115">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="50e86-116">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="50e86-116">Not implemented.</span></span>|  
|[<span data-ttu-id="50e86-117">GetHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-117">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="50e86-118">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="50e86-118">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="50e86-119">GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-119">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="50e86-120">Hata ayıklayıcının iç yardımcı iş parçacığı için işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="50e86-120">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="50e86-121">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-121">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="50e86-122">İşlemin işletim sistemi (OS) KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="50e86-122">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="50e86-123">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="50e86-123">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="50e86-124">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="50e86-124">Not implemented.</span></span>|  
|[<span data-ttu-id="50e86-125">GetThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-125">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="50e86-126">Belirtilen işletim sistemi iş parçacığı KIMLIĞINE sahip ICorDebugThread örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="50e86-126">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="50e86-127">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-127">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="50e86-128">Verilen iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="50e86-128">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="50e86-129">IsOSSuspended Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-129">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="50e86-130">Hata ayıklayıcının işlemi durdurmasının bir sonucu olarak iş parçacığının askıya alınıp alınmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="50e86-130">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="50e86-131">IsTransitionStub Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-131">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="50e86-132">Bir adresin, yönetilen koda geçişe neden olacak bir saplama içinde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="50e86-132">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="50e86-133">ModifyLogSwitch Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-133">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="50e86-134">Belirtilen günlük anahtarının önem derecesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="50e86-134">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="50e86-135">ReadMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-135">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="50e86-136">İşlemden belleği okur.</span><span class="sxs-lookup"><span data-stu-id="50e86-136">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="50e86-137">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-137">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="50e86-138">Verilen iş parçacığının bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="50e86-138">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="50e86-139">ThreadForFiberCookie Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-139">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="50e86-140">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50e86-140">Deprecated.</span></span>|  
|[<span data-ttu-id="50e86-141">WriteMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50e86-141">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="50e86-142">İşlemdeki bir bellek alanına veri yazar.</span><span class="sxs-lookup"><span data-stu-id="50e86-142">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e86-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50e86-143">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50e86-144">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="50e86-144">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e86-145">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50e86-145">Requirements</span></span>  

 <span data-ttu-id="50e86-146">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e86-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e86-147">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50e86-147">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e86-148">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50e86-148">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e86-149">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e86-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e86-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50e86-150">See also</span></span>

- [<span data-ttu-id="50e86-151">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50e86-151">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="50e86-152">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50e86-152">Debugging Interfaces</span></span>](debugging-interfaces.md)
