---
title: ICorDebugProcess::GetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d54becc2d7cd4359c78415f25f579b968cb3f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775615"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="cf0fd-102">ICorDebugProcess::GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf0fd-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="cf0fd-103">Bu işlem belirli bir iş parçacığı için bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf0fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf0fd-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf0fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf0fd-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cf0fd-106">[in] Bağlamı almak istediğiniz iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="cf0fd-107">[in] Boyutu `context` dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="cf0fd-108">[out içinde] İş parçacığı bağlamı açıklayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="cf0fd-109">Bağlam, iş parçacığının yürütülmekte olan işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf0fd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf0fd-110">Remarks</span></span>  
 <span data-ttu-id="cf0fd-111">Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `GetThreadContext` yöntemi, çünkü iş parçacığı aslında, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="cf0fd-112">Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="cf0fd-113">Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="cf0fd-114">Döndürülen veriler, geçerli platform için bir bağlam yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="cf0fd-115">İle olduğu gibi Win32 `GetThreadContext` Initialize yöntemi, çağırana `context` bu yöntemi çağırmadan önce parametresi.</span><span class="sxs-lookup"><span data-stu-id="cf0fd-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf0fd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf0fd-116">Requirements</span></span>  
 <span data-ttu-id="cf0fd-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf0fd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf0fd-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf0fd-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf0fd-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf0fd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf0fd-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf0fd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
