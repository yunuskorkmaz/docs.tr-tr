---
description: ': ICorDebugProcess:: GetThreadContext metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4cb926183522548e924013580f207d1d0677a0d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746873"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="74ce5-103">ICorDebugProcess::GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74ce5-103">ICorDebugProcess::GetThreadContext Method</span></span>

<span data-ttu-id="74ce5-104">Bu işlemdeki verilen iş parçacığının bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-104">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ce5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74ce5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74ce5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74ce5-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="74ce5-107">'ndaki Bağlamını almak için iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="74ce5-107">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="74ce5-108">'ndaki `context` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="74ce5-108">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="74ce5-109">[in, out] İş parçacığının bağlamını tanımlayan bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="74ce5-109">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="74ce5-110">Bağlam, iş parçacığının yürütüldüğü işlemcinin mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-110">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74ce5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74ce5-111">Remarks</span></span>  

 <span data-ttu-id="74ce5-112">`GetThreadContext`İş parçacığı gerçekten, bağlamı geçici olarak değiştirilen bir "ele geçirilmiş" durumda olabileceğinden, hata ayıklayıcı Win32 yöntemi yerine bu yöntemi çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-112">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="74ce5-113">Bu yöntem, yalnızca bir iş parçacığı yerel kodda olduğunda kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-113">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="74ce5-114">Yönetilen koddaki iş parçacıkları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="74ce5-114">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="74ce5-115">Döndürülen veriler, geçerli platform için bir bağlam yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="74ce5-115">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="74ce5-116">Win32 yönteminde olduğu gibi `GetThreadContext` , çağıranın `context` Bu yöntemi çağırmadan önce parametresini başlatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="74ce5-116">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74ce5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74ce5-117">Requirements</span></span>  

 <span data-ttu-id="74ce5-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ce5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ce5-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74ce5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74ce5-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74ce5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74ce5-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ce5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
