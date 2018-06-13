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
ms.openlocfilehash: ed8b6bf60790c10b9869dcc41678be050b8979dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420231"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="c48bb-102">ICorDebugNativeFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c48bb-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="c48bb-103">Yönerge işaretçisi yerel kodda belirtilen uzaklık konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c48bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c48bb-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c48bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c48bb-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="c48bb-106">[in] Yerel kodda uzaklık konumu.</span><span class="sxs-lookup"><span data-stu-id="c48bb-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c48bb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c48bb-107">Remarks</span></span>  
 <span data-ttu-id="c48bb-108">Çağrılar `SetIP` hemen tüm çerçeveler ve zincirleri geçerli iş parçacığı için geçersiz.</span><span class="sxs-lookup"><span data-stu-id="c48bb-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="c48bb-109">Hata ayıklayıcı çerçeve bilgileri yapılan bir çağrı sonra gerekirse `SetIP`, yeni bir yığın izlemesi gerçekleştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c48bb-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="c48bb-110">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesi geçerli bir durumda tutmak deneyecek.</span><span class="sxs-lookup"><span data-stu-id="c48bb-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="c48bb-111">Ancak, çalışma zamanı ilgili olduğu kadar çerçeve geçerli bir durumda olsa bile, yine olabilir başlatılmayan yerel değişkenlerde vb. gibi sorunlar.</span><span class="sxs-lookup"><span data-stu-id="c48bb-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="c48bb-112">Çağıran, çalışan program önbelleklerinin sağlamak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="c48bb-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="c48bb-113">64 bit platformlarda dışı yönerge işaretçisi taşınamaz bir `catch` veya `finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="c48bb-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="c48bb-114">Varsa `SetIP` çağrılır böyle bir 64-bit platformu üzerinde hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="c48bb-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c48bb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c48bb-115">Requirements</span></span>  
 <span data-ttu-id="c48bb-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c48bb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c48bb-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c48bb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c48bb-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c48bb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c48bb-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c48bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48bb-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c48bb-120">See Also</span></span>  
 
