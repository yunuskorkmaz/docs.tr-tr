---
title: ICorDebugProcess::GetThreadContext Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e45d101db946747463ba4200bc5dd3b95d21391
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="92ef1-102">ICorDebugProcess::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="92ef1-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="92ef1-103">Bu işlem verilen iş parçacığı için bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="92ef1-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92ef1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92ef1-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92ef1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92ef1-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="92ef1-106">[in] İçerik almak için iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="92ef1-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="92ef1-107">[in] Boyutunu `context` dizi.</span><span class="sxs-lookup"><span data-stu-id="92ef1-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="92ef1-108">[içinde out] İş parçacığının içeriğini açıklayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="92ef1-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="92ef1-109">Bağlam parçacığının çalıştırdığından işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92ef1-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92ef1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92ef1-110">Remarks</span></span>  
 <span data-ttu-id="92ef1-111">Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `GetThreadContext` yöntemi, çünkü iş parçacığı gerçekte, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="92ef1-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="92ef1-112">Bu yöntem yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92ef1-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="92ef1-113">Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="92ef1-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="92ef1-114">Döndürülen veri geçerli platform için bir bağlam yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="92ef1-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="92ef1-115">Win32 gibi olduğu `GetThreadContext` çağıran Initialize yöntemi, `context` bu yöntemi çağırmadan önce parametre.</span><span class="sxs-lookup"><span data-stu-id="92ef1-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92ef1-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92ef1-116">Requirements</span></span>  
 <span data-ttu-id="92ef1-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92ef1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92ef1-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92ef1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92ef1-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92ef1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92ef1-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92ef1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
