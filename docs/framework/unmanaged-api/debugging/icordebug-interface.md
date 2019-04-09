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
ms.openlocfilehash: 193232ce1006a9cf209db9330343386404948440
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168291"
---
# <a name="icordebug-interface"></a><span data-ttu-id="7788e-102">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7788e-102">ICorDebug Interface</span></span>
<span data-ttu-id="7788e-103">Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7788e-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7788e-104">Karma mod (yönetilen ve yerel kod) hata ayıklaması, Windows 95, Windows 98 veya Windows ME veya x86 olmayan platformları (örneğin, IA64 ve AMD64 gibi) üzerinde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7788e-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7788e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7788e-105">Methods</span></span>  
  
|<span data-ttu-id="7788e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7788e-106">Method</span></span>|<span data-ttu-id="7788e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7788e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7788e-108">CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="7788e-109">Yeni bir işlem başlatılıyor veya belirtilen işleme iliştirdikten geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7788e-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="7788e-110">CreateProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="7788e-111">Bir işlem ve onun birincil iş parçacığı hata ayıklayıcının denetiminin altında başlatır.</span><span class="sxs-lookup"><span data-stu-id="7788e-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="7788e-112">DebugActiveProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="7788e-113">Hata ayıklayıcı, varolan bir sürece ekler.</span><span class="sxs-lookup"><span data-stu-id="7788e-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="7788e-114">EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="7788e-115">Hatası ayıklanmakta işlemler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7788e-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="7788e-116">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="7788e-117">Belirtilen işlem kimliğiyle "ICorDebugProcess" nesneyi döndürür</span><span class="sxs-lookup"><span data-stu-id="7788e-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="7788e-118">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="7788e-119">Başlatır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="7788e-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="7788e-120">SetManagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="7788e-121">Yönetilen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7788e-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="7788e-122">SetUnmanagedHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="7788e-123">Yönetilmeyen olaylar için olay işleyicisi nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7788e-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="7788e-124">Terminate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7788e-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="7788e-125">Sonlandırır `ICorDebug` nesne.</span><span class="sxs-lookup"><span data-stu-id="7788e-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7788e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7788e-126">Remarks</span></span>  
 `ICorDebug` <span data-ttu-id="7788e-127">hata ayıklayıcı işleme için bir olay işleme döngüsünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7788e-127">represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="7788e-128">Hata ayıklayıcı beklemelisiniz [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) serbest bırakmadan önce bu arabirimi hata ayıklaması yapılan tüm işlemlerden geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7788e-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="7788e-129">`ICorDebug` Nesnedir tüm daha fazla yönetilen hata ayıklama denetlemek için ilk nesne.</span><span class="sxs-lookup"><span data-stu-id="7788e-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="7788e-130">.NET Framework sürüm 1.0 ve 1.1, bu nesne olduğu bir `CoClass` COM'dan oluşturulan nesne</span><span class="sxs-lookup"><span data-stu-id="7788e-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="7788e-131">.NET Framework sürüm 2. 0'da, bu nesne artık değil bir `CoClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="7788e-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="7788e-132">Tarafından oluşturulmalıdır [Createdebuggingınterfacefromversion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) sürümü daha duyarlı işlevi.</span><span class="sxs-lookup"><span data-stu-id="7788e-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="7788e-133">Bu yeni oluşturma işlevi özel uygulanışı almak istemcileri etkinleştirir `ICorDebug`, hangi ayrıca öykünür belirli bir hata ayıklama API sürümü.</span><span class="sxs-lookup"><span data-stu-id="7788e-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7788e-134">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7788e-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7788e-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7788e-135">Requirements</span></span>  
 <span data-ttu-id="7788e-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7788e-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7788e-137">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7788e-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7788e-138">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7788e-138">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7788e-139">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7788e-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7788e-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7788e-140">See also</span></span>

- [<span data-ttu-id="7788e-141">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7788e-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
