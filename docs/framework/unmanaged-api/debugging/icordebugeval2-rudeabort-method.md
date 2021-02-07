---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugEval2:: RudeAbort Yöntemi'
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
ms.openlocfilehash: 2835fd635da007b5ee3f0e642b77f3954945f168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693518"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="bac1a-103">ICorDebugEval2::RudeAbort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bac1a-103">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="bac1a-104">`ICorDebugEval2`Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="bac1a-104">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac1a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bac1a-105">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bac1a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bac1a-106">Remarks</span></span>  

 <span data-ttu-id="bac1a-107">`RudeAbort` , değerlendirici 'in tuttuğu herhangi bir kilidi serbest bırakmadığından, hata ayıklama oturumunu güvenli olmayan bir durumda bırakır.</span><span class="sxs-lookup"><span data-stu-id="bac1a-107">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="bac1a-108">Bu yöntemi çok dikkatli bir şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="bac1a-108">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac1a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bac1a-109">Requirements</span></span>  

 <span data-ttu-id="bac1a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac1a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac1a-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bac1a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bac1a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bac1a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bac1a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac1a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
