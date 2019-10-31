---
title: ICorDebugNativeFrame::SetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 1d978cab0817af68356d95d635f8d2bfa3fd546a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096748"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="d3542-102">ICorDebugNativeFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3542-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="d3542-103">Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3542-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3542-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3542-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3542-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3542-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="d3542-106">'ndaki Yerel koddaki konum konumu.</span><span class="sxs-lookup"><span data-stu-id="d3542-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3542-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3542-107">Remarks</span></span>  
 <span data-ttu-id="d3542-108">`SetIP` çağrıları, geçerli iş parçacığı için tüm çerçeveleri ve zincirleri hemen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="d3542-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="d3542-109">Hata ayıklayıcı `SetIP`çağrısından sonra çerçeve bilgilerine ihtiyaç duyuyorsa, yeni bir yığın izlemesi gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="d3542-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="d3542-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="d3542-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="d3542-111">Ancak, çerçeve geçerli bir durumda olsa da, çalışma zamanı ele aldığına bağlı olarak, başlatılmamış yerel değişkenler gibi sorunlar da olabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="d3542-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="d3542-112">Çağıran, çalışan programın ayırt edilemeyen bir şekilde sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d3542-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="d3542-113">64 bit platformlarda, yönerge işaretçisi bir `catch` veya `finally` bloğunun dışına taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="d3542-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="d3542-114">`SetIP`, 64 bitlik bir platformda böyle bir geçiş yapmak için çağrılırsa, hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3542-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3542-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3542-115">Requirements</span></span>  
 <span data-ttu-id="d3542-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3542-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3542-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d3542-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3542-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d3542-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3542-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3542-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3542-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3542-120">See also</span></span>
