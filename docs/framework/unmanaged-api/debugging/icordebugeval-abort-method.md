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
ms.openlocfilehash: 98a9b285323bc3ad94b4f555e72a4b3242519801
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976297"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="d98a1-102">ICorDebugEval::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d98a1-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="d98a1-103">Bu ıcorınkıımagegeval nesnesinin Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="d98a1-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d98a1-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d98a1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d98a1-105">Remarks</span></span>  
 <span data-ttu-id="d98a1-106">Değerlendirme iç içe geçmişse ve en son bir değilse, `Abort` yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="d98a1-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98a1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d98a1-107">Requirements</span></span>  
 <span data-ttu-id="d98a1-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d98a1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98a1-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d98a1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d98a1-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d98a1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d98a1-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98a1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
