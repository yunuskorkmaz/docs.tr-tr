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
ms.openlocfilehash: 41c5116d23655730f3586dc656aa69c8ae817b6c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792618"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="6a40f-102">ICorDebugProcess::GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a40f-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="6a40f-103">Bu işlemdeki verilen iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="6a40f-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a40f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a40f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a40f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a40f-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6a40f-106">'ndaki Bağlamını almak için iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6a40f-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6a40f-107">'ndaki `context` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="6a40f-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="6a40f-108">[in, out] İş parçacığının bağlamını tanımlayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="6a40f-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="6a40f-109">Bağlam, iş parçacığının yürütüldüğü işlemcinin mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a40f-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a40f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a40f-110">Remarks</span></span>  
 <span data-ttu-id="6a40f-111">İş parçacığı gerçekten, bağlamı geçici olarak değiştirilen "ele alınmış" durumda olabileceğinden, hata ayıklayıcı Win32 `GetThreadContext` yöntemi yerine bu yöntemi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a40f-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="6a40f-112">Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a40f-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="6a40f-113">Yönetilen koddaki iş parçacıkları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a40f-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="6a40f-114">Döndürülen veriler, geçerli platform için bir bağlam yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="6a40f-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="6a40f-115">Win32 `GetThreadContext` yönteminde olduğu gibi, çağıranın bu yöntemi çağırmadan önce `context` parametresini başlatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6a40f-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a40f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a40f-116">Requirements</span></span>  
 <span data-ttu-id="6a40f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a40f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a40f-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a40f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a40f-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a40f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a40f-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a40f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
