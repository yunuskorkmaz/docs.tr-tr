---
title: ICorDebugProcess::SetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b949961e854facf8414c81c47f995b2ac57af3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755388"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="cf7bb-102">ICorDebugProcess::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf7bb-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="cf7bb-103">Bu işlemde belirli iş parçacığı bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf7bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf7bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf7bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf7bb-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cf7bb-106">[in] Hangi bağlamını ayarlamak iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="cf7bb-107">[in] Boyutu `context` dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="cf7bb-108">[in] İş parçacığı bağlamı açıklayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="cf7bb-109">Bağlam, iş parçacığının yürütülmekte olan işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf7bb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf7bb-110">Remarks</span></span>  
 <span data-ttu-id="cf7bb-111">Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `SetThreadContext` iş parçacığı, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabileceğinden, işlev.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="cf7bb-112">Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="cf7bb-113">Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="cf7bb-114">Hiçbir zaman bir bant dışı (OOB) hata ayıklama olayı sırasında bir iş parçacığı bağlamı değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="cf7bb-115">Geçirilen veriler, geçerli platform için bir bağlam yapısı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="cf7bb-116">Bu yöntem, çalışma zamanı yanlış kullandıysanız bozabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7bb-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf7bb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf7bb-117">Requirements</span></span>  
 <span data-ttu-id="cf7bb-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf7bb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf7bb-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf7bb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf7bb-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf7bb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf7bb-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf7bb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
