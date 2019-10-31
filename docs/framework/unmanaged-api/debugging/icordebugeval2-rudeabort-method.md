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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084790"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="6f4c9-102">ICorDebugEval2::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f4c9-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="6f4c9-103">Bu `ICorDebugEval2` Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="6f4c9-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f4c9-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6f4c9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f4c9-105">Remarks</span></span>  
 <span data-ttu-id="6f4c9-106">`RudeAbort`, değerlendirici 'in tuttuğu kilitleri serbest bırakmadığından, hata ayıklama oturumunu güvenli olmayan bir durumda bırakır.</span><span class="sxs-lookup"><span data-stu-id="6f4c9-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="6f4c9-107">Bu yöntemi çok dikkatli bir şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="6f4c9-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f4c9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f4c9-108">Requirements</span></span>  
 <span data-ttu-id="6f4c9-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f4c9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f4c9-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6f4c9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f4c9-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f4c9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f4c9-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f4c9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
