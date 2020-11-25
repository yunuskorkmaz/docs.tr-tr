---
title: ICorDebugEval2::RudeAbort Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 478772925dfb7ca7389b5267433f9b06ace3d5a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729622"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="65c0b-102">ICorDebugEval2::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65c0b-102">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="65c0b-103">`ICorDebugEval2`Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="65c0b-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c0b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="65c0b-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="65c0b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65c0b-105">Remarks</span></span>  

 <span data-ttu-id="65c0b-106">`RudeAbort` , değerlendirici 'in tuttuğu herhangi bir kilidi serbest bırakmadığından, hata ayıklama oturumunu güvenli olmayan bir durumda bırakır.</span><span class="sxs-lookup"><span data-stu-id="65c0b-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="65c0b-107">Bu yöntemi çok dikkatli bir şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="65c0b-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c0b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65c0b-108">Requirements</span></span>  

 <span data-ttu-id="65c0b-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c0b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c0b-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65c0b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65c0b-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="65c0b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65c0b-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c0b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
