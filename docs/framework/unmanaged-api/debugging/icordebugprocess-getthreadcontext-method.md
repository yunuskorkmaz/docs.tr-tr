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
ms.openlocfilehash: 2bdbf373144e2fb49074cfd035e7b0ffe3c8c291
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212899"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="eeafe-102">ICorDebugProcess::GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eeafe-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="eeafe-103">Bu işlemdeki verilen iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="eeafe-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeafe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eeafe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eeafe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eeafe-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="eeafe-106">'ndaki Bağlamını almak için iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="eeafe-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="eeafe-107">'ndaki `context`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="eeafe-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="eeafe-108">[in, out] İş parçacığının bağlamını tanımlayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="eeafe-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="eeafe-109">Bağlam, iş parçacığının yürütüldüğü işlemcinin mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eeafe-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eeafe-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eeafe-110">Remarks</span></span>  
 <span data-ttu-id="eeafe-111">`GetThreadContext`İş parçacığı gerçekten, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 yöntemi yerine bu yöntemi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eeafe-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="eeafe-112">Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eeafe-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="eeafe-113">Yönetilen koddaki iş parçacıkları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="eeafe-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="eeafe-114">Döndürülen veriler, geçerli platform için bir bağlam yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="eeafe-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="eeafe-115">Win32 yönteminde olduğu gibi `GetThreadContext` , çağıranın `context` Bu yöntemi çağırmadan önce parametresini başlatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eeafe-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eeafe-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eeafe-116">Requirements</span></span>  
 <span data-ttu-id="eeafe-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eeafe-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eeafe-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eeafe-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eeafe-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eeafe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eeafe-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eeafe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
