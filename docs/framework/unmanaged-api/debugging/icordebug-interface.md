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
ms.openlocfilehash: 74c5036bdc8a4a75e5711c6dc1d34d8f2c21128f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408677"
---
# <a name="icordebug-interface"></a><span data-ttu-id="7b28c-102">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b28c-102">ICorDebug Interface</span></span>
<span data-ttu-id="7b28c-103">Geliştiricilerin uygulamalarında ortak dil çalışma zamanı (CLR) ortamında hata ayıklamak yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b28c-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b28c-104">Karışık mod (yönetilen ve yerel kodu) hata ayıklama Windows 95, Windows 98 veya Windows ME ya da (örneğin, IA64 ve AMD64) x86 olmayan platformlarda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7b28c-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b28c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7b28c-105">Methods</span></span>  
  
|<span data-ttu-id="7b28c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7b28c-106">Method</span></span>|<span data-ttu-id="7b28c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b28c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b28c-108">CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="7b28c-109">Yeni bir işlem başlatılıyor veya verilen işlemine iliştirme geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7b28c-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="7b28c-110">CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="7b28c-111">Hata ayıklayıcı denetiminde birincil kendi iş parçacığı ve bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="7b28c-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="7b28c-112">DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="7b28c-113">Hata ayıklayıcı varolan bir işlemi ekler.</span><span class="sxs-lookup"><span data-stu-id="7b28c-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="7b28c-114">EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="7b28c-115">Ayıklanacak işlemleri için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7b28c-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="7b28c-116">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="7b28c-117">Belirtilen işlem kimliğiyle "ICorDebugProcess" nesnesi döndürür</span><span class="sxs-lookup"><span data-stu-id="7b28c-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="7b28c-118">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="7b28c-119">Başlatır `ICorDebug` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7b28c-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="7b28c-120">SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="7b28c-121">Yönetilen olayları için olay işleyici nesnesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b28c-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="7b28c-122">SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="7b28c-123">Yönetilmeyen olayları için olay işleyici nesnesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7b28c-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="7b28c-124">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b28c-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="7b28c-125">Sonlandırır `ICorDebug` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7b28c-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b28c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b28c-126">Remarks</span></span>  
 <span data-ttu-id="7b28c-127">`ICorDebug` hata ayıklayıcı işlem için bir olay işleme döngüye temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7b28c-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="7b28c-128">Hata ayıklayıcı beklemelisiniz [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) bu arabirim bırakmadan önce ayıklanacak tüm işlemlerden geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7b28c-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="7b28c-129">`ICorDebug` Nesnesidir tüm daha fazla yönetilen hata ayıklama denetlemek için ilk nesne.</span><span class="sxs-lookup"><span data-stu-id="7b28c-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="7b28c-130">.NET Framework sürüm 1.0 ve 1.1, bu nesne olan bir `CoClass` COM'dan oluşturulan nesne</span><span class="sxs-lookup"><span data-stu-id="7b28c-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="7b28c-131">.NET Framework sürüm 2. 0'da, bu nesne artık değil bir `CoClass` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7b28c-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="7b28c-132">Tarafından oluşturulmalıdır [Createdebuggingınterfacefromversion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) sürüm daha kullanmayan işlevi.</span><span class="sxs-lookup"><span data-stu-id="7b28c-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="7b28c-133">İstemcilerin, belirli bir uygulamasına almak bu yeni oluşturma işlevi sağlar `ICorDebug`, hangi ayrıca öykünür hata ayıklama API'si belirli bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="7b28c-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b28c-134">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7b28c-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b28c-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b28c-135">Requirements</span></span>  
 <span data-ttu-id="7b28c-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b28c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b28c-137">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b28c-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b28c-138">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b28c-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b28c-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b28c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b28c-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b28c-140">See Also</span></span>  
 [<span data-ttu-id="7b28c-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7b28c-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
