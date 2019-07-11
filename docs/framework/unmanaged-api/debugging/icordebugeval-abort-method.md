---
title: ICorDebugEval::Abort Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 052c467f5570119cd08b4719c768d178dd52aba2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752212"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="6c24c-102">ICorDebugEval::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c24c-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="6c24c-103">Bu Icordebugeval nesne gerçekleştirmekte hesaplama durdurur.</span><span class="sxs-lookup"><span data-stu-id="6c24c-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c24c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c24c-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6c24c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c24c-105">Remarks</span></span>  
 <span data-ttu-id="6c24c-106">Değerlendirme iç içe geçmiş ve en son biri değilse `Abort` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c24c-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c24c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c24c-107">Requirements</span></span>  
 <span data-ttu-id="6c24c-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c24c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c24c-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c24c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c24c-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c24c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c24c-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c24c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
