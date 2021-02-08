---
description: ': ICorPublishEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
title: ICorPublishEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: f0124681c8051a5c05c1caf3edd06c697da486e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794610"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="80086-103">ICorPublishEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80086-103">ICorPublishEnum::Skip Method</span></span>

<span data-ttu-id="80086-104">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="80086-104">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80086-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80086-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80086-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80086-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="80086-107">'ndaki İmlecin ileri taşımasını sağlayan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="80086-107">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80086-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80086-108">Requirements</span></span>  

 <span data-ttu-id="80086-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80086-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80086-110">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="80086-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="80086-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80086-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80086-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80086-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80086-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80086-113">See also</span></span>

- [<span data-ttu-id="80086-114">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80086-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
