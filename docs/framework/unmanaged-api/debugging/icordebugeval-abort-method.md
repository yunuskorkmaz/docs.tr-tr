---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: Abort yöntemi'
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
ms.openlocfilehash: d61cb0d696a8a134d992bc8dbbfdb61103ef469f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694324"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="17e86-103">ICorDebugEval::Abort Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17e86-103">ICorDebugEval::Abort Method</span></span>

<span data-ttu-id="17e86-104">Bu ıcorınkıımagegeval nesnesinin Şu anda gerçekleştirdiği hesaplamayı iptal eder.</span><span class="sxs-lookup"><span data-stu-id="17e86-104">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e86-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="17e86-105">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="17e86-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17e86-106">Remarks</span></span>  

 <span data-ttu-id="17e86-107">Değerlendirme iç içe geçmişse ve en son bir değilse, `Abort` Yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="17e86-107">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e86-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17e86-108">Requirements</span></span>  

 <span data-ttu-id="17e86-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e86-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e86-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="17e86-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17e86-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="17e86-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17e86-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e86-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
