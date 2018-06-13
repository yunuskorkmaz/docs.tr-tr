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
ms.openlocfilehash: 682d6684b6c86485530b9e5283d843f3b2eb7e46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413810"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="9a5f7-102">ICorDebugEval::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a5f7-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="9a5f7-103">Bu Icordebugeval nesne gerçekleştirmekte hesaplama durdurur.</span><span class="sxs-lookup"><span data-stu-id="9a5f7-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a5f7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a5f7-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a5f7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a5f7-105">Remarks</span></span>  
 <span data-ttu-id="9a5f7-106">Değerlendirme iç içe geçmiş ve en son bir değilse `Abort` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a5f7-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a5f7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a5f7-107">Requirements</span></span>  
 <span data-ttu-id="9a5f7-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a5f7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a5f7-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a5f7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a5f7-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a5f7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a5f7-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a5f7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
