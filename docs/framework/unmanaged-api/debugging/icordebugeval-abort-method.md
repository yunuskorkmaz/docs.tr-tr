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
ms.openlocfilehash: 78402e5e099815fe309618e692285de91b8b29f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124233"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="e7f58-102">ICorDebugEval::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7f58-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="e7f58-103">Bu ıcorınkıımagegeval nesnesinin Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="e7f58-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7f58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7f58-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e7f58-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7f58-105">Remarks</span></span>  
 <span data-ttu-id="e7f58-106">Değerlendirme iç içe ise ve en son bir değer değilse `Abort` yöntemi başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7f58-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7f58-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7f58-107">Requirements</span></span>  
 <span data-ttu-id="e7f58-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7f58-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7f58-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e7f58-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7f58-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e7f58-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7f58-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7f58-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
