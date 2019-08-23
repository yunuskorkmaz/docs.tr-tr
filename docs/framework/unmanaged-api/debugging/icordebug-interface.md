---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afbf480d69e97662b5963706bb8c192aec0325a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966291"
---
# <a name="icordebug-interface"></a><span data-ttu-id="f0672-102">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0672-102">ICorDebug Interface</span></span>
<span data-ttu-id="f0672-103">Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamındaki uygulamalarda hata ayıklamasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0672-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0672-104">Karma mod (yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (ıA64 ve AMD64 gibi) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f0672-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0672-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0672-105">Methods</span></span>  
  
|<span data-ttu-id="f0672-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f0672-106">Method</span></span>|<span data-ttu-id="f0672-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0672-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0672-108">CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="f0672-109">Yeni bir işlemin başlatılmasını veya belirtilen işleme, geçerli makine ve çalışma zamanı yapılandırması bağlamında mümkün olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f0672-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="f0672-110">CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="f0672-111">Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="f0672-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="f0672-112">DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="f0672-113">Hata ayıklayıcıyı mevcut bir işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="f0672-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="f0672-114">EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="f0672-115">Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f0672-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="f0672-116">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="f0672-117">Verilen işlem KIMLIĞINE sahip "ICorDebugProcess" nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0672-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="f0672-118">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="f0672-119">`ICorDebug` Nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="f0672-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="f0672-120">SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="f0672-121">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0672-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="f0672-122">SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="f0672-123">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0672-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="f0672-124">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0672-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="f0672-125">`ICorDebug` Nesneyi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="f0672-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0672-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0672-126">Remarks</span></span>  
 <span data-ttu-id="f0672-127">`ICorDebug`hata ayıklayıcı işlemi için bir olay işleme döngüsünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0672-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="f0672-128">Hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess geri çağırması](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) , bu arabirimi serbest bırakmadan önce hata ayıklamakta olan tüm işlemlerden geri aramasını beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0672-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="f0672-129">`ICorDebug` Nesne, daha fazla yönetilen hata ayıklamayı denetlemek için ilk nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f0672-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="f0672-130">.NET Framework sürüm 1,0 ve 1,1 ' de, bu nesne com ' `CoClass` dan oluşturulan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f0672-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="f0672-131">.NET Framework sürüm 2,0 ' de, bu nesne artık bir `CoClass` nesne değildir.</span><span class="sxs-lookup"><span data-stu-id="f0672-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="f0672-132">Daha fazla sürüm tanıyan [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) işlevi tarafından oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f0672-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="f0672-133">Bu yeni oluşturma işlevi `ICorDebug`, istemcilerin belirli bir uygulamasını almasını sağlar ve bu da hata ayıklama API 'sinin belirli bir sürümüne öykünür.</span><span class="sxs-lookup"><span data-stu-id="f0672-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0672-134">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f0672-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0672-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0672-135">Requirements</span></span>  
 <span data-ttu-id="f0672-136">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0672-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0672-137">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0672-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0672-138">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f0672-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0672-139">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0672-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0672-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0672-140">See also</span></span>

- [<span data-ttu-id="f0672-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0672-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
