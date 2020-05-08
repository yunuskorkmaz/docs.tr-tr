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
ms.openlocfilehash: 64d9db09b3e604247ab6a26cdca9eca22adbaace
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976310"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="8c909-102">ICorDebugEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c909-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="8c909-103">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="8c909-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c909-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c909-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c909-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c909-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8c909-106">'ndaki İmlecin ileri taşımasını sağlayan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="8c909-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c909-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c909-107">Requirements</span></span>  
 <span data-ttu-id="8c909-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c909-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c909-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8c909-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c909-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8c909-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c909-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c909-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c909-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c909-112">See also</span></span>

- [<span data-ttu-id="8c909-113">ICorDebugEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c909-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
