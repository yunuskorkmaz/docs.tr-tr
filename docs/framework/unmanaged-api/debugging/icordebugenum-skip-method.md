---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a886d8ab8f2d59bb9c9b0b3ff00fd89f7c931ff8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692827"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="039ca-102">ICorDebugEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="039ca-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="039ca-103">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="039ca-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="039ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="039ca-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="039ca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="039ca-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="039ca-106">[in] İmleç ilerlemek, öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="039ca-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="039ca-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="039ca-107">Requirements</span></span>  
 <span data-ttu-id="039ca-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="039ca-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="039ca-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="039ca-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="039ca-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="039ca-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="039ca-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="039ca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039ca-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="039ca-112">See also</span></span>
- [<span data-ttu-id="039ca-113">ICorDebugEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="039ca-113">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
