---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a691f61fcd25b7aaaae90e6adcc3c2ee0c421cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424264"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="ad0c7-102">ICorPublishEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad0c7-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="ad0c7-103">İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.</span><span class="sxs-lookup"><span data-stu-id="ad0c7-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad0c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad0c7-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad0c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad0c7-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ad0c7-106">[in] İmleç ilerlemek, öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="ad0c7-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad0c7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad0c7-107">Requirements</span></span>  
 <span data-ttu-id="ad0c7-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad0c7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad0c7-109">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ad0c7-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ad0c7-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad0c7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad0c7-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad0c7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0c7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0c7-112">See Also</span></span>  
 [<span data-ttu-id="ad0c7-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad0c7-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
