---
description: Daha fazla bilgi için bkz. ICorDebug arabirimi
title: ICorDebug Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: b989013f7eb54e163feeb965e10448a3a1756e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772529"
---
# <a name="icordebug-interface"></a><span data-ttu-id="a6641-103">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6641-103">ICorDebug Interface</span></span>

<span data-ttu-id="a6641-104">Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamındaki uygulamalarda hata ayıklamasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6641-104">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6641-105">Karma mod (yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (ıA64 ve AMD64 gibi) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a6641-105">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6641-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a6641-106">Methods</span></span>  
  
|<span data-ttu-id="a6641-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a6641-107">Method</span></span>|<span data-ttu-id="a6641-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6641-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6641-109">CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-109">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="a6641-110">Yeni bir işlemin başlatılmasını veya belirtilen işleme, geçerli makine ve çalışma zamanı yapılandırması bağlamında mümkün olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a6641-110">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="a6641-111">CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-111">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="a6641-112">Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="a6641-112">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="a6641-113">DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-113">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="a6641-114">Hata ayıklayıcıyı mevcut bir işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="a6641-114">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="a6641-115">EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-115">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="a6641-116">Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a6641-116">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="a6641-117">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-117">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="a6641-118">Verilen işlem KIMLIĞINE sahip "ICorDebugProcess" nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6641-118">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="a6641-119">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-119">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="a6641-120">Nesnesini başlatır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="a6641-120">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="a6641-121">SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-121">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="a6641-122">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6641-122">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="a6641-123">SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-123">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="a6641-124">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6641-124">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="a6641-125">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6641-125">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="a6641-126">Nesneyi sonlandırır `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="a6641-126">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6641-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6641-127">Remarks</span></span>  

 <span data-ttu-id="a6641-128">`ICorDebug` hata ayıklayıcı işlemi için bir olay işleme döngüsünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6641-128">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="a6641-129">Hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess geri çağırması](icordebugmanagedcallback-exitprocess-method.md) , bu arabirimi serbest bırakmadan önce hata ayıklamakta olan tüm işlemlerden geri aramasını beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a6641-129">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="a6641-130">`ICorDebug`Nesne, daha fazla yönetilen hata ayıklamayı denetlemek için ilk nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a6641-130">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="a6641-131">.NET Framework sürüm 1,0 ve 1,1 ' de, bu nesne COM ' `CoClass` dan oluşturulan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="a6641-131">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="a6641-132">.NET Framework sürüm 2,0 ' de, bu nesne artık bir nesne değildir `CoClass` .</span><span class="sxs-lookup"><span data-stu-id="a6641-132">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="a6641-133">Daha fazla sürüm tanıyan [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) işlevi tarafından oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a6641-133">It must be created by the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="a6641-134">Bu yeni oluşturma işlevi, istemcilerin belirli bir uygulamasını almasını sağlar `ICorDebug` ve bu da hata ayıklama API 'sinin belirli bir sürümüne öykünür.</span><span class="sxs-lookup"><span data-stu-id="a6641-134">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6641-135">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a6641-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6641-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6641-136">Requirements</span></span>  

 <span data-ttu-id="a6641-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6641-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6641-138">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6641-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6641-139">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a6641-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6641-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6641-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6641-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6641-141">See also</span></span>

- [<span data-ttu-id="a6641-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a6641-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
