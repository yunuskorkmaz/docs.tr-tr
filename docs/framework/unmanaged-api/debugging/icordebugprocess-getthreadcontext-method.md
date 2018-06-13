---
title: ICorDebugProcess::GetThreadContext Metodu
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
ms.openlocfilehash: ea977b1ccecf9de5a04e1f1127658ca6c15043a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416546"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="5c134-102">ICorDebugProcess::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="5c134-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="5c134-103">Bu işlem verilen iş parçacığı için bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="5c134-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c134-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c134-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c134-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c134-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5c134-106">[in] İçerik almak için iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="5c134-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5c134-107">[in] Boyutunu `context` dizi.</span><span class="sxs-lookup"><span data-stu-id="5c134-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="5c134-108">[içinde out] İş parçacığının içeriğini açıklayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="5c134-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="5c134-109">Bağlam parçacığının çalıştırdığından işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c134-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c134-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c134-110">Remarks</span></span>  
 <span data-ttu-id="5c134-111">Hata ayıklayıcı Win32 yerine bu yöntemi çağırmanız gerekir `GetThreadContext` yöntemi, çünkü iş parçacığı gerçekte, onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c134-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="5c134-112">Bu yöntem yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c134-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="5c134-113">Kullanım [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) yönetilen kodda iş parçacığı için.</span><span class="sxs-lookup"><span data-stu-id="5c134-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="5c134-114">Döndürülen veri geçerli platform için bir bağlam yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="5c134-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="5c134-115">Win32 gibi olduğu `GetThreadContext` çağıran Initialize yöntemi, `context` bu yöntemi çağırmadan önce parametre.</span><span class="sxs-lookup"><span data-stu-id="5c134-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c134-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c134-116">Requirements</span></span>  
 <span data-ttu-id="5c134-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c134-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c134-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c134-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c134-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c134-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c134-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c134-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
