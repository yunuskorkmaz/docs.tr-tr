---
description: 'Şu konuda daha fazla bilgi edinin: ıcorı, Genum:: Skip yöntemi'
title: ICorDebugEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: f72e400b3c2c911f609aca19f1b7d6a3a4e785cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694363"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="deeb4-103">ICorDebugEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="deeb4-103">ICorDebugEnum::Skip Method</span></span>

<span data-ttu-id="deeb4-104">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="deeb4-104">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deeb4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="deeb4-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deeb4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="deeb4-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="deeb4-107">'ndaki İmlecin ileri taşımasını sağlayan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="deeb4-107">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deeb4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="deeb4-108">Requirements</span></span>  

 <span data-ttu-id="deeb4-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deeb4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deeb4-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="deeb4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deeb4-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="deeb4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deeb4-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deeb4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deeb4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deeb4-113">See also</span></span>

- [<span data-ttu-id="deeb4-114">ICorDebugEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deeb4-114">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
