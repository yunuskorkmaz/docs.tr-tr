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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2d0628d3c8bf5912c811ddf4b2a00b9dfca4687
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639217"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="2a158-102">ICorDebugNativeFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a158-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="2a158-103">Yönerge işaretçisi yerel kodda uzaklık belirtilen konuma ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2a158-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a158-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a158-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a158-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a158-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="2a158-106">[in] Yerel kodda uzaklık konumu.</span><span class="sxs-lookup"><span data-stu-id="2a158-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a158-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a158-107">Remarks</span></span>  
 <span data-ttu-id="2a158-108">Çağrılar `SetIP` hemen tüm çerçeveleri ve zincirleri için geçerli iş parçacığı geçersiz.</span><span class="sxs-lookup"><span data-stu-id="2a158-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="2a158-109">Hata ayıklayıcı çağrısı yapıldıktan sonra çerçeve bilgileri gerekiyorsa `SetIP`, yeni bir yığın izlemesi gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a158-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="2a158-110">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesini geçerli bir durumda tutmak çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="2a158-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="2a158-111">Ancak, çalışma zamanı ilgili olduğu kadar çerçeveyi geçerli bir durumda olsa bile, yine de olabilir başlatılmamış yerel değişkenler vb. gibi sorunlar.</span><span class="sxs-lookup"><span data-stu-id="2a158-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="2a158-112">Çalışan programa önbelleklerinin sağlamak için çağıran sorumludur.</span><span class="sxs-lookup"><span data-stu-id="2a158-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="2a158-113">64-bit platformlarda, yönerge işaretçisini tanesi taşınamaz bir `catch` veya `finally` blok.</span><span class="sxs-lookup"><span data-stu-id="2a158-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="2a158-114">Varsa `SetIP` çağrılır böyle bir 64-bit platformlarda hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a158-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a158-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a158-115">Requirements</span></span>  
 <span data-ttu-id="2a158-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a158-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a158-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a158-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a158-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a158-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a158-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a158-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a158-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a158-120">See also</span></span>

