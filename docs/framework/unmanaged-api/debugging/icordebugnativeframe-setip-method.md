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
ms.openlocfilehash: bc33768e4155a0e272d3374d4c586c79ef2ff3fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792774"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="e4592-102">ICorDebugNativeFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4592-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="e4592-103">Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e4592-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4592-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4592-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4592-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4592-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="e4592-106">'ndaki Yerel koddaki konum konumu.</span><span class="sxs-lookup"><span data-stu-id="e4592-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4592-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4592-107">Remarks</span></span>  
 <span data-ttu-id="e4592-108">`SetIP` çağrıları, geçerli iş parçacığı için tüm çerçeveleri ve zincirleri hemen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e4592-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="e4592-109">Hata ayıklayıcı `SetIP`çağrısından sonra çerçeve bilgilerine ihtiyaç duyuyorsa, yeni bir yığın izlemesi gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="e4592-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="e4592-110">[ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="e4592-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="e4592-111">Ancak, çerçeve geçerli bir durumda olsa da, çalışma zamanı ele aldığına bağlı olarak, başlatılmamış yerel değişkenler gibi sorunlar da olabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="e4592-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="e4592-112">Çağıran, çalışan programın ayırt edilemeyen bir şekilde sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e4592-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="e4592-113">64 bit platformlarda, yönerge işaretçisi bir `catch` veya `finally` bloğunun dışına taşınamaz.</span><span class="sxs-lookup"><span data-stu-id="e4592-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="e4592-114">`SetIP`, 64 bitlik bir platformda böyle bir geçiş yapmak için çağrılırsa, hata belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4592-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4592-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4592-115">Requirements</span></span>  
 <span data-ttu-id="e4592-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4592-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4592-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e4592-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4592-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e4592-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4592-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4592-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4592-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4592-120">See also</span></span>
