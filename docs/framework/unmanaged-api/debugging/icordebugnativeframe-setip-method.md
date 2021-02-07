---
description: ': ICorDebugNativeFrame:: SetIP metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cb55b35eb4bd107a7273fd80ba83baac96610fb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729178"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="b8705-103">ICorDebugNativeFrame::SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8705-103">ICorDebugNativeFrame::SetIP Method</span></span>

<span data-ttu-id="b8705-104">Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b8705-104">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8705-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8705-105">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8705-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8705-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="b8705-107">'ndaki Yerel koddaki konum konumu.</span><span class="sxs-lookup"><span data-stu-id="b8705-107">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8705-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8705-108">Remarks</span></span>  

 <span data-ttu-id="b8705-109">`SetIP`Geçerli iş parçacığının tüm çerçevelerini ve zincirlerini hemen geçersiz kılmak için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="b8705-109">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="b8705-110">Hata ayıklayıcı, öğesine yapılan çağrıdan sonra çerçeve bilgisine ihtiyaç duyuyorsa `SetIP` , yeni bir yığın izlemesi gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8705-110">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="b8705-111">[ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak.</span><span class="sxs-lookup"><span data-stu-id="b8705-111">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="b8705-112">Ancak, çerçeve geçerli bir durumda olsa da, çalışma zamanı ele aldığına bağlı olarak, başlatılmamış yerel değişkenler gibi sorunlar da olabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="b8705-112">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="b8705-113">Çağıran, çalışan programın ayırt edilemeyen bir şekilde sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b8705-113">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="b8705-114">64 bit platformlarda, yönerge işaretçisi bir `catch` veya bloğunun dışına taşınamaz `finally` .</span><span class="sxs-lookup"><span data-stu-id="b8705-114">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="b8705-115">`SetIP`Bu tür bir taşımayı 64 bitlik bir platformda yapmak için çağrılırsa, hata belirten BIR hresult döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8705-115">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8705-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8705-116">Requirements</span></span>  

 <span data-ttu-id="b8705-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8705-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8705-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8705-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8705-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8705-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8705-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8705-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8705-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8705-121">See also</span></span>
