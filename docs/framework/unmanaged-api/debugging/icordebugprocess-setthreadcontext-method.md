---
title: "ICorDebugProcess::SetThreadContext Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 70368602672e06dc3a5aaf4f2f4bc7632c5a9a79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="52107-102">ICorDebugProcess::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52107-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="52107-103">Verilen iş parçacığı bağlamının bu işlemde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="52107-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52107-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52107-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52107-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52107-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="52107-106">[in] Bağlam ayarlanacağı için iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="52107-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="52107-107">[in] Boyutunu `context` dizi.</span><span class="sxs-lookup"><span data-stu-id="52107-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="52107-108">[in] İş parçacığının içeriğini açıklayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="52107-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="52107-109">Bağlam parçacığının çalıştırdığından işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="52107-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52107-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52107-110">Remarks</span></span>  
 <span data-ttu-id="52107-111">Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `SetThreadContext` iş parçacığı içinde onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabileceğinden, işlev.</span><span class="sxs-lookup"><span data-stu-id="52107-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="52107-112">Bu yöntem yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52107-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="52107-113">Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="52107-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="52107-114">Hiçbir zaman bir bant dışı (OOB) hata ayıklama olayı sırasında bir iş parçacığı bağlamı değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="52107-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="52107-115">Geçirilen verileri geçerli platform için bir bağlam yapısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="52107-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="52107-116">Bu yöntem, yanlış kullandıysanız çalışma zamanı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="52107-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52107-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52107-117">Requirements</span></span>  
 <span data-ttu-id="52107-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52107-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52107-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52107-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52107-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52107-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52107-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52107-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
