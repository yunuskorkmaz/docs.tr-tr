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
ms.openlocfilehash: 66b50bad0e8d2622922da96c213643ac3be83a9e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895368"
---
# <a name="icordebug-interface"></a><span data-ttu-id="816b1-102">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="816b1-102">ICorDebug Interface</span></span>
<span data-ttu-id="816b1-103">Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamındaki uygulamalarda hata ayıklamasına imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="816b1-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="816b1-104">Karma mod (yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (ıA64 ve AMD64 gibi) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="816b1-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="816b1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="816b1-105">Methods</span></span>  
  
|<span data-ttu-id="816b1-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="816b1-106">Method</span></span>|<span data-ttu-id="816b1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="816b1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="816b1-108">CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-108">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="816b1-109">Yeni bir işlemin başlatılmasını veya belirtilen işleme, geçerli makine ve çalışma zamanı yapılandırması bağlamında mümkün olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="816b1-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="816b1-110">CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-110">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="816b1-111">Hata ayıklayıcının denetimi altında bir işlem ve birincil iş parçacığını başlatır.</span><span class="sxs-lookup"><span data-stu-id="816b1-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="816b1-112">DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-112">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="816b1-113">Hata ayıklayıcıyı mevcut bir işleme iliştirir.</span><span class="sxs-lookup"><span data-stu-id="816b1-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="816b1-114">EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-114">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="816b1-115">Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="816b1-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="816b1-116">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-116">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="816b1-117">Verilen işlem KIMLIĞINE sahip "ICorDebugProcess" nesnesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="816b1-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="816b1-118">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-118">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="816b1-119">`ICorDebug` Nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="816b1-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="816b1-120">SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-120">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="816b1-121">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="816b1-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="816b1-122">SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-122">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="816b1-123">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="816b1-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="816b1-124">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="816b1-124">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="816b1-125">`ICorDebug` Nesneyi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="816b1-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="816b1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="816b1-126">Remarks</span></span>  
 <span data-ttu-id="816b1-127">`ICorDebug`hata ayıklayıcı işlemi için bir olay işleme döngüsünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="816b1-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="816b1-128">Hata ayıklayıcının [ICorDebugManagedCallback:: ExitProcess geri çağırması](icordebugmanagedcallback-exitprocess-method.md) , bu arabirimi serbest bırakmadan önce hata ayıklamakta olan tüm işlemlerden geri aramasını beklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="816b1-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="816b1-129">`ICorDebug` Nesne, daha fazla yönetilen hata ayıklamayı denetlemek için ilk nesnedir.</span><span class="sxs-lookup"><span data-stu-id="816b1-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="816b1-130">.NET Framework sürüm 1,0 ve 1,1 ' de, bu nesne COM ' `CoClass` dan oluşturulan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="816b1-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="816b1-131">.NET Framework sürüm 2,0 ' de, bu nesne artık bir `CoClass` nesne değildir.</span><span class="sxs-lookup"><span data-stu-id="816b1-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="816b1-132">Daha fazla sürüm tanıyan [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) işlevi tarafından oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="816b1-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="816b1-133">Bu yeni oluşturma işlevi `ICorDebug`, istemcilerin belirli bir uygulamasını almasını sağlar ve bu da hata ayıklama API 'sinin belirli bir sürümüne öykünür.</span><span class="sxs-lookup"><span data-stu-id="816b1-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="816b1-134">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="816b1-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="816b1-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="816b1-135">Requirements</span></span>  
 <span data-ttu-id="816b1-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="816b1-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="816b1-137">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="816b1-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="816b1-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="816b1-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="816b1-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="816b1-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816b1-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="816b1-140">See also</span></span>

- [<span data-ttu-id="816b1-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="816b1-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
